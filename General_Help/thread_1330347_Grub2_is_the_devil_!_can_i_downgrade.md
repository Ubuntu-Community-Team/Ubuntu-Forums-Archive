---
title: "Grub2 is the devil ! can i downgrade ?"
date: 2009-11-18
forum: General Help
---

### Post by zonemikel on 2009-11-18
Just when i got used to menu.lst and adding options to it and setting my resolution and such .... bam its all a thing of the past. 

I have to edit two files just to change the resolution in grub2 and after that i still cant really choose between them (eg have different menu.lst options for different resolutions). 

All that aside my main gripe with grub is this ! 

1.) i dd my drive to another drive on the system eg dd if=/dev/sda1 of=/dev/sdb1
2.) i reboot my system 

them magically my system is booting off of /dev/sda1 but has /dev/sdb1 mounted as the root file system, wth. I never changed grub, all i did was dd. So this is very confusing, i'll be thinking i'm using one file system and its using the other. Why would grub just automatically do that ? 

Also all the scripting in the files just to add options to the menu are confusing as hell to me (/etc/grub.d/**). I did manage to add a few options but it seems like overkill. 

Is there anyway to downgrade ? Or does anyone know why grub would behave in this "self aware" sort of way ? 

I guess grub2 might be better, i just dont have time to go learn it right now !

---

### Post by Giblet5 on 2009-11-18
Grub2 is the default on Karmic because someone thought it would be a good idea.

Ever read Dilbert? I suspect the person who made this decision has two little points of hair above his ears.

You can install "legacy" grub and uninstall grub2.

IMO, it's not even close to ready...but I'm sticking with it because I like pain.

---

### Post by drs305 on 2009-11-18
There is information on how to do it on the GRUB 2 community documentation page:
[https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202")

If you would like to resolve issues you are having with G2 there is probably information there that might help as well. And of course you can always ask here (although you already have, sort of).

---

### Post by zonemikel on 2009-11-18
Ya its the default on ubuntu 9.10 also ! makes all my old rescue cd's useless. So do i just sudo apt-remove or something ? then sudo apt-get grub ? or will that reinstall the latest version ?

oh nvm ... read what the nice people say mikey 

> 
**Reverting to GRUB Legacy**

 If a user chooses to return to GRUB legacy (0.97), these steps will remove GRUB 2 and install GRUB.  
The command line produces a cleaner uninstall and reinstallation. While adding and removing the packages can be accomplished with Synaptic, certain steps must be accomplished in a terminal. 

[LIST=1]
[*]Open a terminal: Applications, Accessories, Terminal. 
[*]Make backup copies of the main GRUB 2 folders & files. (Optional) 

[LIST]
[*]sudo cp /etc/default/grub /etc/default/grub.old 
[*]sudo cp -R /etc/grub.d /etc/grub.d.old 
[*]sudo cp -R /boot/grub /boot/grub.old 
[/LIST]
[*]Remove GRUB 2 
[LIST]
[*]sudo apt-get purge grub2 grub-pc 
[*][IMG]https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=important.png[/IMG] The system will be unbootable until another bootloader is installed. 
[*]Once the packages are removed, many files will still remain in '/boot/grub'  
[/LIST]
[*]Install GRUB 0.97 
[LIST]
[*]sudo apt-get install grub 
[/LIST]
[*]With *grub* installed, the user must still create the *menu.lst* and *stage1/stage2* files by running the following two commands. 

[LIST=1]
[*]sudo update-grub 

[LIST]
[*]Generates *menu.lst*  

[LIST]
[*]Tab to "Yes" when prompted. 
[/LIST]
[/LIST]
[*]sudo grub-install /dev/sdX 

[LIST]
[*]Choose the correct device (sda, sdb, etc), normally the one on which Ubuntu is installed. 
[*]Creates the *stage1* & *stage2* files in */boot/grub* and writes to the MBR. 
[/LIST]
[/LIST]
[*]Reboot 
[/LIST]
[IMG]https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=important.png[/IMG]


---

### Post by falconindy on 2009-11-18
Since it hasn't been mentioned yet, you'll definitely want to pin your grub-legacy package so that it isn't upgrade next time you do `apt-get upgrade`. To do so:

```
echo "grub hold" | sudo dpkg --set-selections
```

To undo the above, use 'install' in place of 'hold'.

---

### Post by zonemikel on 2009-11-18
> **falconindy said:**
> Since it hasn't been mentioned yet, you'll definitely want to pin your grub-legacy package so that it isn't upgrade next time you do `apt-get upgrade`. To do so:

```
echo "grub hold" | sudo dpkg --set-selections
```To undo the above, use 'install' in place of 'hold'.

Thanks man lots of help.

your site is very informational ... ya it looks like it is old world because i do see those icons in [http://en.wikipedia.org/wiki/Old_World_ROM](http://en.wikipedia.org/wiki/Old_World_ROM)

---

### Post by ericwwheeler on 2009-12-11
were you able to successfully downgrade to grub legacy?  I followed all the instructions on downgrading and still am having grub 2 boot.

---

### Post by Strigoides on 2010-02-06
Hey, is there any way to downgrade using the LiveCD?
I ask because Grub2 Has decided not to let me get into my Ubuntu install

---

### Post by drs305 on 2010-02-06
> **Strigoides said:**
> Hey, is there any way to downgrade using the LiveCD?
I ask because Grub2 Has decided not to let me get into my Ubuntu install

Here is a guide to do what you are requesting (as well as trying to fix Grub 2 - see the Command line section). There are people here who can probably assist you if you want to salvage Grub 2.

[https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202")

---

### Post by Strigoides on 2010-02-06
> **drs305 said:**
> Here is a guide to do what you are requesting (as well as trying to fix Grub 2 - see the Command line section). There are people here who can probably assist you if you want to salvage Grub 2.

[https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202)
Yeah, I tried doing that from the LiveCD, but nothing happened, I got the same old Grub 1.97 beta 4 command line upon booting.

---

### Post by drs305 on 2010-02-07
> **Strigoides said:**
> Yeah, I tried doing that from the LiveCD, but nothing happened, I got the same old Grub 1.97 beta 4 command line upon booting.

If you were using the LiveCD and attempting to follow the instructions in the link cited, did you chroot into your actual installation?  The instructions are meant to be used from within a normal login. 

If you try to do the steps as outlined *but from a LiveCD* you will not be making any changes to your real system partition. There are instructions on how to "chroot" earlier in the guide. 

Just a note: make sure you have internet capability after you "chroot" and before you start removing packages. In some cases additional system resources such as /dev/pts and /sys must be mounted, as well as copying over /etc/resolve.conf.

Grub 2 has a simple command to install itself to a mounted partition without having to chroot. I don't know if there is a similar capability in Grub legacy. Someone still using the legacy version may be able to answer that question.

---

### Post by Strigoides on 2010-02-08
Will this still work if Ubuntu is not on a separate partition, because I installed using wubi, so my Windows install and Ubuntu are on the same partition. The only reason I really want to get into my Ubuntu install is to be able to back up /home before I install Ubuntu properly to a seperate partition.
Thanks

---

### Post by drs305 on 2010-02-08
> **Strigoides said:**
> Will this still work if Ubuntu is not on a separate partition, because I installed using wubi, so my Windows install and Ubuntu are on the same partition. The only reason I really want to get into my Ubuntu install is to be able to back up /home before I install Ubuntu properly to a seperate partition.
Thanks

Since your goal is to access your wubi install, let's get straight to the problem and bypass Grub. 

For this method, you must already have booted to a normal Ubuntu system (which apparently you can't) or use the LiveCD. You can mount your wubi install and access it's files by running the following commands. If your Windows install is not on [COLOR="DarkRed"]sda1[/COLOR], make the appropriate changes (sdb1, etc):

```

sudo mkdir /mnt/windows  /mnt/vdisk
sudo mount /dev/[COLOR="DarkRed"]sda1[/COLOR] /mnt/windows
sudo mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/vdisk
```

You wubi folders/files should be accessible in /mnt/disk

---

### Post by Strigoides on 2010-02-09
Thank you
I have been able to access my wubi files using this method and have reinstalled onto a separate partition successfully. GRUB 2 is behaving itself so far, and the computer is booting straight to GRUB rather than to the windows bootloader, do you think I should still downgrade considering the history of problems I have had with GRUB 2?

---

### Post by drs305 on 2010-02-09
> **Strigoides said:**
> GRUB 2 is behaving itself so far, and the computer is booting straight to GRUB rather than to the windows bootloader, do you think I should still downgrade considering the history of problems I have had with GRUB 2?

Are you having any problems with Grub 2 now? Wubi creates it's own set of challenges and if Grub 2 is working correctly now I'd stick with it. 

If it isn't working and you only have Ubuntu and Windows, we should be able to fix any problems you are having.

---

### Post by rnerwein on 2010-02-09
hi
have a look in a dictonary for the german translation of "grub" 
to grub ---> sich plagen
and grub2 i think is the raise to the second power.

no i think it just will take some time that all the problems will be gone (  what's new on new software ? - new errors ! )
ciao

---

### Post by rickyrockrat on 2012-02-07
It's been two years and it's still the devil. What an awful, scripted bunch of spaghetti.  Nothing will change the design.  Grub was simple and it mostly just worked.  If you have to mess with Grub, chances are you already have trouble and now you get to dig through the pointy haired boss's tiny, chaotic brain and try to figure out how to get it to do what you want.

I'm still downgrading Grub2 to Grub, and we are talking Oneric!

---

