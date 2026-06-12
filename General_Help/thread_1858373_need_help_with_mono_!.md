---
title: "need help with mono !"
date: 2011-10-12
forum: General Help
---

### Post by papampi on 2011-10-12
I tried to run file with mono or wine!
I want to run [[COLOR="RoyalBlue"]_*BRMovieTool.exe*_[/COLOR]]("http://code.google.com/p/br-movie-tool/") which will grab movie trailers from youtube and save them in the same directory !

when i run it with wine it asks for .netframwork v4.0
and with mono BRMovieTool.exe give me this error :
```
payam@PAYAM-UBUNTU:~/win/BRMovieTool.1.0.2$ mono ./BRMovieTool.exe
WARNING: The runtime version supported by this application is unavailable.
Using default runtime: v1.1.4322
** (./BRMovieTool.exe:6990): WARNING **: Missing method System.Windows.Forms.Application::SetCompatibleTextRenderingDefault(bool) in assembly /usr/lib/mono/gac/System.Windows.Forms/1.0.5000.0__b77a5c561934e089/System.Windows.Forms.dll, referenced in assembly /home/payam/win/BRMovieTool.1.0.2/BRMovieTool.exe
Unhandled Exception: System.MissingMethodException: Method not found: 'System.Windows.Forms.Application.SetCompatibleTextRenderingDefault'.

```
any idea how to run this ?

---

### Post by mikejonesey on 2011-10-12
I think dotnet only goes up to 3.5 in wine atm... there is a wine utitlity for installing "addons" which includes the netframeworks and fonts, but i cant remember what it is called... winetool or somthing...

---

### Post by papampi on 2011-10-12
> **mikejonesey said:**
> I think dotnet only goes up to 3.5 in wine atm... there is a wine utitlity for installing "addons" which includes the netframeworks and fonts, but i cant remember what it is called... winetool or somthing...

thanks for your reply !
the problem solved by upgrading from version 2.6.7 to 2.10.2 !!!
version 2.10.2 supports .net v4.0 !

---

