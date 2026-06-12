---
title: "Netcat"
date: 2011-10-08
forum: General Help
---

### Post by LemonAid on 2011-10-08
Hello !

    First of all i would like to tell you that i`m not sure where this thread belongs to, so if it isn't in the right place, i apologize. 

    Right then, before i ask the question this is my setup: laptop running Ubuntu 11.04 + PC running Windows 7 SP1, on the same network, connected trough a router. On the PC (win) i set up a listening server that will put every connecting user into a CMD shell: 
```
nc -l -d -e cmd.exe -p 1500 -L
```    I can connect from my laptop and everything works fine, but i do not know how to start another Netcat from within the CMD shell i land into. _The reason i want this is in order to transfer files from one machine to the other, using Netcat._
    The error i get (from the CMD shell i`m in) is: ```
'nc' is not recognized as an internal or external command,operable program or batch file.
```Now, the way i set up Netcat on the PC (comp i`m connecting to), is by adding a registry value to the Windows registry that autostarts nc.exe in the background on reboot/relog (the first code).. i don`t believe this is relevant, but i thought i'd throw it out there.
    The shell lands me in: "C:\Windows\System32>", and since that is where i copied the nc.exe, i tried looking for it, but when i list the items in the folder i can not see nc.exe. :confused:
Note: nc.exe is in the Winodows PATH, since it`s in "system32". I also added it to the Windows PATH explicitly !

Oh.. the question was: "How can i start Netcat from the CMD shell after i connect?

_Update_: If i copy the nc.exe in another directory, browse to it, and start a listening server from there, it does indeed work, i however want to start the same nc.exe that`s in "System32" from my CMD shell.

**[SOLVED]**: The problem was that on a x64Win7 the folder System32 is reserved for 64bit applications. The full story -> [http://msdn.microsoft.com/en-us/library/aa384187](http://msdn.microsoft.com/en-us/library/aa384187) 
Now there are a number of ways to go about this, but the simplest way is to go into the nc.exe (netcat) Proprieties->Compatibility tab, and check "Run this program as an administrator".

---

