---
title: "LibreOffice open files disappearing"
date: 2012-07-03
forum: General Help
---

### Post by Thinkintuit on 2012-07-03
I'm having a recurring problem with LibreOffice in which I have a number of files open, but can't access them. Normally if I click on the LibreOffice icon to the left of the screen, I see small versions of all the files I have open. But when this problem crops up (which has been happening fairly frequently), clicking on the icon just opens a new file. Also, when this happens the little triangles that show up next to the icon disappear. However, if I then start closing files, the previously opened ones will appear, apparently in the order in which I had first opened them.

It's not clear to me whether this is a LibreOffice problem, or a Unity/Ubuntu 12.04 problem. It may be that the problem lies with multiple instances of a program being opened in Unity.

The only way I've found so far to stop this problem is to shut down the computer and restart it. 

Has anyone else encountered a problem like this? Any ideas on how to prevent it from happening, or--if it does occur--to get it working again without restarting the computer?

I'm using LibreOffice 3.5.4.2 Build ID: 350m1(Build:2)

---

### Post by efflandt on 2012-07-03
Just on the odd chance that it is related to problems I have bring up update manager when it checks for updates and starts automatically minimized, or sometimes when minimizing something from one of my own launchers (that launches a terminal script to launch a java gui game), **try switching to a different workspace with the workspace switcher and see if it works then**.  That seems to work when I cannot bring up the hidden update manager.

---

### Post by Thinkintuit on 2012-07-04
> **efflandt said:**
> **try switching to a different workspace with the workspace switcher and see if it works then**

Thanks for the suggestion! I'll try that the next time the problem occurs.

---

### Post by Thinkintuit on 2012-07-06
The problem just recurred; I tried switching to a different workspace per efflandt's suggestion, but that had no effect.

---

### Post by Qu4rk on 2012-07-16
> **Thinkintuit said:**
> The problem just recurred; I tried switching to a different workspace per efflandt's suggestion, but that had no effect.

I'm experiencing a similar problem to you.  My Libre icons are not locked to the sidebar.  But at times, I get a weird blank space the size of an icon between and then a unity icon that is blank Libre office icon (i.e. it doesn't have the green text & stuff a spreadsheet) & not I can't click it.  I have to open a new document that's a text document which will open up writer, then use the windows menu to access the spread sheet.  

Its a little anoying, so if you find a solution, I will try it for my problem too.  Because I don't know where to start.

---

### Post by karlkropf on 2012-07-17
I've found the same problem with Writer and Calc.  One of the symptoms is that the generic LibreOffice icon in the launcher has the 'on another workspace' open triangle (>) on the left edge.  As per efflandt's suggestion I've tried all (4) workspaces but the documents are not on any of them.  Also tried increasing and decreasing the number of workspaces but not luck.

There would seem to be a phantom workspace.

The problem only seems to have started fairly recently so wonder if it is a regression.

---

### Post by karlkropf on 2012-07-17
Just spotted this 

<http://askubuntu.com/questions/144151/libreoffice-icons-missing-from-unity-task-panel>

which gives a workaround - super+W - which shows all open windows.

Also suggests it's a known bug <https://bugs.launchpad.net/ubuntu/+source/bamf/+bug/995916>

---

### Post by Thinkintuit on 2012-07-20
> **karlkropf said:**
> a workaround - super+W - which shows all open windows


Thanks, karlkropf! super+W is a very useful workaround. The bug has occurred 3 times so far this morning, which is unusually frequent. At least with super+W I don't have to restart my computer. 

Thanks also for letting us know that it's a known bug. Hopefully there will be a fix before too long.

---

### Post by Qu4rk on 2012-07-20
> **Thinkintuit said:**
> Thanks, karlkropf! super+W is a very useful workaround. The bug has occurred 3 times so far this morning, which is unusually frequent. At least with super+W I don't have to restart my computer. 

Thanks also for letting us know that it's a known bug. Hopefully there will be a fix before too long.

Yes, thanks karlkropf!

---

### Post by drmtiede on 2012-08-21
some time has gone by.

has anything come up jet? i have the same problem with the calc icon not showing up.

ubuntu 12.04 &  LibreOffice 3.5.4.2 
Numero di build: 350m1(Build:2)

---

### Post by Qu4rk on 2012-08-21
I'm using the same version of both as you are.  

I still have to use Super + W.  Its a known bug, so I guess we have to be patient.

---

### Post by twipley on 2012-08-24
Thanks for the "Super + W" workaround!

Having just installed the 12.04.1 iteration of Precise, I was impressed to find out such a bug is still present (being an LTS).

EDIT: [https://bugs.launchpad.net/unity/+bug/1026426](https://bugs.launchpad.net/unity/+bug/1026426) -- 350 as the heat value at the time of this writing.

---

### Post by mktrejo on 2012-08-27
I have had this problem for a while now since I installed Ubuntu 12.04, does anyone know when a fix would be committed?

---

### Post by brazov on 2012-08-29
I am not sure that I had exactly the same problem, but I solved by fixing also LibreOffice Calc in the launcher (I removed it after having installed Ubuntu). Don't ask me why it works! :lolflag:

EDIT: ...mmm actually it does not work. I found the (wrong) solution by googling, but I have the same problem again. So I had to revert to the super+W workaround. :(

---

### Post by boardman on 2012-09-11
Hi all. I came across this because I have the exact same problem.

I have not tried the super-W yet but one solution I have found is to middle click the libre icon in the menu. This magically brings one of the windows to the top. Last time I tried this middle clicking repeatedly brought differnt windows to the fore. super-W looks like a much nicer suggestion.

---

### Post by typhoon_tip on 2012-09-16
Hey guys, this bug annoyed me for ages. On work level, since we install many Ubuntu workstation, is an absolute pain in the ***, to put it very mildly. Absurd that is not being solved yet... I would love to help as well.

Anyway, there is a workaround that works quite well, found in the bug report:
```
sudo gedit /etc/libreoffice/sofficerc
```

Line Logo=1 change to Logo=0, save and exit (do not touch other settings !).

Restart all LibreOffice apps (better logoff/login again). This setting has the effect to remove the splash screen at boot of LibreOffice, which seems to make the problem disappear (at least for me, I have not had it happen since I did the trick).

For those who installed newest one from LibreOffice website manually, do this command instead:
```
sudo gedit /etc/libreoffice3.6/program/sofficerc
```

Cheers.

---

### Post by brazov on 2012-09-17
It seems that the recent updates solved the problem. At least in my case.

---

### Post by xavivaldi on 2012-10-12
Thanks, Typhoon_Tip! I had the exact same problem, with the same builds of Ubuntu and LibreOffice and the workaround worked as a charm

---

### Post by drmtiede on 2012-10-16
Seems that also in my case the updates solved the problem. in any case i shut off the splash screen, you newer know... 

as for my part i would mark the issue as [solved]

---

