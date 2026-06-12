---
title: "Can someone help me getrid of it?"
date: 2009-08-13
forum: General Help
---

### Post by Anne Wee on 2009-08-13
I don't know whether I am the right place here, just coming here because of the recommendation of my friend. I want to uninstall a program called Personal Antivirus program from my computer without success for several time. So I sincerely hope that can someone here uninstall it from my computer.

I am running XP.

Thanks for your time.:)

---

### Post by ben-ess08 on 2009-08-13
Try going [here]("http://forums.techguy.org/") for help, Ubuntu is a different operating system from Windows XP.

---

### Post by King_Ragger on 2009-08-13
This is the Ubuntu Linux forum. Your question would be better asked at one of the several million Windows forums on the net.

But to answer your question. If the uninstaller doesn't work for me I just boot Windows up in safe mode and erase the requisite folder from the Program Files directory. Then I just erase the shortcuts and stop it from trying to start using msconfig. It works 99% of the time for me. Although I only really use Windows to play games that won't work in Wine.

---

### Post by SPr on 2009-08-13
Instructions to remove this infection: [http://www.bleepingcomputer.com/virus-removal/remove-personal-antivirus](http://www.bleepingcomputer.com/virus-removal/remove-personal-antivirus)

---

### Post by KlinerDraken on 2009-08-13
try downloading and running [SuperAntiSpyware]("http://www.superantispyware.com/download.html") and [Avast]("http://www.avast.com/eng/download-avast-home.html"). 

Better yet stop using Windows and start using a Linux OS like Ubuntu. ;)

---

### Post by khelben1979 on 2009-08-13
[WindowsBBS.com]("http://www.windowsbbs.com/windows-xp/") seems like a pretty good place for your type of questions.

---

### Post by Pbethe on 2009-08-13
> **Anne Wee said:**
> I don't know whether I am the right place here, just coming here because of the recommendation of my friend. I want to uninstall a program called Personal Antivirus program from my computer without success for several time. So I sincerely hope that can someone here uninstall it from my computer.

I am running XP.

Thanks for your time.:)

Maybe this is what your friend had in mind: 

 [http://mghicks.wordpress.com/2007/03/24/virus-scanning-windows-from-knoppix/](http://mghicks.wordpress.com/2007/03/24/virus-scanning-windows-from-knoppix/)

This page is written for Knoppix linux, but I have adapted these instructions for use with the Ubuntu live CD.  So, the first thing you would want to do is get some live CD, so that you can boot your computer in linux.  If that is more than you want to do, the other replies to this should help you out.

Paul Bethe

---

### Post by tgeer43 on 2009-08-13
> **King_Ragger said:**
> This is the Ubuntu Linux forum. Your question would be better asked at one of the several million Windows forums on the net.

But to answer your question. If the uninstaller doesn't work for me I just boot Windows up in safe mode and erase the requisite folder from the Program Files directory. Then I just erase the shortcuts and stop it from trying to start using msconfig. It works 99% of the time for me. Although I only really use Windows to play games that won't work in Wine.
That will get rid of the bulk of it in most cases but there will be the inevitable horde of registry entries and configuration/data files in the Users/*username*/AppData/Local and .../LocalLow and .../Roaming folders. There could also be remnants in similar folders under the /Users/Default, Default User, and All Users folders. Then there's the ProgramData folder - don't forget that one. Some programs even create a folder for themselves right in the root directory. Many Windows apps also have the nasty habit of strewing .dll and other miscellaneous support files in /Windows/System32.

So to steer things back towards a Linux/Ubuntu topic, now you know one of many reasons I don't run Windows anymore. At least apps for Linux and Ubuntu in particular usually confine themselves to their installation directory and possibly one data/configuration directory in $HOME. If you can't uninstall normally for some reason then you can at least be assured of  an easy manual removal of just about all of it except for possibly a broken link here and there.

A far better reason for ditching Windows altogether is the fact that the OP's issue actually concerns a nasty piece of malware masquerading as security software that has latched its hooks into his system, disabled vital security functions of the OS as well as third-party security software and blocked access to online security related sites (like online virus scanners and anti-virus definition update sites.

tgeer

---

