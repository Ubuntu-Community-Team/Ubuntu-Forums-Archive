---
title: "Boot error with wubi install (9.10 Karmic)"
date: 2010-02-24
forum: General Help
---

### Post by glasya on 2010-02-24
i am experiencing some difficulty booting ubuntu 9.10 (karmic) threw Wubi. I installed ubuntu threw wubi not to long ago and had no problems at all. I was able to boot ubuntu and set everything up just fine. I decided to uninstall that distro and reinstall it from my pen drive instead. after i uninstalled ubuntu threw wubi's uninstall I rebooted my computer and it brought up the Select OS screen as if ubuntu was still there, so i chose to boot ubuntu and see if the uninstall failed or something and it gave me a corrupt or missing file message instead of booting(The following file is either corrupt or missing: <Windows root>\system32\hal.dll please reinstall this file or find a valid copy)or something like that but the file name is accurate. just to be sure i didn't screw anything up i rebooting after reading the message and logged into windows (xp) and looked around but couldn't find any trace of an error and the ubuntu files and wubi were both gone. I have since tried a few things such as reinstalling wubi and using it to install ubuntu, i did succeed in installing it however when i choose ubuntu on the boot screen it gives me this same error/corrupt message i mentioned before. If anyone has had something similar or knows what this is please offer your wisdom, or if anyone wants to brainstorm and try to figure this out I would greatly appreciate it.

Thank you for reading my post and I hope I at least posted it in the rite spot. :smile:

---

### Post by Tourdog on 2010-02-24
Glasya,
It seems to me (no expert) but a wubi install exists for each boot.................  It is a "kinda of a dual boot" because  it is another OS although temporary.  Sometimes, even though the intent is to use a wubi install I think "flying fingers" can press the button for an actual "partition install" of an ISO and wubi just happens to ride along on the download and never gets used at all..

Is it possible you have/had an actual "9.10 Installed on its own partition on the hd" Ubuntu install?  It would help to explain some of what you've indicated.

---

### Post by meierfra. on 2010-02-24
> Select OS screen as if ubuntu was still there, so i chose to boot ubuntu and see if the uninstall failed or something and it gave me a corrupt or missing file message instead of booting(

This is a quite common error:  The Wubi Uninstaller was unable the remove the Wubi entry from  the Window Boot loader.  You just had to remove the line "C:\wubildr.mbr=Ubuntu" from  the file "C:\boot.ini"

But after all  your random actions, I'm sure what your current situation is. So lets check out your system: Follow these [instruction ]("http://bootinfoscript.sourceforge.net/")to run the Boot Info Script and post the RESULTS.txt.

---

### Post by glasya on 2010-02-25
Your were correct that line still exists in boot.ini and i am glad this is a common problem. I opened boot.ini as a txt (ANSI) and removed the line > "C:\wubildr.mbr=Ubuntu" and attempted to save but it said "Cannot create file C:/boot.ini" then opened the "save as" directory list showing my C drive and the folders within... i am wondering, do i simply save it as a txt in the c drive or did i miss something?   

 Also, the instructions for the bash script were for linux distros and i cannot acces ubuntu atall, further more i am not good with windows command prompt so i am not sure if its compatible with windows or how to use it in windows.

---

### Post by meierfra. on 2010-02-25
> attempted to save but it said "Cannot create file C:/boot.ini" 
Instructions to edit boot.ini:

[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

> i cannot access ubuntu at all, 
Then you will need a Ubuntu LiveCD or LiveUSB to run the Boot Info Script.

---

### Post by glasya on 2010-02-26
I may have been able to solve my issue myself thanks to a little added knowledge about boot.ini and cmd prompt. although i am not sure... i am reinstalling wubi this very second to see if i have in fact fixed the issue. once i figure out if it is fixed or not i will post again either from ubuntu or windows, hopefully ubuntu, and if i am on ubuntu i will run the bash script and display the code with my next post. 

 I prefer to run wubi because i do not think this system can handle a second partition. even if it can it wouldnt handle it very well. I am currently waiting on some chipsets and harddrives to come in aswell as my new liquid cooling system. i am in the prosses of setting up a new build using EVGA x58i SLI LE mobo and intel i7 cpu. rite now i am running a stock eMachine that i bought for $250 because my last system got "ran over" by an angry ex :frown:. But its all good, I was experimenting with linux distos to find an OS that will bring out the full potential of my new build and found ubuntu. so i am eager to learn all i can about it in preparation for my new build.

---

### Post by meierfra. on 2010-02-26
> I may have been able to solve my issue myself thanks to a little added knowledge about boot.ini and cmd prompt. although i am not sure... i am reinstalling wubi this very second to see if i have in fact fixed the issue.
??????? I have no idea what issue you might have resolved by editing boot.ini and then reinstalling Wubi.

> I prefer to run wubi because i do not think this system can handle a second partition. even if it can it wouldnt handle it very well.
Make no sense to me.  A regular installation will be easier on your system than a Wubi install.

---

### Post by glasya on 2010-02-26
> ??????? I have no idea what issue you might have resolved by editing boot.ini and then reinstalling Wubi. Well by removing the Ubuntu OS ID# i was able to reinstall wubi fully and that is what i was trying to accomplish by posting in the first place. I assume based on what i have learned recently that wubi failed to uninstall fully leaveing the ubuntu boot id and there for preventing wubi from accurately reinstalling again.

---

