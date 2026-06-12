---
title: "I need 1 windows program to work in TS"
date: 2009-12-21
forum: General Help
---

### Post by carsonrose on 2009-12-21
I use "ACT! by Sage" for my CRM. I am looking all over for an open source replacement that will replace it, import the data from it into the new system. 

My question is this, I have a server 2008 in the server room in the back. It is running TS gateway. Currently I have about half a half in my office, Linux/Windows XP machines. On both the windows machines and the Ubuntu machines, I just open tsclient and connect that way. The server is terribly slow and bogs down quite a bit. But I have to use it this way to use ACT because Wine didnt install it/it doesnt work the way it is. 

Any ideas guys? Any help would be greatly appreciated!

-Doug Bradshaw

---

### Post by reiki on 2009-12-21
How often do you use ACT? I have a couple of programs that won't run in wine so I use VirtualBox to put them in a virtual machine.

---

### Post by carsonrose on 2009-12-21
> **reiki said:**
> How often do you use ACT? I have a couple of programs that won't run in wine so I use VirtualBox to put them in a virtual machine.
I have 18 employees, all of us use ACT daily... Its our only way at the moment to access client information...

---

### Post by proxess on 2009-12-21
Have you tried running it on Wine? Maybe you could also invest a little to try it out on Crossover. I'd give it a go but I don't have any way to obtain that application.

---

### Post by carsonrose on 2009-12-21
> **proxess said:**
> Have you tried running it on Wine?
yes, it will install, but not run correctly. I suspect this is because ACT uses MSSQL. Im not completly sure. I'd really like to get rid of windows altogether, but I dont know enough about Ubuntu to make that happen just yet. I am thinking about the only way Im going to be able to make this happen is to use TS Web Access on the server 2008 machine and access that one piece of software through a browser window... Too bad there isnt a way to just open one single window on a Windows server... :(

---

### Post by proxess on 2009-12-21
> **carsonrose said:**
> yes, it will install, but not run correctly. I suspect this is because ACT uses MSSQL. Im not completly sure. I'd really like to get rid of windows altogether, but I dont know enough about Ubuntu to make that happen just yet. I am thinking about the only way Im going to be able to make this happen is to use TS Web Access on the server 2008 machine and access that one piece of software through a browser window... Too bad there isnt a way to just open one single window on a Windows server... :(

Does it output some kind of error in the console when you try installing it through Wine? How about copying the Windows install folder into Wine?

---

### Post by carsonrose on 2009-12-21
> **proxess said:**
> Does it output some kind of error in the console when you try installing it through Wine? How about copying the Windows install folder into Wine?
Perhaps Im a little lost. Are you asking about copying the entire windows folder from my user ID in Server 2008 into the wine folder?

---

### Post by Thelasko on 2009-12-21
> **carsonrose said:**
> I am looking all over for an open source replacement that will replace it, import the data from it into the new system.

I don't know of an open source replacement.  But Salesforce.com is web based, and therefore should work well across all of your systems.

P.S. SugarCRM is an open source alternative you may want to consider too.

---

### Post by proxess on 2009-12-21
> **carsonrose said:**
> Perhaps Im a little lost. Are you asking about copying the entire windows folder from my user ID in Server 2008 into the wine folder?

The folder I mean is the (probably) C:\Program Files\ACT\ or C:\Program Files\sage\ACT\ and then searching for the missing DLLs in the system32 folder if the program doesn't launch through wine (check the console's output, wine ~/.wine/drive_c/Program\ Files/ACT/act.exe).


You may also want to check out this tutorial, which helps you pick an OSS CRM for your needs.

---

### Post by carsonrose on 2009-12-22
thanks guys!

---

### Post by akakingess on 2009-12-22
> **carsonrose said:**
> thanks guys!

If you decide/get one of the options to work, would you mind letting us know, because I am in a similar position and would like to hear how you resolve it or if you just decide to keep it going as is.  Thank you.

---

### Post by carsonrose on 2010-07-14
> **reiki said:**
> How often do you use ACT? I have a couple of programs that won't run in wine so I use VirtualBox to put them in a virtual machine.


This worked! In seamless mode it really is like having a windows/linux hybrid.... freaky...

---

