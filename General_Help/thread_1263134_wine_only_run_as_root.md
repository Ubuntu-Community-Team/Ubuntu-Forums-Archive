---
title: "wine only run as root"
date: 2009-09-10
forum: General Help
---

### Post by vivasjimmy on 2009-09-10
Hi, I am running wine as normal user. When I do
wine /home/wine/drive_c/Program\ Files/Microsoft\ Office/Office12/EXCEL.EXE

**I get this:**
jimmy@SS02-NBK-004:~> wine /home/wine/drive_c/Program\ Files/Microsoft\ Office/Office12/EXCEL.EXE
fixme:actctx[IMG]http://e1h7.simplecdn.net/lqcdn/images/questions/images/smilies/tongue.gif[/IMG]****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\wine\\drive_c\\Program Files\\Microsoft Office\\Office12\\EXCEL.EXE") not found
fixme:actctx[IMG]http://e1h7.simplecdn.net/lqcdn/images/questions/images/smilies/tongue.gif[/IMG]****_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\wine\\drive_c\\Program Files\\Microsoft Office\\Office12\\oart.dll") not found
err:module:import_dll Library oart.dll (which is needed by L"Z:\\home\\wine\\drive_c\\Program Files\\Microsoft Office\\Office12\\EXCEL.EXE") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\wine\\drive_c\\Program Files\\Microsoft Office\\Office12\\EXCEL.EXE" failed, status c0000135

The only way to run wine programs is logging in as root from terminal or from X session...

I follow [URL="http://ubuntuforums.org/showthread.php?t=527169&page=2"]this link to try to fix it but I am still not able too.
[/URL] 
I need to be able to run office 2007 and other programs as normal user and not root.

Thanks to whoever can help.

---

