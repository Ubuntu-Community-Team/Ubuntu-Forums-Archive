---
title: "Preventing Viral Spread To Windows Drive"
date: 2012-04-04
forum: General Help
---

### Post by carmenin87 on 2012-04-04
I'm using a custom Ubuntu Live CD that I made.  I've done the security updates as well.  When I boot my XP machine using the Live CD, using places=>computer, I can see my XP hard drive.

Is there a risk that a virus or other unwanted files (eg worms/trojans) could be saved to the XP drive?

Also, is there a way to prevent the XP drive from being seen by Ubuntu?

---

### Post by wildmanne39 on 2012-04-04
Hi, no files are stored on the hard drive using the livecd they are stored in ram. You do not need to worry.
Thanks

---

### Post by carmenin87 on 2012-04-04
> **wildmanne39 said:**
> Hi, no files are stored on the hard drive using the livecd they are stored in ram. You do not need to worry.
Thanks

I do understand that the livecd only stores files in RAM, but using Places, I can see my internal XP hard drive that is in the computer.

Is there any way to ensure that no files get saved on the XP drive, either Ubuntu files or more importantly something that gets inadvertently downloaded from the net?

Thanks

---

### Post by asuastrophysics on 2012-04-04
> **carmenin87 said:**
> 
Is there a risk that a virus or other unwanted files (eg worms/trojans) could be saved to the XP drive?

This is extremely, extremely unlikely. The possibility of this happening to you is like 0.000001*10^.01 . You are statistically more likely to die in a car crash than spread a virus in this manner using Ubuntu.

Viruses and trojans could possibly be saved to your ubuntu live partition through some backdoor security loophole in firefox, but even if any malware was downloaded, it would not be able to execute it's code, because most malware are executable files and ubuntu by itself cannot run these. Therefore, any malware downloaded would stay put right where it was downloaded to, and it would not be able to make copies of itself.

> **carmenin87 said:**
> 
Also, is there a way to prevent the XP drive from being seen by Ubuntu?
Sure, just click the eject button next to the drive in file browser. This unmounts it. If you don't want it to be seen by ubuntu, don't click on the drive in the first place, because by doing so, you mount the drive.

---

### Post by wildmanne39 on 2012-04-04
Hi, +1 for asuastrophysics answer and also I believe that you have to become root to be able to use nautilus to copy files to the xp drive so it will not let you without learning first how to become root in the livecd.
Thanks

---

### Post by critin on 2012-04-04
> Is there a risk that a virus or other unwanted files (eg worms/trojans) could be saved to the XP drive?[http://www.tomshardware.com/forum/236882-50-linux-virus](http://www.tomshardware.com/forum/236882-50-linux-virus)

Probably not, but if it did your windows virus program would catch it.

---

### Post by asuastrophysics on 2012-04-04
carmenin87: Welcome to the world of safety and rock-solid stability. I mean of course, Ubuntu and linux in general. While running ubuntu, you are far safer than other people running Windows. Enjoy! :KS

---

### Post by carmenin87 on 2012-04-04
> **asuastrophysics said:**
> Sure, just click the eject button next to the drive in file browser. This unmounts it. If you don't want it to be seen by ubuntu, don't click on the drive in the first place, because by doing so, you mount the drive.

I'm sorry if this sounds like a very basic question, but I don't see an eject button.  Am I looking perhaps in the wrong place?

At the top of the screen it says Computer - File Browser and to the left it says Places, below which it says my User Name, Desktop, File System, Network, Drive C, Drive D, Trash, Documents, Music, Pictures, Videos, Downloads

If I right click on the Windows partition, there is no eject.  The menu I get says Open, Open With Other Application, Copy, Rename, Copy To, Format, Mount, Properties.

---

### Post by asuastrophysics on 2012-04-04
> **carmenin87 said:**
> 
If I right click on the Windows partition, there is no eject.  The menu I get says Open, Open With Other Application, Copy, Rename, Copy To, Format, **Mount**, Properties.

Right! That's because your drives are _not_ mounted. The file browser "sees" your other drives, but none of your drives' contents are readable or accessable because the drive is not mounted. This is the "stowed and safe" position of your drives. Nothing and nobody can change the contents of those drives without them being mounted first (I mean, you could technically format the drive because it's not mounted, but you're not going to do that :p) 

If it says "unmount" when you right-click on it, that means it's already mounted. If it says "mount" when you right-click it, that means it's not already mounted. Also, if it's mounted, a little eject icon should display directly to the right of the drive name in the "Places" pane.
:lolflag:

---

### Post by carmenin87 on 2012-04-04
> **asuastrophysics said:**
> Nothing and nobody can change the contents of those drives without them being mounted first 

 Also, if it's mounted, a little eject icon should display directly to the right of the drive name in the "Places" pane.
:lolflag:

Perfect, I think you just cleared this up for me and I learnt something in the process :)

I just mounted the drive and low and behold, there was the eject button that was referenced earlier.

And the second point is that so long as the drive is NOT mounted, there is nothing from the Internet that could accidentally be downloaded and saved onto the Windows partition.

I think I feel a lot more comfortable.  Thanks again for everyone's help.

---

### Post by holycow131415 on 2012-04-04
even if it is mounted, ubuntu doesnt save things to that drive by default anyway =) You would literally have to tell ubuntu to save a file in your windows drive. Cookies, temp files, etc are all saved in the file system of ubuntu, and gets cleared when you power off when the RAM is cleared since it is a liveCD.

---

### Post by carmenin87 on 2012-04-05
> **holycow131415 said:**
> even if it is mounted, ubuntu doesnt save things to that drive by default anyway =) You would literally have to tell ubuntu to save a file in your windows drive. Cookies, temp files, etc are all saved in the file system of ubuntu, and gets cleared when you power off when the RAM is cleared since it is a liveCD.

I've been running my Ubuntu install under my administrator account.

One of the things that I noticed was that when I double click on a Windows drive, it automatically mounts it.  Out of curiosity, I created a regular user account and this time when I click on a Windows drive, the system asks me for the administrator password.

I seem to have read before (or at least I thought) that it was ok to run Ubuntu under the admin account and that there was no need to create a user account.  I guess for an extra layer of protection, I should really be doing everything under the user account.

---

### Post by zombifier25 on 2012-04-05
> **carmenin87 said:**
> I've been running my Ubuntu install under my administrator account.

One of the things that I noticed was that when I double click on a Windows drive, it automatically mounts it.  Out of curiosity, I created a regular user account and this time when I click on a Windows drive, the system asks me for the administrator password.

I seem to have read before (or at least I thought) that it was ok to run Ubuntu under the admin account and that there was no need to create a user account.  I guess for an extra layer of protection, I should really be doing everything under the user account.

By 'administrator' account do you mean an admin account or the root account? If the former, you are pretty much safe, since even an admin account can't modify system files without the password (only root can, and it's disabled by default). Running a non-admin user account doesn't really do much difference, since you still have to supply the admin's password.
Of course, it pays to be paranoid, so your mileage may vary.

---

### Post by carmenin87 on 2012-04-05
> **zombifier25 said:**
> By 'administrator' account do you mean an admin account or the root account? If the former, you are pretty much safe, since even an admin account can't modify system files without the password (only root can, and it's disabled by default). Running a non-admin user account doesn't really do much difference, since you still have to supply the admin's password.
Of course, it pays to be paranoid, so your mileage may vary.

I'm assuming it's the administrator account, but I have no idea how to tell if it is the root account.

This is the account I setup when I installed Ubuntu and when I look under Users and Groups, it lists this account as account type: Administrator.

---

### Post by SeijiSensei on 2012-04-05
I may be wrong, but I believe the default live CD user, called "ubuntu," has root privileges by default.  Otherwise you wouldn't be able to mount a partition just by double-clicking it.  Ordinarily you'd need a password to gain access to sudo, but since the ubuntu user has no password, I believe it's functionally equivalent to running as the root user.

This doesn't matter in practice if you limit your activities to the read-only Live CD, but it does matter if you mount additional filesystems or devices.

I don't have a Live CD handy to test this at the moment, but if I'm wrong, someone please correct me.

---

