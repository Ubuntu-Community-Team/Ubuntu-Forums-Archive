---
title: "Office 2007 in wine?"
date: 2011-09-03
forum: General Help
---

### Post by cptrohn on 2011-09-03
OK, so I got a free copy of Office 2007 Enterprise from work and I am trying to get it to install on Ubuntu with wine....  Followed the steps they had listed on the page at wine, BUT when I click on the disk icon, then click open and then right click on the setup.exe file in the disk's folder I get a swirling cursor for a minute or so and then nothing happens and the set up just stops...  

Anybody that has been through this process with a similar problem, any help would be greatly appreciated!

---

### Post by KingYaba on 2011-09-03
I was frustrated trying to work with wine that I dug up my old XP disc and just used Virtualbox so I could use CS3. Maybe you could do the same? I know, it's not perfect.

---

### Post by searchfgold6789 on 2011-09-03
I am able to install this program perfectly. I think I even went to the website and gave it my Platinum Rating.
Try installing it from the terminal. Just type in "wine " (including the space at the end) and then click'n'drag the setup.exe file from your file manager and into the terminal. Then press Enter.

---

### Post by cptrohn on 2011-09-03
> **searchfgold6789 said:**
> I am able to install this program perfectly. I think I even went to the website and gave it my Platinum Rating.
Try installing it from the terminal. Just type in "wine " (including the space at the end) and then click'n'drag the setup.exe file from your file manager and into the terminal. Then press Enter.

Hmm on I gave this a try and this is what I got in terminal.
```
user@ubuntu:~$ "wine "'/media/OFFICE12/setup.exe' 
bash: wine /media/OFFICE12/setup.exe: No such file or directory

```

---

### Post by searchfgold6789 on 2011-09-03
Omit the double-quotation-marks = "```
wine /media/OFFICE12/setup.exe
```

---

### Post by cptrohn on 2011-09-03
> **searchfgold6789 said:**
> Omit the double-quotation-marks = "```
wine /media/OFFICE12/setup.exe
```


Ok, so I did that and I come up with this error.. (which is probably why it won't run in the first place eh?) 

```
user@ubuntu:~$ wine /media/OFFICE12/setup.exe
Warning: could not find DOS drive for current working directory '/home/user', starting in the Windows directory.
wine: cannot find '/media/OFFICE12/setup.exe'

```

---

### Post by cptrohn on 2011-09-03
OK, so I cut and pasted my error in a browser window and came back with this from the wine wiki..

4.2. I double-clicked on an .exe file, but the system said "The file foo.exe is not marked as executable..."
If the dialog says "Read about the executable bit", with a hyperlink, try clicking on the hyperlink and reading about the executable bit.
If the file is on your hard drive, right-click it, choose Properties / Permissions, and check "Allow executing file as program".
If the file is on a CD-ROM, you can run it from the commandline as described above. Or, if you know how to use 'mount', remount the cd-rom to mark all files as executable with a command like  mount -o remount,mode=0777,exec /media/cdrom but using the real mount point if it's different from /media/cdrom.


I do have both the original Office DVD and I also made a copy of the .iso using dd....  I did get the "executable bit" error and went back into the file and changed the permissions on the OFFICE12 file...  I wonder do I need to go into everything.. word, outlook, etc and change all of their permissions as well?

---

### Post by gandaran on 2011-09-04
copy the whole office cd/dvd to ubuntu desktop, don't do it in ISO format, just use plain copy/paste, the only file you have to change permissions to allow executing is the office installer launcher then right click the launcher and open with wine loader.

---

### Post by cptrohn on 2011-09-04
> **gandaran said:**
> copy the whole office cd/dvd to ubuntu desktop, don't do it in ISO format, just use plain copy/paste, the only file you have to change permissions to allow executing is the office installer launcher then right click the launcher and open with wine loader.

Darn it, still no luck....  I do have XPpro and 7 Pro both loaded in VB and will use that as a last resort I guess... Got an email saying to give Play on Linux a try, so I will give that a go.  I'll let everybody know if it works or not.

---

### Post by gringo8217 on 2011-09-04
i installed it through play linux with no problems at all using windows 2007 office disk !!

---

### Post by gringo8217 on 2011-09-04
i installed using play linux with no problems !!

---

### Post by cptrohn on 2011-09-04
Ahhh Success!!

Play on Linux did the trick and was EXTREMELY easy to use as well...  fired right up from the Office DVD...  Word, Excel and Power Point all worked...  Access and Groove and Publisher it seems do not work with Wine though...

---

### Post by Mark Phelps on 2011-09-04
Only the "core: Office apps (Word, Excel, Powerpoint) appear to work well with Wine.  Some other Office 2007 apps, Access and Outlook, do not work.  Others (Info Path, Visio, Project) haven't had enough testing to know for sure ... but they probably don't work either.

It took Codeweavers three years to get SOME of Office 2007 working.  By the time they did, Office 2010 was already out.

And before you ask, Office 2010 does NOT work.

If you're going to rely on using Office 2007 on a daily basis, you're really better off using a dual-boot system (or VirtualBox) with Office 2007 running in MS Windows.

---

