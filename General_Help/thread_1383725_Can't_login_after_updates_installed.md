---
title: "Can't login after updates installed?"
date: 2010-01-17
forum: General Help
---

### Post by cAlpha on 2010-01-17
I'm running Ubuntu 9.10.  I installed all suggested updates and then rebooted.  Upon doing so, I noticed an extra kernel option (I can't recall the version number, but vaguely recall the one I was used to ending in --15 and the new one being --17) and I booted into the newer one.  

The splash screen looks as it should and the boot appears to be working properly when I'm presented with a simple login screen and a message box in the upper right that says: "Install Problem!  The configuration defaults for GNOME Power Manager have not been install correctly.  Please contact your computer administrator."

Regular login (using my current login/pass) appears to work but I'm returned to the same screen after a few seconds.  

Booting into the --15 kernel gives the same screen and error, and subsequent results.  

The following:
[I]sudo dpkg --configure -a
sudo apt-get -f install[/I]

followed by a reboot leaves me in the same position I'd been in.  

This seems to have been a bug in previous versions of Ubuntu (per a quick search), but I'm confused about why this would have only BECOME an issue after the new kernel was loaded as part of the automatic updates--my previous 9.10 installation worked like a charm.  :-/

---

### Post by warfacegod on 2010-01-17
Go into the recovery kernel of the newest number and select drop to shell. Once their, type passwd username (username is the name you login with) hit enter. Type a new password (don't forget what it is) hit enter. Type reboot, hit enter.

---

### Post by happyhamster on 2010-01-17
Try booting until the login screen appears. Instead of logging in, press Ctrl-Alt-F3 to enter a console. Login, and run:

killall gnome-power-manager

- Next restart the powermanager, and make a note of any errors shown:

gnome-power-manager --no-daemon

- If there's no output, try:

killall gnome-power-manager
gnome-power-manager --no-daemon --verbose

- After this, you can try starting X using:

sudo service gdm restart

- Which command could also provide some feedback. Good luck.

---

### Post by warfacegod on 2010-01-17
> **happyhamster said:**
> Try booting until the login screen appears. Instead of logging in, press Ctrl-Alt-F3 to enter a console. Login, and run:

killall gnome-power-manager

- Next restart the powermanager, and make a note of any errors shown:

gnome-power-manager --no-daemon

- If there's no output, try:

killall gnome-power-manager
gnome-power-manager --no-daemon --verbose

- After this, you can try starting X using:

sudo service gdm restart

- Which command could also provide some feedback. Good luck.

I was under the impression that starting X was done with:

```
startx
```

---

### Post by cAlpha on 2010-01-17
> **warfacegod said:**
> Go into the recovery kernel of the newest number and select drop to shell. Once their, type passwd username (username is the name you login with) hit enter. Type a new password (don't forget what it is) hit enter. Type reboot, hit enter.


Thanks for your reply.  I tried entering valid login and invalid pass just to see if my login/pass got messed up during the update.  Doing so didn't seem to 'work' in the same way as my regular login/pass did, so I don't think it has to do with my login info.  Other thoughts?

---

### Post by happyhamster on 2010-01-17
> **warfacegod said:**
> I was under the impression that starting X was done with:

```
startx
```
Yes, that works too (assuming no xserver is already active). Restarting GDM brings you a fresh graphical login.

---

### Post by cAlpha on 2010-01-17
> **happyhamster said:**
> Try booting until the login screen appears. Instead of logging in, press Ctrl-Alt-F3 to enter a console. Login, and run:

killall gnome-power-manager

- Next restart the powermanager, and make a note of any errors shown:

gnome-power-manager --no-daemon

- If there's no output, try:

killall gnome-power-manager
gnome-power-manager --no-daemon --verbose

- After this, you can try starting X using:

sudo service gdm restart

- Which command could also provide some feedback. Good luck.

Cool, I'll give this a shot...will let you know how it goes.

---

### Post by cAlpha on 2010-01-17
Alrighty...

both "gnome-power-manager ..." commands gave the following:

"(gnome-power-manager: 2435) Gtk-WARNING**: cannot open display"

Rebooting again gave the same problematic login screen.  Any thoughts on how to proceed?

---

### Post by warfacegod on 2010-01-17
I believe it ought to have been gnome *desktop* manager not *power*

---

### Post by cAlpha on 2010-01-17
> **warfacegod said:**
> I believe it ought to have been gnome *desktop* manager not *power*

Why desktop manager--the power manager was the process indicated in the error message on the problematic login screen?

---

### Post by happyhamster on 2010-01-17
You could try removing and re-installing gnome-power-manager. It should be pretty safe because nothing depends on it except ubuntu-desktop (which is merely an empty metapackage).

- Again, press Ctrl-Alt-F3 when you reach the login screen. Login and issue:

sudo apt-get update

sudo apt-get remove --purge gnome-power-manager

- Apt should warn you it will remove 2 packages: gnome-power-manager and ubuntu-desktop. If so, proceed. Next, re-install:

sudo apt-get install gnome-power-manager ubuntu-desktop

- This might pull in some other packages you had chosen to remove before. Reboot:

sudo reboot

- Good luck.

---

### Post by warfacegod on 2010-01-17
> **cAlpha said:**
> Why desktop manager--the power manager was the process indicated in the error message on the problematic login screen?

My apologies, I'd forgotten that from your original post.

---

### Post by cAlpha on 2010-01-17
Alright, tried removing and reinstalling power manager and desktop manager.  

Did as you'd suggested, happyhamster, and got:
"Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main gnome-power-manager 2.20.1-0ubuntu1
  Could not resolve 'us.archive.ubuntu.com'"

and the same message for desktop-manager.  

Rebooting, I notice the error message that had previously been in the upper right (ie, "Install Problem! ...") is gone, but I still get the same sparse login splash and can't get to my desktop.  

The us.archive.ubuntu.com does exist and appear to be up.  Is this then simply an intermittent access issue on my side, or something else?  Namely, should I just wait a bit, try again and see what happens, or try something different?

---

### Post by happyhamster on 2010-01-17
> **cAlpha said:**
> Alright, tried removing and reinstalling power manager and desktop manager.  

Did as you'd suggested, happyhamster, and got:
"Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main gnome-power-manager 2.20.1-0ubuntu1
  Could not resolve 'us.archive.ubuntu.com'"

and the same message for desktop-manager.  

I don't understand. If you don't have networking, then "sudo apt-get update" should have warned you. Is gnome-power-manager uninstalled now?

> 
Rebooting, I notice the error message that had previously been in the upper right (ie, "Install Problem! ...") is gone, but I still get the same sparse login splash and can't get to my desktop.  
So perhaps some other part of gnome fails?

> 
The us.archive.ubuntu.com does exist and appear to be up.  Is this then simply an intermittent access issue on my side, or something else?  Namely, should I just wait a bit, try again and see what happens, or try something different?
It could be that the gconf database is corrupted (stores settings for gnome apps). Are you perhaps low on disk space?

edit: you can check with the command:  df

---

### Post by happyhamster on 2010-01-17
Do you get networking when booting in recovery mode, and choosing the "netroot" option? If so, re-install from there:

sudo apt-get update

sudo apt-get install gnome-power-manager ubuntu-desktop

- In case you don't get the "netroot" option, run:

dhclient eth0

- to get networking (assuming eth0 is your device), then run the above apt-get commands.

---

### Post by cAlpha on 2010-01-17
> **happyhamster said:**
> I don't understand. If you don't have networking, then "sudo apt-get update" should have warned you. Is gnome-power-manager uninstalled now?


So perhaps some other part of gnome fails?


It could be that the gconf database is corrupted (stores settings for gnome apps). Are you perhaps low on disk space?

edit: you can check with the command:  df

Yes (~120MB on my C drive and ~200MB on my (shared partition) F drive). 


> **happyhamster said:**
> Do you get networking when booting in recovery mode, and choosing the "netroot" option? If so, re-install from there:

sudo apt-get update

sudo apt-get install gnome-power-manager ubuntu-desktop

- In case you don't get the "netroot" option, run:

dhclient eth0

- to get networking (assuming eth0 is your device), then run the above apt-get commands.

I have vague memory of a root w networking option when I was in recovery mode earlier today.  Let me see if I can boot into that, else I'll give your second suggestion a try.  Will report back shortly...thanks for your help, man.

---

### Post by cAlpha on 2010-01-17
K, tried both.  

I get 
"DHCPDISCOVER on eth0 255.255.255.255 port 67 interval 4"

a number of times and then 
"No DHCPOFFERS received.
No working leases in persistent database - sleeping"

for each (the 'eth0' portion obviously changes doing the first way you suggested).

So it seems I can't connect.  Perhaps an easier question--is there any way to collect a number of files I have on my desktop within that installation and then simply reinstall?  

I don't really care about having to adjust defaults and what not to get my system the way it had been, but I'd done a bit of work that I'd saved on the desktop that I'd REALLY like to avoid losing.  Any way to access that or other ideas on how to fix this?

---

### Post by happyhamster on 2010-01-17
> **cAlpha said:**
> I don't really care about having to adjust defaults and what not to get my system the way it had been, but I'd done a bit of work that I'd saved on the desktop that I'd REALLY like to avoid losing.  Any way to access that
One way is booting from a live cd. Simply boot into a live session, mount your disks (they should be visible and mountable from within your file browser), and copy the stuff you want rescued onto the shared partition or onto an USB stick or so.

> 
other ideas on how to fix this? 
No, not really :(

---

### Post by cAlpha on 2010-01-17
lol, the boot from hell continues...

I booted from the disk and attempted to find the the location of my 9.10 files to no avail.  The 'File System' disk ended up containing the files from my previous installation (8.04) rather than the new (9.10) installation.

The closest thing I found was the 'ubuntu' folder on the C drive.  It contains a 'boot' folder, a 'root.disk' file and 'swap.disk' file.  I'm thinking the root.disk file is the one I need to access but how do I go about it?  

*sigh*  Appreciate your help, man.

---

### Post by happyhamster on 2010-01-17
> **cAlpha said:**
> lol, the boot from hell continues...

I booted from the disk and attempted to find the the location of my 9.10 files to no avail.  The 'File System' disk ended up containing the files from my previous installation (8.04) rather than the new (9.10) installation.

The closest thing I found was the 'ubuntu' folder on the C drive.  It contains a 'boot' folder, a 'root.disk' file and 'swap.disk' file.  I'm thinking the root.disk file is the one I need to access but how do I go about it? 
Is that a wubi install? I know close to nothing about those. I did find this though:
[https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?](https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?)

```

How can I access my Wubi install and repair my install if it won't boot?

Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:

sudo mkdir /win
sudo mount /dev/sda1 /win

Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein

sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

Now the content of the virtual disk will be visible under /vdisk. 7.04 users will have to install ntfs-3g first and specify it as fstype to gain r/w access.

```
And then move your files onto an USB stick or such.

Another way to get to your files (it will be a pain though): do a regular boot into the login screen, press Ctrl-Alt-F3 to drop into a console, and manually mount, find and copy everything from here. This will be no fun.

---

### Post by cAlpha on 2010-01-17
It worked!  Whew, you saved me about a week's worth of work (and painful work at that).  

Well, getting those files back will need to be good enough for now.  

Thanks for your help, I appreciate it.

---

### Post by happyhamster on 2010-01-17
> **cAlpha said:**
> It worked!  Whew, you saved me about a week's worth of work (and painful work at that).  
Congrats!

> 
Well, getting those files back will need to be good enough for now.  

My thoughts: a few configuration files are corrupted because they were being written to when the partition ran out of space when installing the new kernel (this is pure speculation though).
To repair this you would have to re-generate those config files. A practical, but random way of doing that is re-installing apps (gnome system-related stuff). You'd probably have to have a working internet connection at this point to make that procedure safe (I don't think everything will just be available in cache). You'll also need to make available some free disk space, because else stuff might get corrupted again.

If this was my system (full access): after a lot of experimenting trying to save it, in the end I would just do a complete re-install. But it would have been fun :)

---

### Post by JGMS on 2010-01-26
L.S.,

I experience the very same problem of a login loop after an update to 2.6.31-17. THe update was probably interrupted by a network problem. 

From the conversation above I can not understand which files from which directories need to be copied from the LiveCD into where on the harddisk.

Could you please specifiy so that I can too try to solve this nasty problem. 

Many thanks ahead, JGMS

---

### Post by happyhamster on 2010-01-26
> **JGMS said:**
> L.S.,

I experience the very same problem of a login loop after an update to 2.6.31-17. THe update was probably interrupted by a network problem. 

From the conversation above I can not understand which files from which directories need to be copied from the LiveCD into where on the harddisk.

Could you please specifiy so that I can too try to solve this nasty problem. 

Many thanks ahead, JGMS
Well, the live-cd was used to get files off the harddisk instead (as a last resort to recover data), not to repair the installation.

- In your case, try booting until the login screen. Instead of logging in, press: Ctrl-Alt-F3 to drop into a console. Login, and run:

sudo dpkg --configure -a

- If that worked, run:

sudo apt-get update
sudo apt-get upgrade

- Then reboot:

sudo reboot

- If that doesn't work, could you show the errors here? (especially those from "sudo dpkg --configure -a"). Good luck.

---

### Post by cAlpha on 2010-02-13
I thought I'd share what worked (and the reasoning) since I ran into this issue again last night and was just able to fix it.  

The difficulties I had can be tied directly to being low on disk space both times this happened.  

I noted the first time that it happened after installing updates, and last night, it happened after installing a new program from within Synaptec.  In each case, rather than being related to the specific files being installed, the problem was that each install dried up all my remaining disk space.  I don't know enough about GPM, or the kernel frankly, to comment on WHY I got the GPM error as opposed to any of the other internals that need disk spaces during boot, but that's the way it fell out.  

To fix it, I just booted from the Live CD and mounted my Ubuntu file system.  At this point, you just need to find a few things you can delete to shore up a bit of space.  Open a terminal window and remove the files.  I got errors when trying to delete from within the file browser, my guess related to permissions, hence relied on "sudo rm [...]".

---

### Post by SerpentHearted on 2010-02-18
i'm having the same issue here, although i have plenty of space (4gb) left on the partition. I'm able to login and run xfce sessions. I still get the error message about gnome power manager but i can log in and work anyway. If i try to log in to gnome desktop i just get the error message and that's the end.

have tried removing gnome power manager and gnome desktop and reinstalling, but to no avail.

currently downloading the files for a re-install. Most annoying! Hopefully this will solve the problem anyway.

---

### Post by SerpentHearted on 2010-02-18
well... full reinstall did not fix this for me.

GOD so annoying. I guess it's somethng wrong in the latest update, because before that I actually had a reasonably smooth running installation of 9.10 - much better than any of the previous releases.

Meh - i guess it is back to windows2000 for me :(

---

### Post by bjarkih on 2010-03-07
I found this thread searching for a solution to my own "power manager" problem, turned out it was a full HD.  After deleting some files everything went back to normal :-)  Thank you all for the help.

---

