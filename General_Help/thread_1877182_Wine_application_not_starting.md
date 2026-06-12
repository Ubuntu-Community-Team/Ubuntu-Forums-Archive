---
title: "Wine application not starting"
date: 2011-11-07
forum: General Help
---

### Post by dlemos on 2011-11-07
Hello all

I was wondering If anyone has the same problem as I do: when I try to run a specific windows app with wine, a windows "window" appears and then quicly disappears, and the app does not start.

I've tried changing the options, installing the latest version of wine (1.3), installing wine tricks, and googling the answer but had no sucess.

can anyone help?

Thank you

---

### Post by grahammechanical on 2011-11-07
Hi

1) Have you checked the wine database to see if your specific program runs under wine without too many problems?

2) Did you install the Windows program using the Uninstall Wine Programs utility?

3) How are you trying to load the program? From an icon?

4) You should try to load the program from the command line in a terminal with **wine "C:\program files\appname\appname.exe**.

This will give you error messages from which you may work out what is wrong with the program. It may be unable to find some of its files. I had had this with a specific Windows program that I wanted to run under wine. I needed to move some files from one folder to another and then it would load.

I am guessing the window that you almost see is the program's splash screen and when the program fails to load this screen just blinks out of existence.

What version of Ubuntu are you using?

Regards.

---

### Post by dlemos on 2011-11-07
hello grahammechanical thank for your help

1)well, this is a very specific app and it is not in the database.

2) yes i did

3)at first from an icon, later I did what you sugested and ran from terminal. I get the error:

*wine: Install Mono for Windows to run .NET 2.0 applications.*

I've opened ubuntu software center but mono seems to be installed already :S what should i do?

---

### Post by dlemos on 2011-11-07
I've also installed net framework 2.0 using wine but now i get the error: 
"Object reference not set to an instance of an object"

:(

---

### Post by Mark Phelps on 2011-11-07
Unfortunately,  .NET doesn't work very well in Wine.

What is the specific app, and version, that you're trying to use?

---

### Post by dlemos on 2011-11-07
Well, it is a very specific tool: [http://www.oreyitrade.com/showpage.php?id=51&cid=0](http://www.oreyitrade.com/showpage.php?id=51&cid=0)

the tool comes with a service and that's the reason I'm trying to run this specific tool

Now i tried to reinstall mono and also a library that seemed to be missing: " mscorlib.dll" . I tried to solve this by installing nant, according to this link:
[http://opensimulator.org/wiki/Troubleshooting#The_assembly_mscorlib.dll_was_not_found_or_could_not_be_loaded](http://opensimulator.org/wiki/Troubleshooting#The_assembly_mscorlib.dll_was_not_found_or_could_not_be_loaded)

PS: I'm using ubuntu 11.10

---

### Post by Mark Phelps on 2011-11-08
One of the prime reasons many Windows apps don't work in Wine is that they use specialized DLL files.  CodeWeavers rewrote SOME of the DLL files so that instead of Windows OS calls, they make Linux kernel calls -- which is why Wine works at all.

Problem is, they couldn't possibly find and rewrite EVERY single DLL file -- there are thousands of them.

But in Windows, DLL files get installed for lots of reasons, and if an app uses one that say gets installed by .NET v4, since you don't have that installed, that DLL won't be there -- and the app won't work.

Since .NET doesn't work well in Wine, anything that relies on it will probably not work well, either.

This is most likely to be yet another Windows app that simply won't work in Wine.

---

### Post by dlemos on 2011-11-08
But what about mono? isn't it supost to solve this problem, by allowing to run .NET apps?

---

