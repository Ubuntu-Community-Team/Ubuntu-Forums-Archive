---
title: "cannot login to iFolder server on 9.0.4 Desktop"
date: 2010-02-06
forum: General Help
---

### Post by Bakawolf on 2010-02-06
I recently installed iFolder server on my 9.0.4 desktop computer.
I cannot login as a user using a web interface or client. Using the correct password, it takes a long time, then tells me that the login may be incorrect. With an incorrect password, it tells me this immediately. 
 I am able to login to the web admin interface, but the "System" tab will generate the following error after several minutes.

> Server Version: 1.8.3.0
HostName:       xx
MachineName:    xx
OS Version:     Unix 2.6.28.15
CLR Version:    2.0.50727.42


Exception detail:

Exception type: Exception

Unable to connect to master serverSystem.Net.WebException: The request timed out
  at System.Net.HttpWebRequest.GetRequestStream () [0x00000] 
  at System.Web.Services.Protocols.SoapHttpClientProtocol.Invoke (System.String method_name, System.Object[] parameters) [0x00000] 

  at Novell.iFolderWeb.Admin.SystemInfo.ConnectToMaster () [0x00000] 
  at Novell.iFolderWeb.Admin.SystemInfo.Page_PreRender (System.Object source, System.EventArgs e) [0x00000] 
  at System.Web.UI.Control.OnPreRender (System.EventArgs e) [0x00000] 
  at System.Web.UI.Control.PreRenderRecursiveInternal () [0x00000] 
  at System.Web.UI.Page.ProcessLoadComplete () [0x00000] 
  at System.Web.UI.Page.InternalProcessRequest () [0x00000] 
  at System.Web.UI.Page.ProcessRequest (System.Web.HttpContext context) [0x00000] 

Attempting to log in as a user will generate the following error in my apache2.log

> ** (/usr/lib/mono/2.0/mod-mono-server2.exe:13785): WARNING **: _wapi_connect: error looking up socket handle 0xb


I believe this may be due to improper mono installation, but cannot find the problem. Any help would be appreciated.

---

### Post by Bakawolf on 2010-02-15
Still no progress.

---

### Post by dsmithpdx on 2010-08-19
I realize this is an old thread, but I am having the exact same problem and can't figure it out!  Did you ever solve this?

Thanks!

---

