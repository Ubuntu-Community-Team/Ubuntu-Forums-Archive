---
title: "MATLAB does not run under wine"
date: 2011-05-22
forum: General Help
---

### Post by harbimilan on 2011-05-22
Hi,
I have Ubuntu 10.10 and wine installed on it.
I have succeeded installing MATLAB R2007a with wine and run it before.
and I have formatted ubuntu, re-installed everything, and I installed MATLAB.

when I try to run MATLAB, it doesn't run, and the terminal output is the following:

[B]fixme:actctx: parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.ATL" (8.0.50608.0)
fixme:actctx: parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC" (8.0.50608.0)
err:module:import_dll Library MFC80.DLL (which is needed by L"Z:\\home\\furk\\Desktop\\Programlar\\MATLABdir\\bin\\win32\\uiw.dll") not found
err:module:import_dll Library uiw.dll (which is needed by L"Z:\\home\\furk\\Desktop\\Programlar\\MATLABdir\\bin\\win32\\comcli.dll") not found
err:module:import_dll Library ATL80.DLL (which is needed by L"Z:\\home\\furk\\Desktop\\Programlar\\MATLABdir\\bin\\win32\\comcli.dll") not found
err:module:import_dll Library MFC80.DLL (which is needed by L"Z:\\home\\furk\\Desktop\\Programlar\\MATLABdir\\bin\\win32\\comcli.dll") not found
err:module:import_dll Library comcli.dll (which is needed by L"Z:\\home\\furk\\Desktop\\Programlar\\MATLABdir\\bin\\win32\\mcr.dll") not found
fixme:actctx: parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.ATL" (8.0.50608.0)
fixme:actctx: parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.ATL" (8.0.50608.0)
fixme:actctx: parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC" (8.0.50608.0)
err:module:import_dll Library MFC80.DLL (which is needed by L"Z:\\home\\furk\\Desktop\\Programlar\\MATLABdir\\bin\\win32\\uiw.dll") not found
err:module:import_dll Library uiw.dll (which is needed by L"Z:\\home\\furk\\Desktop\\Programlar\\MATLABdir\\bin\\win32\\comcli.dll") not found
err:module:import_dll Library ATL80.DLL (which is needed by L"Z:\\home\\furk\\Desktop\\Programlar\\MATLABdir\\bin\\win32\\comcli.dll") not found
err:module:import_dll Library MFC80.DLL (which is needed by L"Z:\\home\\furk\\Desktop\\Programlar\\MATLABdir\\bin\\win32\\comcli.dll") not found
err:module:import_dll Library comcli.dll (which is needed by L"Z:\\home\\furk\\Desktop\\Programlar\\MATLABdir\\bin\\win32\\mwoles05.DLL") not found
err:module:import_dll Library ATL80.DLL (which is needed by L"Z:\\home\\furk\\Desktop\\Programlar\\MATLABdir\\bin\\win32\\mwoles05.DLL") not found
err:module:import_dll Library mwoles05.DLL (which is needed by L"Z:\\home\\furk\\Desktop\\Programlar\\MATLABdir\\bin\\win32\\mcr.dll") not found
fixme:actctx: parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC" (8.0.50608.0)
err:module:import_dll Library MFC80.DLL (which is needed by L"Z:\\home\\furk\\Desktop\\Programlar\\MATLABdir\\bin\\win32\\mlautoregister.dll") not found
err:module:import_dll Library mlautoregister.dll (which is needed by L"Z:\\home\\furk\\Desktop\\Programlar\\MATLABdir\\bin\\win32\\mcr.dll") not found
fixme:actctx: parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC" (8.0.50608.0)
fixme:actctx: parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC" (8.0.50608.0)
err:module:import_dll Library MFC80.DLL (which is needed by L"Z:\\home\\furk\\Desktop\\Programlar\\MATLABdir\\bin\\win32\\uiw.dll") not found
err:module:import_dll Library uiw.dll (which is needed by L"Z:\\home\\furk\\Desktop\\Programlar\\MATLABdir\\bin\\win32\\hg.dll") not found
err:module:import_dll Library MFC80.DLL (which is needed by L"Z:\\home\\furk\\Desktop\\Programlar\\MATLABdir\\bin\\win32\\hg.dll") not found
err:module:import_dll Library hg.dll (which is needed by L"Z:\\home\\furk\\Desktop\\Programlar\\MATLABdir\\bin\\win32\\mcr.dll") not found
fixme:actctx: parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC" (8.0.50608.0)
err:module:import_dll Library MFC80.DLL (which is needed by L"Z:\\home\\furk\\Desktop\\Programlar\\MATLABdir\\bin\\win32\\uiw.dll") not found
err:module:import_dll Library uiw.dll (which is needed by L"Z:\\home\\furk\\Desktop\\Programlar\\MATLABdir\\bin\\win32\\mcr.dll") not found
err:module:import_dll Library mcr.dll (which is needed by L"Z:\\home\\furk\\Desktop\\Programlar\\MATLABdir\\bin\\win32\\MATLAB.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\furk\\Desktop\\Programlar\\MATLABdir\\bin\\win32\\MATLAB.exe" failed, status c0000135[/B]

how can I fix this?

thanks in advance..

---

