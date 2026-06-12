---
title: "wubi - kernel panic - not syncing VFS..."
date: 2009-11-06
forum: General Help
---

### Post by opensas on 2009-11-06
I installed ubuntu 9.10 using wubi

Verything worked fine, until I got the infamous:

[2.012847] kernel panic - not syncing - VFS: unable to mount root fs on unknown block (8,5)

I realized that the disk in which ubuntu was installed was almost full (just a 150 MB free)

so I made space (14,3 GB free out of 67 GB), checked it for error from windows, and defragmented it, but I still get the same error

any advice?

oh, one more thing, I've also notices that this directory

D:\ubuntu\disks\boot\grub

is empty... is that ok??? or maybe I lost grub's configuration...

I don't think that's the case, cause grub seems to be runing fine... who knows...

---

### Post by nepaliketa on 2009-11-11
I also have exactly same problem! anybody out there?

---

### Post by garikgarik on 2009-11-11
> **nepaliketa said:**
> I also have exactly same problem! anybody out there?
Same problem.

---

### Post by garikgarik on 2009-11-11
> **garikgarik said:**
> Same problem. :popcorn:

---

### Post by ALF102 on 2009-11-12
DOn't have much to say, I got this right after updates

---

### Post by r0tor on 2009-11-12
> **ALF102 said:**
> DOn't have much to say, I got this right after updates

same here... any fixes?

---

### Post by henz103 on 2009-11-12
i got it yesterday after updates :S can't boot now

---

### Post by Schobs on 2009-11-12
exactly the same... anyone knows whether its a bios problem?

---

### Post by r0tor on 2009-11-12
bumping this...

booted in windows and the grub folder is empty.  Ran chkdsk -r and it did not recover anything

---

### Post by fduplex on 2009-11-12
Same problem here, running 9.10 through Wubi. It just appeared today. I booted Ubuntu for the first time in about a week or so.

I got a popup saying updates were available so I installed them.

However, I also attempted to create a second virtual partition (loopback) in my /host/ubuntu/disks folder. After adding it to /etc/fstab and rebooting I assumed that was the cause of my problems. I have since deleted the new loopback file (and modified /etc/fstab accordingly using a ubuntu install cd in live mode), defragmented my host drive and still I get the same error saying the root fs cannot be mounted.

I did a little digging in /var/lib/dpkg/info to see what packages were changed during the latest update, I noticed udev was updated. Maybe this could have something to do with the problem?

I also noticed my initrd file has a modification time stamp around the time of the update. Maybe the initrd is somehow broken?

Oh, and yes my C:\ubuntu\disks\boot\grub folder is empty as well. I assumed this was normal, can anyone confirm this folder should not be empty? I have a /boot folder with grub's files in it on the root loopback partition (observed using the live cd), so I thought nothing of it.

It can't be a coincidence we're all having the same problem at the same time. I think the latest update must be responsible.

---

### Post by ALF102 on 2009-11-13
I dunno what the 'real' problem is but I do know they made a 'big' mistakey in the new updates. -_-
I've been searching for solutions but still find no luck on getting one. The problem is not somewhere in Grub2 that's for sure.

---

### Post by VesaKo on 2009-11-13
I had this same problem.

Could not find a way to fix this problem but following is what I did to rescue my files.

You will need the following:
[LIST=1]
[*]Ubuntu 9.10 desktop CD (burn one if you do not already have it)
[*]USB flash disk (or somewhere to put your files)
[/LIST]

First, boot Ubuntu from the desktop CD.

Next, follow the instructions on this page (See: "How can I access my Wubi install and repair my install if it won't boot?"):

[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?)

It tells you how to mount the disk image file within Ubuntu. Now you have access to your files in folder /vdisk.

Then just copy your files to the USB flash drive. (You now have access also to your Windows drive, so you could probably copy the files to some folder within Windows.)

[INDENT]I tried to run fsck on the disk image as instructed in the above page. fsck did not complain anything and told that the filesystem is clean. Then I tried to reboot to the original Ubuntu again but got kernel panic again. So, that did not solve the kernel panic problem.[/INDENT]

Anyway, now I have all my needed files backed up. Next thing I will do is reinstall wubi.

---

### Post by benjamin222 on 2009-11-13
Same here... no fixes? Seriously? Got the error after I ran updates. Didn't make any changes to ubuntu other than that.

---

### Post by VesaKo on 2009-11-13
> **benjamin222 said:**
> Same here... no fixes? Seriously? Got the error after I ran updates. Didn't make any changes to ubuntu other than that.

I mean, my system became unusable because I could not log in.

Only thing I could do was to rescue my files (as described above), then uninstall Ubuntu and reinstall it again.

---

### Post by kaelonlloyd on 2009-11-13
Why ain't these updates checked properly?, this is the second week an update has made ubuntu unbootable

---

### Post by ALF102 on 2009-11-14
Wait, correct me if I'm wrong...Did 'all' of you install Ubuntu using Wubi? or is there anyone that use a clean LiveCD install?

---

### Post by garvinrick4 on 2009-11-14
I have been running WUBI inside of Vista for quite some time. If there is anything
I can do for you all let me know. I am working fine and update on daily basis. Will help
in any way. WUBI should work. My Intel drivers all generic 64 bit.

---

### Post by ALF102 on 2009-11-14
Well, I dunno..Right now I've uninstalled WUBI and reinstall ubunntu using the LiveCD

---

### Post by r0tor on 2009-11-14
> **VesaKo said:**
> I had this same problem.

Could not find a way to fix this problem but following is what I did to rescue my files.

You will need the following:
[LIST=1]
[*]Ubuntu 9.10 desktop CD (burn one if you do not already have it)
[*]USB flash disk (or somewhere to put your files)
[/LIST]

First, boot Ubuntu from the desktop CD.

Next, follow the instructions on this page (See: "How can I access my Wubi install and repair my install if it won't boot?"):

[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?)

It tells you how to mount the disk image file within Ubuntu. Now you have access to your files in folder /vdisk.

Then just copy your files to the USB flash drive. (You now have access also to your Windows drive, so you could probably copy the files to some folder within Windows.)

[INDENT]I tried to run fsck on the disk image as instructed in the above page. fsck did not complain anything and told that the filesystem is clean. Then I tried to reboot to the original Ubuntu again but got kernel panic again. So, that did not solve the kernel panic problem.[/INDENT]

Anyway, now I have all my needed files backed up. Next thing I will do is reinstall wubi.

I'm in the middle of this... basically copy your entire HOME <user name> directory entirely and wipe ubuntu/wubi out, reinstall, and drop your <user name> folder back into your fresh install

---

### Post by BinaryFeast on 2009-11-14
Same boot problem and error message. Happened after the latest update. Can't reach a terminal. Though I booted from a Linux Mint live CD and managed to mount root.disk to save my files. In case anyone wonders the command to use is

```
sudo mount /Path/To/ubuntu/disks/root.disk /mnt -o loop

```

Is there any way to repair this without reinstalling?

---

### Post by figosound on 2009-11-17
Seriously guys, is anybody at least trying to solve this problem?? Does developers know that many people have lost their installations because of... what? Upgrades?
This is a huge problem, and folks at launchpad have failed to even mark the importance of this bug... Is this all the support that the community can provide?

And please, do not state that people should use "real installations" instead of wubi, for wubi is very popular and pubblicized to spread linux, and is included in --every-- ubuntu/kubuntu/xubuntu/minor flavor versions.
If wubi is going to be THAT instable, then please do not include it as a standard feature: am I right or what?

Sorry for my rant, but this is a major issue that seems to be highly ignored.

---

### Post by Dale61 on 2009-11-17
I was greeted with a kernel panic message this morning, but fortunately, I only had 9.10 installed for a couple of days, so I lost very little.  99% of my files were backed up anyway.

As I had installed via WUBI, I just deleted it.  As I have to retain VISTA on the new laptop (until I actually own it), I can't do a stand-alone install.

Lucky, eh!

I'll give it a couple of days before re-installing the WUBI way (and just think, I had finally sorted out my wireless problem!).

---

### Post by gramm on 2009-11-18
Hi all,
I currently have the same problem : wubi, xubuntu karmic koala, upgrade, fail. ](*,)
I posted a help message on the french forum but it doesn't get much attention. I guess all the linux gurus are too occupied compiling obscure wifi adapter drivers to help the mainstream users.
All that to say, keep posting, maybe somehow someone will finally help us :)
ps: I also have my /grub directory empty

---

### Post by khairat on 2009-11-18
same here..
problem is I am new to the whole Linux game.. and it seems that this has been lingering on for a while..

I originally decided to install ubuntu as I was told it is more stable than MS Windows!!:confused:

---

### Post by figosound on 2009-11-18
It **IS** more stable, the bug we are dealing with has to do with some wubi shenannighens, wich is not a component if the OS, but an "abstraction layer" of the hard drive, or something like that: what I am saying is that if wubi is the source of many problems, including this one, then WHY include it as an install option? This way the community has to deal with many more bugs and complains from new users which, after have an useless installation, will simply turn back to MS or Apple and never look back.

---

### Post by khairat on 2009-11-19
hmm.. I know that it IS from a pure "OS" and a technical prospective..
but when you look from a simple business user prospective.. it ain't working.. and it's the newest version!!

I lost about 5% of my new files in the process.. before installing I had a back up and that counts for 95% of my files.. 

I've been reading up on this forum as well as other.. this is a base problem or so it seems..  it has been around for a while and it is not being addressed.. and I would quote figosound "wubi is the source of many problems" hence most non-technical users (or users who do not have the luxury of time) would hit this wall and turn to other systems with out looking back..

Personally, I won't give up on it yet :)

---

### Post by figosound on 2009-11-19
Neither i won't (in fact the machine i had set up for family bizniz is running ubuntu 9.04 flawlessly and with my great pleasure), but it seems that this kind of problem is not worth for attention from developers...

---

### Post by gramm on 2009-11-20
Still no news ? This sucks. They shouldn't do this Wubi stuff unless it's safe. I've installed Ubuntu 3 times in one month : 
* The first time (duh)
* Then, it froze during the update from 9.4 to 9.10, ruinning the installation, so I installed the 9.10 directly
* Then, it worked two week and was ruinned once again. Since I was playing with a lot of packages I thought it was my fault
* Now it's ruinned again because of an official update.

Seriously ?  I really enjoy Ubuntu, but this Wubi stuff shouldn't exist if it brings so much trouble.

---

### Post by sudome on 2009-11-20
It seems that this is a tricky error 'cause the bug has been submitted to launchpad almost two weeks ago and they have'nt even decided the importance of the bug yet... 

Bah.. irritating!

---

### Post by figosound on 2009-11-20
Tell me: who is able to assign the importance level of a bug at Launchpad? Maybe if we harrass him/her we could have some attention...

---

### Post by LuxY2k on 2009-11-20
I think it's not a wubi problem.
I had this problem with Wubi on WinXP/Ubuntu9.10 last week. But after reading some forums I can recover my Ubuntu isntallation. All I have to do is to boot with LiveCD, mount the windowsXP partition, mount the root.img file and after it create a new initrd file in the boot dir. ("mkinitramfs -d /etc/initramfs-tools -o initrd_new.img",for example). After it, I have added this new initrd file to grub.conf in /boot/grub dir. And voilá, it can boot again.
But I think it's again not a good advertising for Linux. Who wants to deal with this **** after just a simple update? Damn. But I'm still in love with Ubuntu. :)

Lux/Y2k

---

### Post by sudome on 2009-11-21
Thats great! I need to try that.... too bad you have to lug around with a boot cd everytime you do a update.. or maybe one can make a script that builds a new initrd and adds it into grub everytime you do an update..hmm

---

### Post by Dale61 on 2009-11-21
I've just finished re-installing 9.10 via WUBI, and the kernel that crashed is now working fine.

---

### Post by ultimatevikrant on 2009-11-21
It is because of the package **initscripts_2.87dsf-4ubuntu12_i386** which is installed as an update. This changes the initrd scripts. So the solution is to revert back to the original **initrd** file in** /boo**t. Mount the root.disk inside the live CD or Virtualbox(for those those who have only the iso) and copy the following file to the /boot after taking the backup of original **initrd.img-2.6.31-14-generic** which is found in the **/boot** of the LiveCD or the VBox machine. This would solve the problem

---

### Post by nrthguy on 2009-11-21
Exactly same behaviour my end, with same circumstances as yous. 
Trying on these on now but dont know if it can be of any help in our case:
[http://ubuntuforums.org/showthread.php?t=1330725](http://ubuntuforums.org/showthread.php?t=1330725)
[http://ubuntuforums.org/showthread.php?t=1330725](http://ubuntuforums.org/showthread.php?t=1330725)

especially 
[http://ubuntuforums.org/showthread.php?t=1317397](http://ubuntuforums.org/showthread.php?t=1317397)

---

### Post by rockfx01 on 2009-11-21
> **ultimatevikrant said:**
> It is because of the package **initscripts_2.87dsf-4ubuntu12_i386** which is installed as an update. This changes the initrd scripts. So the solution is to revert back to the original **initrd** file in** /boo**t. Mount the root.disk inside the live CD or Virtualbox(for those those who have only the iso) and copy the following file to the /boot after taking the backup of original **initrd.img-2.6.31-14-generic** which is found in the **/boot** of the LiveCD or the VBox machine. This would solve the problem

ultimatevikrant, thanks for the possible solution but I see no initrd.img-2.6.31-14-generic file when i boot to my live 'cd' (actually a live USB drive image).  I can mount the wubi root.disk and see the initrd.img in the /boot folder there, but I have nothing to replace it with ](*,)  Is there a backup on the root.disk somewhere?

Alternatively, can someone post a valid initrd.img-2.6.31-14-generic file to download?  I would love to actually get my system up and running again.

So much for getting any work done today...  I did an update yesterday and my system worked find after suspend/resume, but after a full shutdown last night, well, you know the story.

---

### Post by noisyscanner on 2009-11-21
No fix then :(
Just booted up about 20 mins ago and had the same error as you guys.
So is the only method of fixing this re installing then.
Yes i use wubi.
Can I back up my stuff from ubuntu through xp though?
Anyway I still have the installer and I don't think I had an awful lot on there!
Bradley

---

### Post by curpin on 2009-11-21
OK, guys.
I am a newbie to Linux, but I had similar situation and followed your thread. I have started [my own]("http://ubuntuforums.org/showthread.php?p=8361248#post8361248") as well.
Anyway, let me please thank Lux/Y2k for his contribution because that have saved my installation.
Here is a bit of what I did to sort this problem:
I booted from the live CD and then did the following:
sudo mkdir /win
sudo mount /dev/sda1 /win

sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
(this way disk.root can be browsed via /vdisk)

Then I had to switch the root 
sudo mount -o bind /proc /vdisk/proc (not sure if this is necessary)
sudo mount -o bind /dev /vdisk/dev (not sure if this is necessary too)
sudo chroot /vdisk /bin/bash

now the root points to the damaged system.
mkinitramfs -d /etc/initramfs-tools -o initrd_new.img  (this will create a file called initrd_new.img
depending where you have created this file, move it to /boot (of your damaged installation)
and then change this line in /boot/grub/grub.cfg
from:
    initrd /boot/initrd.img-2.6.31-14-generic
to:
    initrd /boot/initrd_new.img

And then reboot.  Surprisingly this worked and saved me reinstalling the whole system.
With all respect to Ubuntu, a failed upgrade/installation/update should not break an operating system known for it's stability.  So I hope this will be taken more seriously in the future.

---

### Post by sudome on 2009-11-21
I can confirm that the above method works well. Thanks Lux/Y2k!

---

### Post by drxyzzy on 2009-11-22
Lux/Y2k fix worked initially for me using Vista SP2 on Lenovo Y710 - thanks! But second or third time update ran and I tried to recover, boot ends at grub sh. I tried making new initrd image as well as several saved versions that had worked before but no joy.

I'm out of time on this one. Workaround is to switch from WUBI to [VMware Player]("http://www.vmware.com/products/player/") 3.0 which is free and also resolves ACPI problem with Ubuntu on Lenovo (doesn't see CD/DVD player unless ACPI is turned off).

---

### Post by drxyzzy on 2009-11-22
noisyscanner - one way to backup Wubi Ubuntu image is to install [Cygwin]("http://cygwin.com/") on Windows (I used the basic package from the 1.7 beta - you don't need all of cygwin) and use gzip to keep compressed backups. If images are on D:, do this sort of thing from cygwin bash shell:

```
gzip < /cygdrive/d/Ubuntu/disks/root.disk > /cygdrive/d/Save/2009-11-21-ubu.gz
```

Restore with gunzip.

---

### Post by ninja togo on 2009-11-22
I've got one part of this mystery solved now after multiple re-installs. 

Wubi's install files are screwed up by Windows automatically if the user boots into Windows again after Wubi is installed.

My advice is to stay away from Windows until you are ready to go back for good using WINE for any Windows apps you NEED/ Do some investigating on why Windows modifies the files in the first place and stop it, returning a solution better than mine for everyone else.

Again this is the third time I am receiving the error and having to re-install but I was able to mount the, "Root.DISK" file in the, "ubuntu/disks/" folder.

---

### Post by rockfx01 on 2009-11-22
> **ninja togo said:**
> Wubi's install files are screwed up by Windows automatically if the user boots into Windows again after Wubi is installed.

How did you come to this conclusion?  If that were the case then Wubi in and of itself would be absolutely pointless.  I was using Wubi for 6 months with Ubuntu 9.04 with no problems dual-booting Windows Vista 64-bit and Ubuntu 9.04 64-bit (Wubi).

This problem didn't appear until a couple days ago after having recently done an uninstall of 9.04 and clean new install of 9.10 via Wubi.  It was working fine dual booting for a week or two until I applied some updates Friday and then afterwards did a full shut down. Sure, I booted into Windows between when I shut down and when I later tried to boot Ubuntu again (which failed miserably), but that doesn't mean Windows did anything to change the Wubi Ubuntu image.  The only recent changes to my machine were the Ubuntu updates I installed. I boot between the two very regularly so I'd like to see something which actually supports the theory that Windows is in any way related.  While it might feel nice to place the blame squarely on MS for completely hosing everyone's Wubi installation, I simply see absolutely zero facts supporting that theory.

IMO this definitely looks like an Ubuntu update, not Windows has caused this problem, as nearly everyone who stumbled upon the issue had it occur immediately or almost immediately after installing updates.  If that's not hard proof of it being an update issue then I don't know what is.

P.S. creating a new initrd image has not worked for me either, I either continue to get the same error message on bootup or I get the grub sh screen as you mentioned.

---

### Post by FXEF on 2009-11-22
@rockfx01

If this update requires a reboot and is allowed to reboot into Windows instead of Ubuntu, it could be possible that files are corrupted. Then the next time Ubuntu is booted you receive the kernel panic. I have not tested a Wubi install since 8.04. I would suggest to always rebooted to Ubuntu... never Windows, when update ask for a reboot.  

Let me make it clear, I am not saying this is the problem, just saying it could have adverse effects on some updates.

---

### Post by rockfx01 on 2009-11-22
Actually, I don't believe the update required a reboot.  I had done the update in Friday morning, it didn't give a need to reboot message and I used it for the rest of the day suspending/resuming it at least once or twice after the update.  It wasn't until after a full shutdown and having to restart through grub that the problem surfaced.

In any case, my system is still hosed.  I guess it's time to backup and reinstall.  Hopefully restoring my encrypted home directory won't be too painful.

---

### Post by curpin on 2009-11-23
To: [rockfx01]("http://ubuntuforums.org/member.php?u=510232")
I got the same problems as yours after doing the steps on the [previous page of this forum]("http://ubuntuforums.org/showthread.php?t=1317397&page=4"), but then I ended up with the grub prompt.
This, still, is for sure due to the updates that were done on the system.
So I did again the same steps, and then went to the etc/apt/sources.list and 'commented' all the non validated and tested sources.
I then had to go back to /boot/grub/grub.cfg and make sure that initrd points to the initrd_new.img.
Rebooting worked ok.
So far, it works.  I am not keen to re-install, because this is my third install for the same panic issue.
I will keep you updated if I get the issue again.

---

### Post by ninja togo on 2009-11-23
> **rockfx01 said:**
> How did you come to this conclusion?  If that were the case then Wubi in and of itself would be absolutely pointless.  I was using Wubi for 6 months with Ubuntu 9.04 with no problems dual-booting Windows Vista 64-bit and Ubuntu 9.04 64-bit (Wubi).

This problem didn't appear until a couple days ago after having recently done an uninstall of 9.04 and clean new install of 9.10 via Wubi.  It was working fine dual booting for a week or two until I applied some updates Friday and then afterwards did a full shut down. Sure, I booted into Windows between when I shut down and when I later tried to boot Ubuntu again (which failed miserably), but that doesn't mean Windows did anything to change the Wubi Ubuntu image.  The only recent changes to my machine were the Ubuntu updates I installed. I boot between the two very regularly so I'd like to see something which actually supports the theory that Windows is in any way related.  While it might feel nice to place the blame squarely on MS for completely hosing everyone's Wubi installation, I simply see absolutely zero facts supporting that theory.

IMO this definitely looks like an Ubuntu update, not Windows has caused this problem, as nearly everyone who stumbled upon the issue had it occur immediately or almost immediately after installing updates.  If that's not hard proof of it being an update issue then I don't know what is.

P.S. creating a new initrd image has not worked for me either, I either continue to get the same error message on bootup or I get the grub sh screen as you mentioned.

Well I just thought this was the case as booting to Windows caused kernel panic for me THREE times:cry: also I read on another forum that Windows Vista will sometimes move foreign files to a, "found.000x" folder x being a number for the nth time it has found foreign files. Anyway I am glad to see that there are others experiencing the problem, responding and showing solutions. Now this is what's meant by Linux Community. :D

---

### Post by gramm on 2009-11-24
I'm 100% sure that I didn't boot to Windows since I was working on Ubuntu when I did the update. I rebooted because I wanted to have this "OS-just-started" fresh sensation :) . I was standing behind the computer so, I don't think Windows is to blame.
As for the solution gave earlier, thanks :) , but since I have to burn a Ubuntu CD, I'll take the opportunity to create a Linux partition and install it "for real".

---

### Post by figosound on 2009-11-24
> **curpin said:**
> OK, guys.
I am a newbie to Linux, but I had similar situation and followed your thread. I have started [my own]("http://ubuntuforums.org/showthread.php?p=8361248#post8361248") as well.
Anyway, let me please thank Lux/Y2k for his contribution because that have saved my installation.
Here is a bit of what I did to sort this problem:
I booted from the live CD and then did the following:
sudo mkdir /win
sudo mount /dev/sda1 /win

sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
(this way disk.root can be browsed via /vdisk)

Then I had to switch the root 
sudo mount -o bind /proc /vdisk/proc (not sure if this is necessary)
sudo mount -o bind /dev /vdisk/dev (not sure if this is necessary too)
sudo chroot /vdisk /bin/bash

now the root points to the damaged system.
mkinitramfs -d /etc/initramfs-tools -o initrd_new.img  (this will create a file called initrd_new.img
depending where you have created this file, move it to /boot (of your damaged installation)
and then change this line in /boot/grub/grub.cfg
from:
    initrd /boot/initrd.img-2.6.31-14-generic
to:
    initrd /boot/initrd_new.img

And then reboot.  Surprisingly this worked and saved me reinstalling the whole system.
With all respect to Ubuntu, a failed upgrade/installation/update should not break an operating system known for it's stability.  So I hope this will be taken more seriously in the future.

This leads me to a grub:sh terminal... Any gotcha?
(edit: my english sucks)

---

### Post by curpin on 2009-11-24
> **figosound said:**
> This leads me to a grub:sh terminal... Any gotcha?
(edit: my english sucks)

Have you booted from the Live CD and did all the changes?
If you have done so and that lead you to a grub prompt then most likely your initrd file is corrupt and wasn't properly created.

From my humble experience, the first time I did the steps, it worked like magic, until I got the Software updates, that lead me to the grub prompt later when I rebooted the next day.
So I disabled the software updates from untrusted/untested sources.  And recreated the initrd file again and that worked for me.  This was yesterday.

---

### Post by figosound on 2009-11-24
I have done exactly what your post says (btw, thank you very much for the effort!) without getting any warning or error, beside the fact that initialli i did not have permissions to modify grub.conf in /boot/grub/ of the corrupted installation (vdisk). I do not have any untrusted/untested software sources (repositories?): what can i do now?

---

### Post by curpin on 2009-11-24
> **figosound said:**
> I have done exactly what your post says (btw, thank you very much for the effort!) without getting any warning or error, beside the fact that initialli i did not have permissions to modify grub.conf in /boot/grub/ of the corrupted installation (vdisk). I do not have any untrusted/untested software sources (repositories?): what can i do now?

When you boot from the Live CD you should have permission to modify it just remember to put sudo.  You can use nano this way:
sudo nano /boot/grub/grub.cfg

---

### Post by figosound on 2009-11-24
Sorry, what i tried to say is that *initially* I did not have permissions, but i changed them with "properties" dialog... Since you did not mentioned permission issues, i thought it might been useful to tell you :-)

EDIT: Off course i used sudo ;-)

---

### Post by kimharding on 2009-11-24
> **curpin said:**
> OK, guys.
I am a newbie to Linux, but I had similar situation and followed your thread. I have started [my own]("http://ubuntuforums.org/showthread.php?p=8361248#post8361248") as well.
Anyway, let me please thank Lux/Y2k for his contribution because that have saved my installation.
Here is a bit of what I did to sort this problem:
I booted from the live CD and then did the following:
sudo mkdir /win
sudo mount /dev/sda1 /win

sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
(this way disk.root can be browsed via /vdisk)

Then I had to switch the root 
sudo mount -o bind /proc /vdisk/proc (not sure if this is necessary)
sudo mount -o bind /dev /vdisk/dev (not sure if this is necessary too)
sudo chroot /vdisk /bin/bash

now the root points to the damaged system.
mkinitramfs -d /etc/initramfs-tools -o initrd_new.img  (this will create a file called initrd_new.img
depending where you have created this file, move it to /boot (of your damaged installation)
and then change this line in /boot/grub/grub.cfg
from:
    initrd /boot/initrd.img-2.6.31-14-generic
to:
    initrd /boot/initrd_new.img

And then reboot.  Surprisingly this worked and saved me reinstalling the whole system.
With all respect to Ubuntu, a failed upgrade/installation/update should not break an operating system known for it's stability.  So I hope this will be taken more seriously in the future.

I got as far as "and then change this line in /boot/grub/grub.cfg" then found that grub.cfg was missing, not sure what to do next... ](*,)

---

### Post by figosound on 2009-11-25
You have to search for ```
/vdisk/boot/grub/grub.conf
```, as it's the only grub.conf that matters (wubi installation is empty, and /boot/grub/ of the livecd does not matter).

---

### Post by kimharding on 2009-11-25
OK so I have had another go, I find I am getting lost at

> 
now the root points to the damaged system.
mkinitramfs -d /etc/initramfs-tools -o initrd_new.img  (this will create a file called initrd_new.img
depending where you have created this file, move it to /boot (of your damaged installation)
and then change this line in /boot/grub/grub.cfg
So I am going to try a walk through and write up in this post as I do it.

By using the ls command I can see that the initrd_new.img has been created,

```

root@ubuntu:/# ls

```Which shows

```

bin    etc       initrd.img.old  media  root       sys    vmlinuz
boot   home       **initrd_new.img**  mnt      sbin       tmp    vmlinuz.old
cdrom  host       lib           opt      selinux  usr
dev    initrd.img  lost+found       proc   srv       var

```so I now know that it is there, next  have now got to get it into  /boot, so I use

```

root@ubuntu:/# cp initrd_new.img boot

```then to see that it is there

```

root@ubuntu:/# cd boot
root@ubuntu:/boot# ls

abi-2.6.31-14-generic          memtest86+.bin
abi-2.6.31-15-generic          System.map-2.6.31-14-generic
config-2.6.31-14-generic      System.map-2.6.31-15-generic
config-2.6.31-15-generic      vmcoreinfo-2.6.31-14-generic
grub                  vmcoreinfo-2.6.31-15-generic
initrd.img-2.6.31-14-generic  vmlinuz-2.6.31-14-generic
initrd.img-2.6.31-15-generic  vmlinuz-2.6.31-15-generic
initrd_new.img

root@ubuntu:/boot# cd grub
root@ubuntu:/boot/grub# ls
device.map  **grub.cfg**  grubenv  unicode.pf2

```so I have now found the grub.cfgwhich I need to edit it

```

root@ubuntu:/boot/grub# nano grub.cfg

```this gets me into the grub.cfg file
```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        insmod ntfs
        set root=(hd0,4)
        search --no-floppy --fs-uuid --set d262902d62901875
        loopback loop0 /ubuntu/disks/root.disk
        set root=(loop0)
        linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda4 loop=/ubuntu/disks/root.disk ro single
       ** initrd /boot/initrd.img-2.6.31-14-generic**
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
        insmod ntfs
        set root=(hd0,2)
        search --no-floppy --fs-uuid --set 765640d056409333
        chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```and at this point I can change the line from:
    initrd /boot/initrd.img-2.6.31-14-generic
to:
    initrd /boot/initrd_new.img

That done I will now reboot and tell you what happens...

Well it rebooted again and started with a fresh installation, none of my old data there! Can anyone tell me where I went wrong???

---

### Post by figosound on 2009-11-25
Honestly, I cannot help you any further... If it helps, my system is still hosed :-(

---

### Post by Canaryguy on 2009-11-25
Hello,

I had the same problem with the installation of Ubuntu with wubi. Once I installed the updates I saw grub and the system couldn't lunch the graphical interface. But I did something that helped me.

1º Install Ubuntu inside Windows with wubi

2º Install all the updates for Ubuntu when they appear or do it yourself manually

3º After installing the updates when the system asks you to reboot don't do it. Go to the Terminal (Applications/Accessories/Terminal)

4º In the Terminal write: sudo update-grub2 (press enter and write your password if required)

5º Now restart

And that's all

That worked for me.

Good luck.

---

### Post by figosound on 2009-11-25
I give up, I'm going to uninstall my wubi installation, and install ubuntu on a dedicated partition.

Here I make a statement: *I Will Never Ever Use Wubi Again, And I Will Never Ever Tell To Someone To Use Wubi "because it's simpler"*.

Mark my words :lolflag:

---

### Post by curpin on 2009-11-25
> **figosound said:**
> I give up, I'm going to uninstall my wubi installation, and install ubuntu on a dedicated partition.

Here I make a statement: *I Will Never Ever Use Wubi Again, And I Will Never Ever Tell To Someone To Use Wubi "because it's simpler"*.

Mark my words :lolflag:
Wait.
I think I found something today that might help you.
Although my system was working today, I though to try and run: sudo update-grub2
That was a mistake.  Because then my system did not reboot and I got the grub prompt.
So what I did, I checked the grub.cfg file and I noticed that it is point to the new Linux version instead of the I had before.  
***linux /boot/vmlinuz-2.6.31-15-generic***...

What I did is that I reverted the old copy 
which had 
**linux /boot/vmlinuz-2.6.31-14-generic...**

And rebooted and went back to normal.
So most likely your newest linux version was not acceptable, hence grub doesn't know what to do and it doesn't even reach the point of running:
**initrd /boot/initrd.img-2.6.31-14-generic**
in order to the polite kernel panic message.
Hope this helps

---

### Post by drussellkraft on 2009-11-25
> **Canaryguy said:**
> Hello,

I had the same problem with the installation of Ubuntu with wubi. Once I installed the updates I saw grub and the system couldn't lunch the graphical interface. But I did something that helped me.

1º Install Ubuntu inside Windows with wubi

2º Install all the updates for Ubuntu when they appear or do it yourself manually

3º After installing the updates when the system asks you to reboot don't do it. Go to the Terminal (Applications/Accessories/Terminal)

4º In the Terminal write: sudo update-grub2 (press enter and write your password if required)

5º Now restart

And that's all

That worked for me.

Good luck.

Any advice for those of us who have already restarted without doing this?  Any way to run that update from a live-CD boot?  Thanks!

---

### Post by figosound on 2009-11-25
> **curpin said:**
> Wait.
I think I found something today that might help you.
Although my system was working today, I though to try and run: sudo update-grub2
That was a mistake.  Because then my system did not reboot and I got the grub prompt.
So what I did, I checked the grub.cfg file and I noticed that it is point to the new Linux version instead of the I had before.  
***linux /boot/vmlinuz-2.6.31-15-generic***...

What I did is that I reverted the old copy 
which had 
**linux /boot/vmlinuz-2.6.31-14-generic...**

And rebooted and went back to normal.
So most likely your newest linux version was not acceptable, hence grub doesn't know what to do and it doesn't even reach the point of running:
**initrd /boot/initrd.img-2.6.31-14-generic**
in order to the polite kernel panic message.
Hope this helps

Too late :mrgreen: I already wiped out everything... BTW, could you provide me a good install guide? It's because i have to install on a dedicated partition, which is on a secondary drive, but lacks a swap partition, so i have to do it by myself, and do not want to frak up anything :-)

---

### Post by curpin on 2009-11-26
I wish I can; my only experience is installing it on the same Hard Drive where Windows resides.

---

### Post by Ethyrdude on 2009-11-26
Just as a matter of interest, and probably not of any help but I was able to boot up using my previous kernel, but... my login has become corrupt so now I will have to create a new user and try and repair the damage once I'm in, the problem is, I don't have root access, so I can't create a new user, yes I will get in somehow, have done it before when running ubuntu exclusively but not sure if I'm crazy about wubi... Just as a thought, when u have a fixed partition, things tend to stay static but now you're in a folder that changes sizes, oh boy....
:popcorn:

---

### Post by Ethyrdude on 2009-11-27
Ok this is definitely not going to be of any help but may close the situation as being an issue that will be resolved in a day or two, my only recourse of action was to pitch windows out, as I can survive without it and do a nice clean reinstall of Ubuntu and I installed 9.04, 9.10 can wait for a month or two more till things are resolved.

---

### Post by obroyz on 2009-12-04
Hi everyone,

I'm absolutely new to Linux, leave aside Ubuntu. Having installed Ubuntu Karmic Koala just a few days ago, using Wubi, I have been extremely impressed with this O/S.

Getting to the point, I ran into this problem yesterday and I really couldn't understand a word everyone was saying about fixing this issue. My kernel had been updated to 2.6.31-15 and last morning, my machine wouldn't boot.

I noticed that I was able to boot into 2.6.31-14, so I worked on it for a while, trying to find a 'simple' solution before I went on learning all the technical stuff.

Anyhow, the fix:

1) Go to System > Administration > Synaptic Package Manager
2) Put in a search for linux-image
3) Locate the package "linux-image-2.6.31-15-generic"
4) Select the check-box next to this package and choose "Mark for Reinstallation"
5) Apply this changes
6) Reboot your machine

(For me) problem solved.

I hope it works for all of you as well.

Thanks,

J.

---

### Post by usagetta on 2009-12-05
:popcorn::popcorn:> **obroyz said:**
> Hi everyone,

I'm absolutely new to Linux, leave aside Ubuntu. Having installed Ubuntu Karmic Koala just a few days ago, using Wubi, I have been extremely impressed with this O/S.

Getting to the point, I ran into this problem yesterday and I really couldn't understand a word everyone was saying about fixing this issue. My kernel had been updated to 2.6.31-15 and last morning, my machine wouldn't boot.

I noticed that I was able to boot into 2.6.31-14, so I worked on it for a while, trying to find a 'simple' solution before I went on learning all the technical stuff.

Anyhow, the fix:

1) Go to System > Administration > Synaptic Package Manager
2) Put in a search for linux-image
3) Locate the package "linux-image-2.6.31-15-generic"
4) Select the check-box next to this package and choose "Mark for Reinstallation"
5) Apply this changes
6) Reboot your machine

(For me) problem solved.

I hope it works for all of you as well.

Thanks,

J.

thx very much!!!

---

### Post by aiiee on 2009-12-12
what an f'n mess.  Windows 3.1 worked  better than this bs :popcorn:

---

### Post by aiiee on 2009-12-12
> **ultimatevikrant said:**
> It is because of the package **initscripts_2.87dsf-4ubuntu12_i386** which is installed as an update. This changes the initrd scripts. So the solution is to revert back to the original **initrd** file in** /boo**t. Mount the root.disk inside the live CD or Virtualbox(for those those who have only the iso) and copy the following file to the /boot after taking the backup of original **initrd.img-2.6.31-14-generic** which is found in the **/boot** of the LiveCD or the VBox machine. This would solve the problem

Can this still now work what with the current kernel being 2.6.31-16?  The LIveCD has 2.6.31-14 and the latest kernel is 2.6.31-16.  How can I use the 14 version of initrd with the 16 kernel?

---

### Post by Dale61 on 2009-12-12
> **aiiee said:**
> **Can this still now work what with the current kernel being 2.6.31-16?**  The LIveCD has 2.6.31-14 and the latest kernel is 2.6.31-16.  How can I use the 14 version of initrd with the 16 kernel?

I had an update come thru this morning with the -17 kernel.

---

### Post by hhh81 on 2009-12-13
> **curpin said:**
> OK, guys.
I am a newbie to Linux, but I had similar situation and followed your thread. I have started [my own]("http://ubuntuforums.org/showthread.php?p=8361248#post8361248") as well.
Anyway, let me please thank Lux/Y2k for his contribution because that have saved my installation.
Here is a bit of what I did to sort this problem:
I booted from the live CD and then did the following:
sudo mkdir /win
sudo mount /dev/sda1 /win

sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
(this way disk.root can be browsed via /vdisk)

Then I had to switch the root 
sudo mount -o bind /proc /vdisk/proc (not sure if this is necessary)
sudo mount -o bind /dev /vdisk/dev (not sure if this is necessary too)
sudo chroot /vdisk /bin/bash

now the root points to the damaged system.
mkinitramfs -d /etc/initramfs-tools -o initrd_new.img  (this will create a file called initrd_new.img
depending where you have created this file, move it to /boot (of your damaged installation)
and then change this line in /boot/grub/grub.cfg
from:
    initrd /boot/initrd.img-2.6.31-14-generic
to:
    initrd /boot/initrd_new.img

And then reboot.  Surprisingly this worked and saved me reinstal
And then reboot.  Surprisingly this worked and saved me reinstalling the whole system.
With all respect to Ubuntu, a failed upgrade/installation/update should not break an operating system known for it's stability.  So I hope this will be taken more seriously in the future.

I have used those commands in normal kubuntu session and at restart there was command line (root@ubuntu before prompt)  and i didn't know how to back to normal (graphical session) so i formatted linux.> 
sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
(this way disk.root can be browsed via /vdisk)

Then I had to switch the root 
sudo mount -o bind /proc /vdisk/proc (not sure if this is necessary)
sudo mount -o bind /dev /vdisk/dev (not sure if this is necessary too)
sudo chroot /vdisk /bin/bash :(

---

### Post by hhh81 on 2009-12-13
what is the function of those commands? how could i recovery previous state of kubuntu ?
using what commands and how.......
this to prevent bad future situations such the above descripted.

---

### Post by elbandito on 2009-12-13
I have the exact same problem and posted it here a couple of days ago. Here's the post and the suggestions I was given:


[Karmic Koala Won't Boot!]("http://ubuntuforums.org/showthread.php?t=1352776")

---

### Post by elbandito on 2009-12-13
Hey folks... do you think I can pull off this fix from within VMware? I don't have a CD burner in my comp. :S

---

### Post by R2D2! on 2009-12-19
> **ultimatevikrant said:**
> It is because of the package **initscripts_2.87dsf-4ubuntu12_i386** which is installed as an update. This changes the initrd scripts. So the solution is to revert back to the original **initrd** file in** /boo**t. Mount the root.disk inside the live CD or Virtualbox(for those those who have only the iso) and copy the following file to the /boot after taking the backup of original **initrd.img-2.6.31-14-generic** which is found in the **/boot** of the LiveCD or the VBox machine. This would solve the problem

I have a clean install of Ubuntu 9.10 under Wubi. As I understand, as far as I don't uptade the **initscripts_2.87dsf-4ubuntu12_i386** package, I don't have to worry, right?

—Ilhu&#305;temoc

---

### Post by R2D2! on 2009-12-19
OK, now everything is f*cked up. Now I get a grub command line, and after giving the appropiate commands, it boots to a kernel panic...

P.S. Hey, who covered my word???:-x:-x:-x

---

### Post by hhh81 on 2009-12-23
[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169?comments=all](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169?comments=all)

look here the bug seems now finally resolved/fixed .:popcorn:

and similar bug here
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104)

---

### Post by asdfchanta on 2010-01-09
Is it officially fixed or has a temporal solution? Coz i want to install ubuntu using wubi, and update it.

---

### Post by hhh81 on 2010-01-09
Yes it's the fix/patch that will be integrated in wubi.exe, if u don't want to wait until new modified wubi.exe you can use the current wubi to install ubuntu and then manually replace the old wrong c:\wubildr file with new one that can be obtained from [https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90)
as written in [https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169?comments=all](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169?comments=all)  comment number #210



"For a patch/workaround:

A) get the wubildr in [https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90) and copy it over C:\wubildr
B) ensure that when you boot there is no command "insmod ntfs". Press "e" at the grub boot menu to edit the relevant entry and remove "insmod ntfs" before proceeding

New ubuntu/wubi installations do not contain the patch yet. The patch will only be applied once there is a clear confirmation (from you) that it actually solves the problem. Hence your feedback is appreciated."

---

### Post by macsdev on 2010-01-14
^^ It did work. Thanks a lot :D

---

### Post by nhbob on 2010-01-20
_[SIZE=3]**I need "DUMMY" like instructions to repair this error**.[/SIZE]_  [SIZE=4]I like many others just used the regular automatic upgrade path and got the kernel panic. I can execute the older version of Ubuntu from the start menu but I do not know how to get rid of the damaged versions or how to input a fix.  All instructions in the thread seem to assume a general knowledge of Linux and terminal use that I just do not have.  I assure you all that  there are many, many, others out here that try out Ubuntu and Linux and then are forced to retreat and then probably surrender in the face of these challenges.

The fact that Ubuntu and Wubi provide packaged support and upgrade paths for Linux certainly should provide the mass population of computer users a path for that will allow them to take advantage of the many benefits of Linux but it is my opinion that Linux will remain a tool for a very small (comparatively) number of specialist users (something I suspect a number of people secretly like) unless more is done to attract general computer users like myself. Releasing upgrades that result in a mess like this is bad enough, but not providing a rapid, concise set of solutions is worse.

If there is anyone out there from Ubuntu, WUBI and others who seem to at least philosophically agree with my position, please discuss this at the highest level and provide a real "For Dummis" solution to this and future problems.[/SIZE]

---

### Post by hhh81 on 2010-01-21
I reply here to your pm: You must try to replace the file **wubildr**  (without extension) located in C:\    
(you can try from windows)
with the new one that can be obtained from this link [https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90)
this should works

---

### Post by nhbob on 2010-01-25
Thanks for this response.

I have multiple copies of wubildr (79KB) and wubldr.mbr(8KB) and a single copy of wubild.cfg (2KB).  

I take it I somehow delete some and then add the new file by saving it somewhere - where is that?

As I said I need "Dummy" help. I am nor linux proficient.

---

### Post by meierfra. on 2010-01-27
> I take it I somehow delete some 
You don't have to deleted it. It will be overwritten by the new file.

> and then add the new file by saving it somewhere - where is that?

Directly on "C:\". Go to "My Computer" (or "Computer") and then double click the icon for the "C:" drive.

---

### Post by nhbob on 2010-01-28
Thank You.  I will try this method.

---

### Post by Todge on 2010-01-29
Worked for me! Thanks x

---

### Post by asdfchanta on 2010-02-03
So... is the new wubi out? I cant find the different versions or get any information from the wubi site.

Is the new wubi without the nasty bug when updating?

---

### Post by sistercreepy on 2010-03-14
Same here....I get:

4.103654 kernel panic - not syncing:  VFS: unable to mount root fs on unknown block (8,3)

---

### Post by sistercreepy on 2010-03-14
Thank You hhh81 this worked!!

---

### Post by matt! on 2010-03-28
This also worked for me - thank you!

---

### Post by Julian David Pitt on 2010-03-29
Just replaced my wubildr and I still get the kernel panic, mind you I found the wubildr file in my C:\ubuntu\winboot directory, is that correct?

---

### Post by sprocketrx on 2010-04-17
the new wubildr file worked for me, thanks for the easy fix

---

### Post by BinaryBrother on 2010-05-10
> **hhh81 said:**
> I reply here to your pm: You must try to replace the file **wubildr**  (without extension) located in C:\    
(you can try from windows)
with the new one that can be obtained from this link [https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90)
this should works

This did not work for me directly... However, booting into recovery mode worked and from there I ran dpkg repair and after about 45 mins of fixing packages, it worked. Thanks! :)

---

### Post by Dale61 on 2010-05-10
I had to revert to my SIL's Windoze machine (shudders down spine) to find a fix when I first encountered this problem.  Then, what I did was to download the new wubidr file to a flash drive, then go back to my pc, and once I got it running as per normal, I swapped the old wubidr file with the new, and haven't had a problem since.

However, I have now upgraded to 10.04, and haven't had any semblance of a similar problem, so I'm thinking (hoping) it is just a 9.10 problem, and not an on-going issue.

---

### Post by mikerip on 2010-05-21
Sorry, it does happen with 10.04. It seems to depend on the chipset. I have been unable to get 10.04 livecd or a finished install to boot on one system I have with a Sis chipset. I can boot the ALT cd and install from that but grub is most unhappy when trying to boot the finished install. The interesting thing is that if I move the hard drive to another system with an Intel chipset, it boots just fine. 

I'm guessing, but I think it has to do with the kernel masking the IDE drives as /dev/sdX instead of /dev/hdX  

manually booting into grub, it says that (hd0,0) does not exist but it can see (hd0,1) which I consider very odd. I don't think it is specifically the 2.6 kernel as I have Centos5.4 running just fine on the same box (different hard drive). Something is very broken in the way ubuntu is handling the disk structure in their kernels (in my humble opinion).

Waiting for a fix.....

---

### Post by jstn808stb8 on 2010-05-21
I had this problem 9.10 but since i did a clean install with 10.04  (WUBI) i have never had a problem

---

### Post by RAHUL KUMAR on 2011-02-17
> **opensas said:**
> I installed ubuntu 10.10 using wubi

Verything worked fine, until I got the infamous:

[2.012847] kernel panic - not syncing - VFS: unable to mount root fs on unknown block (0,0)

I realized that the disk in which ubuntu was installed was almost full (just a 150 MB free)

so I made space (5 GB free out of 38 GB), checked it for error from windows, and defragmented it, but I still get the same error

any advice?

oh, one more thing, I've also notices that this directory

D:\ubuntu\disks\boot\grub

is empty... is that ok??? or maybe I lost grub's configuration...

I don't think that's the case, cause grub seems to be runing fine... who knows...
plz rply..........!!!!!!!
I m a new user.........

---

