---
title: "update not working"
date: 2012-08-15
forum: General Help
---

### Post by lmellen on 2012-08-15
The latest update requires the Ubuntu 12.04 LTS 64 disc to update.
When I try to update it appears as if it can't read the disc. I've burned 3 different discs, all as images. Nothing seems to work.
The only thing I didn't try was using a 32 bit disc.
The updates are downloaded, they are not being installled.
Anybody know what is going on?

---

### Post by community on 2012-08-15
Don't you have the provision for updating online?

---

### Post by mkstallings1 on 2012-08-15
Are you talking about updating an older version of Ubuntu, or is this an update of an existing Ubuntu 12.04 install?

---

### Post by lmellen on 2012-08-15
Of course,the updates were downloaded,no problem.The update manager wants the Ubuntu 12.04 LTS amd64 to finish the installation. I place the disc in the dvd drive,click on continue, it starts doing it's thing, and instead of installing the updates I just keep getting the disc request over and again.
There is a chance the updates are 32 bit?? If so I might need to use a 32 bit disc?? 

Thanks for the reply - Larry

---

### Post by lmellen on 2012-08-15
I used the windows installer from the Ubuntu website. The laptop a new dell XPS as of 5/12.It already had a Windows 7 64 bit system installed , so I installed the Ubuntu 64 bit OS for a dual boot..I've had no problems with update till now. It's trying to update Libre Office and a few other things, which I believe are still 32 bit(?). I downloaded a 12.04 32 bit, I'll burn another disc and try that later.
Thanks for the reply - Larry

---

### Post by community on 2012-08-15
Was it a wubi install or normal installation? While updating using update manager on 12.04, I don't think it will ask for a disc if updates are downloaded successfully.

---

### Post by lmellen on 2012-08-15
I used the wubi installer.Would the wubi installer keep the 12.04 disc from mounting properly?
As far as I can tell the updater can't read the disc. I hate to spend $$ for a new dvd drive if that is not the problem. The drive reads all other discs, no problem.

---

### Post by raja.genupula on 2012-08-15
Hi open your terminal and type this

```
sudo apt-get update
sudo apt-get upgrade
```

post the errors you are getting.

thank you .

---

### Post by lmellen on 2012-08-15
raja.genupula

When I ran:

 sudo apt-get update
 sudo apt-get upgrade 

It installed 35 of the 38 updates. The 3 left were:

                   "Daemon which notifies about package updates"
                   "Files shared between up-date notifier and other packages"
                   "Apply a diff file to the original"

When I went back to update manager I had the same problem with the disk. I went back to terminal and ran the above 2 commands again.  
This is what I got:

W: Duplicate sources.list entry cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120425)_dists_precise_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

When I ran apt-get update again, I got the same message.

Thank you for the assistance - Larry

---

### Post by lmellen on 2012-08-16
I must get about 50 of copies of this message.

W: Duplicate sources.list entry cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120425)_dists_precise_rest ricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

Sudo apt-get update just produces the same results.

---

### Post by mkstallings1 on 2012-08-16
If you go into synaptic and look under software sources, is cd rom one of your sources?  Uncheck that and then see if it gets cleard up when you run apt-get update.

---

### Post by raja.genupula on 2012-08-16
> **mkstallings1 said:**
> If you go into synaptic and look under software sources, is cd rom one of your sources?  Uncheck that and then see if it gets cleard up when you run apt-get update.

+1 

and one more way is , type this in terminal

```
sudo gedit /etc/apt/sources.lists

```then look at the CD-ROM and place ## before it , click save and close it . then again in terminal type as```
 sudo apt-get update
```P.S : Please place the code in code tags

---

### Post by lmellen on 2012-08-16
raja.genupula

The response I get to:

sudo gedit /etc/apt/sources.lists

is:

(gedit:5320): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.local/share/recently-used.xbel

I also get a blank pop up page from notepad.   

PS: Where are the code tags?

---

### Post by community on 2012-08-16
I don't think it is the problem with wubi install? Was the update successful anytime before? Look into the software sources..One of your sources may be 12.04 disc.

---

### Post by lmellen on 2012-08-16
mkstallings1

I couldn't find cd rom in synaptic, software or cd rom. 
Thanks for the reply - Larry

---

### Post by lmellen on 2012-08-16
The update has worked fine since I installed Ubuntu.
The cd rom works fine also.
The only problem I've had is this time when the update manager asked for the disc.
Thanks for the reply- Larry

---

### Post by community on 2012-08-16
Check once more in any of the tabs under Update Manger>Settings.In Other software/Ubuntu software...

---

### Post by deadflowr on 2012-08-16
Open up update manager, go to settings in left-bottom corner, go to other software, uncheck anything that says cd, go to ubuntu software and make sure the installable from cd/dvd section is unchecked. Close(do not revert) and rerun the update, either click check or use  the terminal.

---

### Post by lmellen on 2012-08-16
Thank you deadflowr,

 That seemed to fix it. There was nothing in the "other software" tab, but   2(duplicate) 12.04 LTS amd64 selections listed in the "Ubuntu software" tab.
 I unchecked them both and the update worked!
You saved me a massive headache.

 Thanks again -- Larry

---

