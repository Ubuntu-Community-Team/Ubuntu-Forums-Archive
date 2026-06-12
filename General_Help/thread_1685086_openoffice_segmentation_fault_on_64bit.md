---
title: "openoffice segmentation fault on 64bit"
date: 2011-02-10
forum: General Help
---

### Post by muatik on 2011-02-10
Hi, 

I try to run soffice headles and connect via php. Code works in my local computer(64bit ubuntu) but doesn't work in redhat(64bit). 

[PHP]<?php
$cloader=get_remote_xcomponent(
      "uno:socket,host=localhost,port=8100;urp;StarOffice.ServiceManager",
      "com.sun.star.frame.Desktop"
      );
      
      $properties=array();
      $cmp=$cloader->loadComponentFromURL(
         'file:///root/tmp.doc',
         "_blank",0,
         $properties
      );
?>
[/PHP]


with php, I got this error message from gdb: 

> Program received signal SIGSEGV, Segmentation fault. 
0x0000003ab0679a30 in strlen () from /lib64/libc.so.6 

I also tried with python and again it doesn't work in readhat. 

```
import uno
local = uno.getComponentContext()
resolver = local.ServiceManager.createInstanceWithContext("com.sun.star.bridge.UnoUrlResolver", local)
context = resolver.resolve("uno:socket,host=localhost,port=8100;urp;StarOffice.ComponentContext")
desktop = context.ServiceManager.createInstanceWithContext("com.sun.star.frame.Desktop", context)
document = desktop.loadComponentFromURL("file:///root/tmp.doc" ,"_blank", 0, ())
t=document.getText()
t2=t.getString()
print t2
```

> __main__.com.sun.star.lang.IllegalArgumentException: URL seems to be an unsupported one.

I started soffice like this:
> soffice -accept="socket,host=localhost,port=8100;urp;StarOffice.ServiceManager" -norestore -nofirstwizard -nologo -headless &

> #netstat -anp|grep 8100
tcp 0 0 127.0.0.1:8100 0.0.0.0:* LISTEN 16219/soffice.bin

---

