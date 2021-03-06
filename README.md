# 4d-plugin-uti-tools
Utility functions to handle UTI on OS X.

##Platform

| carbon | cocoa | win32 | win64 |
|:------:|:-----:|:---------:|:---------:|
|🆗|🆗|🚫|🚫|

Commands
---

```c
// --- Path
PATH_GET_COMPONENTS
PATH_Get_name
PATH_Get_directory_path
PATH_Get_uti
PATH_OPEN_WITH_APPLICATION
PATH_Get_thumbnail

// --- Conversion
UTI_To_ostype
UTI_To_mime
UTI_To_extension
UTI_From_ostype
UTI_From_mime
UTI_From_extension

// --- Comparision
UTI_Equal
UTI_Conforms_to

// --- Information
UTI_Get_declaration
UTI_Get_localized_description
UTI_Get_icon
UTI_Get_application
UTI_Get_description
```

Changes
---

**2015-08-19**
```
  //return "sff" (iWork 09) UTI
$k:=UTI From extension ("key")
$p:=UTI From extension ("pages")
$n:=UTI From extension ("numbers")
```
**2015-08-18**

```
  //fix crash with empty string
$uti:=PATH Get uti ("")
$uti:=PATH Get directory path ("")
```

**Process path components**
 
```
$path:=Get 4D folder(Current resources folder)+"email.key"
ARRAY TEXT($components;0)
PATH GET COMPONENTS ($path;$components)
$name:=PATH Get name ($path;$nameWithoutExtension;$extension)
$directoryPath:=PATH Get directory path ($path)
```

**Inspect UTI**

```
$path:=Get 4D folder(Current resources folder)+"email.key"
$uti:=PATH Get uti ($path)
$declaration:=UTI Get declaration ($uti)
$description:=UTI Get description ($uti)
$description_l:=UTI Get localized description ($uti)//same thing
```

**Images**

```
$path:=Get 4D folder(Current resources folder)+"email.key"
$uti:=PATH Get uti ($path)
$icon:=UTI Get icon ($uti)
$thumbnail:=PATH Get thumbnail ($path;64;64)
```

**Open with application**

```
$path:=Get 4D folder(Current resources folder)+"email.key"
$uti:=PATH Get uti ($path)
$application:=UTI Get application ($uti)//full path
PATH OPEN WITH APPLICATION ($path;$application)
```

**Conversion**

```
$uti:=UTI From extension ("key")
$extension:=UTI To extension ($uti)
$uti:=UTI From mime ("image/png")
$mime:=UTI To mime ($uti)
$uti:=UTI From ostype ("TEXT")
$ostype:=UTI To ostype ($uti)
```

**Comparision**

```
$result:=UTI Conforms to ("public.png";"public.image")
$result:=UTI Equal ("public.png";"public.image")
```
