---
title: "Mono server not working"
date: 2009-10-20
forum: General Help
---

### Post by Mattias Mirhagen on 2009-10-20
Hi!

I'm trying to learn C# with Mono and Monodevelop. I beleive I have installed the packages needed, and everything seems to work fine, except when I try to develop a web application. When I try to run the server I get the following output:

Adding applications '/:.'...
Registering application:
    Host:          any
    Port:          any
    Virtual path:  /
    Physical path: /home/mattias/Projects/091016/PresentationLayer/
Handling exception type FileNotFoundException
Message is Could not load file or assembly 'xsp2, Version=2.5.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies. The system cannot find the file specified.
IsTerminating is set to True
System.IO.FileNotFoundException: Could not load file or assembly 'xsp2, Version=2.5.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies. The system cannot find the file specified.
File name: 'xsp2, Version=2.5.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756'
  at (wrapper xdomain-invoke) System.AppDomain:CreateInstanceAndUnwrap (string,string)
  at (wrapper remoting-invoke-with-check) System.AppDomain:CreateInstanceAndUnwrap (string,string)
  at Mono.WebServer.XSP.Server.RealMain (System.String[] args, Boolean root, IApplicationHost ext_apphost, Boolean quiet) [0x00678] in /home/mattias/xsp/src/Mono.WebServer.XSP/main.cs:440 
  at (wrapper remoting-invoke-with-check) Mono.WebServer.XSP.Server:RealMain (string[],bool,Mono.WebServer.IApplicationHost,bool)
  at Mono.WebServer.XSP.Server.Main (System.String[] args) [0x00018] in /home/mattias/xsp/src/Mono.WebServer.XSP/main.cs:258 


I have no clue what to do, I have googled and tried alot. Could someone please help?

---

### Post by directhex on 2009-10-20
You aren't using packages, you're using something you compiled yourself. It's not possible to help you without a FULL rundown of EVERYTHING you manually installed, as it breaks any instructions you might be given for normal Ubuntu users.

---

### Post by Mattias Mirhagen on 2009-10-20
Okay... Would it be possible for me to uninstall and install with packages instead? Or have I done something irreversable?

---

### Post by Mattias Mirhagen on 2009-10-20
Hmm, actually I think I found and removed now some manually installed binaries. Then I installed the package "mono-xsp". Now I get this error instead:

Adding applications '/:.'...
Registering application:
    Host:          any
    Port:          any
    Virtual path:  /
    Physical path: /home/mattias/Projects/091016/PresentationLayer/
Handling exception type InvalidCastException
Message is Cannot cast from source type to destination type.
IsTerminating is set to True
System.InvalidCastException: Cannot cast from source type to destination type.

Server stack trace: 
  at (wrapper xdomain-dispatch) Mono.WebServer.XSP.Server:RealMain (object,byte[]&,byte[]&,string[],bool,bool)

Exception rethrown at [0]: 

  at (wrapper xdomain-invoke) Mono.WebServer.XSP.Server:RealMain (string[],bool,Mono.WebServer.IApplicationHost,bool)
  at (wrapper remoting-invoke-with-check) Mono.WebServer.XSP.Server:RealMain (string[],bool,Mono.WebServer.IApplicationHost,bool)
  at Mono.WebServer.XSP.Server.RealMain (System.String[] args, Boolean root, IApplicationHost ext_apphost, Boolean quiet) [0x00000] 
  at (wrapper remoting-invoke-with-check) Mono.WebServer.XSP.Server:RealMain (string[],bool,Mono.WebServer.IApplicationHost,bool)
  at Mono.WebServer.XSP.Server.Main (System.String[] args) [0x00000]

---

### Post by directhex on 2009-10-20
Which version is this?

---

### Post by Mattias Mirhagen on 2009-10-20
Actually, I think I solved it, though I'm not quite sure how. I redid my solution, and it worked. Thanks for the help that guided me in the right direction! :)

---

