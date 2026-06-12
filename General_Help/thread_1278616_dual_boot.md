---
title: "dual boot"
date: 2009-09-29
forum: General Help
---

### Post by drakce on 2009-09-29
Can everyone paste here url where i can learn how to setup duall boot for ubuntu 9.04

---

### Post by ZaHACKieL on 2009-09-29
What exactly did you do? I mean, my usual way to the a dual boot (I think it is the easiest way) is to make 2 partitions (or 3 if you want a shared NTFS partition).

What I do first is making a NTFS partition where I install Windows, leaving the rest of the HD space as an unallocated/unformatted space, so, after having Winblows runing fine, I install the Ubuntu with the option that says something like: "Use the next continuous free space" , so it will use you unallocated space.

And that's it! (at least for me), Ubuntu will install the grub and that stuff.

So, if you want to install again ubuntu without deleting windows, I would just erase the ubuntu partition, leave it as unallocated space and install ubuntu there.

Let me know if you have problems

---

### Post by Mobil1 on 2009-09-29
I know this isn't technically a dual boot but I'd honestly recommend using the option on the live cd (booted in Windows?) to "install inside Windows" it gives the option to add say 20GB for your Ubuntu depending on your space and acts almost like a dual boot. So you choose which OS to use when you boot. 

Up to you but I remember having a nightmare with MBR and GRUB issues dual booting with Ubuntu 8.10 and XP. So just my 2 cents :)

BTW if you dont like the install inside Windows option just remove it uninstall it like any other program in Windows via control panel and it'll be like it was never there!!

---

### Post by thoriumchameleon on 2009-09-29
Just make sure you install windows first because if you install ubuntu first the windows bootloader will overwrite grub and then you might have problems if you're not linux savvy. If for some reason grub prevents windows from starting post the error code you are given by windows. It should be an easy fix. Lastly if you want to uninstall ubuntu, when you delete the partition you will get an error from grub that will prevent you from booting windows. So make sure you have a recovery disk handy and you can go to the command prompt and type fixmbr.
Happy dual booting!

---

### Post by im.saravanan on 2009-09-29
Simply -install windows first on one drive and ubuntu on any other drive(i mean partition). ubuntu automatically gives you a dual boot option. select windows or ubuntu as you like when the computer is started. and enjoy

---

### Post by oldfred on 2009-09-29
This site has graphical dual boot examples, see right column for others than the title of this one:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

This site is great but may be too much for a beginner. If you search a little there are graphical examples with explanations:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by ZaHACKieL on 2009-09-29
> **Mobil1 said:**
> I know this isn't technically a dual boot but I'd honestly recommend using the option on the live cd (booted in Windows?) to "install inside Windows" it gives the option to add say 20GB for your Ubuntu depending on your space and acts almost like a dual boot. So you choose which OS to use when you boot. 


Personally, I think that's a bad choice. I don't have now technical reasons to support my claims, just the experience I've had with that kind of installation "inside Windows" . As far as I've tried, it never works good and it's a pain in the ****.

The problems with GRUB and MBR can be avoided, I think, just by letting the linux do its work, using the auto installation.
As I said, the easiest way for dual boot: 

1) One NTFS partition
2) The rest, unallocated space
3) Install Win in NTFS partition
4) Use Linux CD and tell it to use the unallocated partition.
5) Drink 2 beers.

Anyway, this is just my opinion, experience and advise.

Regards!!!

ZL

---

### Post by Mobil1 on 2009-09-29
> **ZaHACKieL said:**
> Personally, I think that's a bad choice. I don't have now technical reasons to support my claims, just the experience I've had with that kind of installation "inside Windows" . As far as I've tried, it never works good and it's a pain in the ****.

The problems with GRUB and MBR can be avoided, I think, just by letting the linux do its work, using the auto installation.


Hey ZL Regards to you to bro! Well that's ok if you don't like my suggestion. It's just from personal experience, you say "within windows" is bad from your experience and from mine "dual boot" is bad. Nice to give the guy some options though we are all here to help hehe! 

I have to be honest though I've never had any problem with the inside windows version but just have a look at google with "ubuntu dual boot can not load windows" {sorry edited} search and the endless horrors there :(

---

### Post by aatyler on 2009-09-29
> **Mobil1 said:**
>  
I have to be honest though I've never had any problem with the inside windows version but just have a look at google with "ubuntu dual boot can not load windows" {sorry edited} search and the endless horrors there :(
 
Just my $0.2:
 
I read all of the horror stories and the method that I found that avoids all that is this:
 
1) shrink/re-allocate the partitions
2) install windows (I can't say for XP, but for vista, vista MUST be installed first)
3) install ubuntu
4) if needed, do an installation repair with a Vista CD. Vista is very picky about how the boot loader is setup and you may get some nasty error messages. But, once I did the install repair, I had no further problems and am now happily running ubuntu on its own partition.
 
Hoped this help. 
 
PS: I'm not at home right now, I'll post the sites that I used to guide me through the process tommorow

---

### Post by blackened on 2009-09-29
There is no one right way to create a dual boot setup, and it's going to be largely a matter of personal preference.

The only piece of wisdom I can pass to you is that you must be willing to break things (or deal with things that others have broken) in order to learn how to properly fix them.

I heartily encourage you to read up, then experiment. The worst that can happen is that you'll fail and must try again. But you'll learn, and that's the most important thing.

---

### Post by Chriswilkie on 2009-09-29
if you have windows just pop in the CD and click "install inside of windows and it should give you the option to dual boot after installation

---

### Post by ZaHACKieL on 2009-09-30
> **Mobil1 said:**
> 
I have to be honest though I've never had any problem with the inside windows version but just have a look at google with "ubuntu dual boot can not load windows" {sorry edited} search and the endless horrors there :(

Yeah, I remember the only time I had problems with the installation was when I tried to do everything manually, that was a pain in the **** and that's why I started using the auto option =]

---

### Post by drakce on 2009-09-30
this is how looks my partition after seconds try to install ubuntu.
first i was instal windows xp
after seconds instal i have 2,5gb on har for use ubuntu, 
then i was deleted E partition and instal ubuntu again.
Afther this i can load windows xp to grub.

---

### Post by aatyler on 2009-09-30
> **drakce said:**
> this is how looks my partition after seconds try to install ubuntu.
first i was instal windows xp
after seconds instal i have 2,5gb on har for use ubuntu, 
then i was deleted E partition and instal ubuntu again.
Afther this i can load windows xp to grub.
 
 
So you have everything working as you want? If not, here are the sites I promised. Feel free to post back with any questions.
 
 
[[COLOR=#444444]https://help.ubuntu.com/community/Installation[/COLOR]]("https://help.ubuntu.com/community/Installation")
[[COLOR=#444444]http://members.iinet.net/~herman546/index.html[/COLOR]]("http://members.iinet.net/~herman546/index.html")
[[COLOR=#444444]http://apcmag.com/how_to_dualboot_vi...lled_first.htm[/COLOR]]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")

---

### Post by drakce on 2009-10-01
after reading this link i cannot load windows to grub.

---

### Post by aatyler on 2009-10-01
> **drakce said:**
> after reading this link i cannot load windows to grub.


What link? Can you post the error messages your getting? 

I just want to make sure I understand you:

Do you have ubuntu up and running? Or do neither windows or ubuntu load?

---

### Post by drakce on 2009-10-02
A do it *** write in all links and all post before, but when i try to load windows to grub a have error 12 i think and write to me wrong particion selected, and a try to load from all partitions makin 25 form hd (0,0) to hd(5,5) but i can not load windows to gub

---

### Post by oldfred on 2009-10-02
If your partitions are as before you put the NTFS partitions in the extended partition. Windows has to be in a primary and linux does not care, it can be primary or extended. 

You can have four primary partitions but if you want more you can convert one primary to extended. 

All the dual boot sites discuss that it is easiest to install windows first to the first primary then install linux.

If you have not done much it will be a lot easier to reinstall windows. You can leave the Ubuntu as the first partition and make windows a second primary partition. Everything else can go into the extended partition.

---

### Post by drakce on 2009-10-03
I first have instaled windows on NTFS, but i would like to edit grub or something else if is posibile to load windows to grub.
I like to reinstal ubuntu if I can made grub to see windows, i do it 2 times but i can not load windows afther this reinstall.
I don't try to set windows to be MBR i think its wrilte like this, maybe i need to do this but i don't know how.
Sory my englisch are so bed.

---

### Post by aatyler on 2009-10-03
> **drakce said:**
> I first have instaled windows on NTFS, but i would like to edit grub or something else if is posibile to load windows to grub.
I like to reinstal ubuntu if I can made grub to see windows, i do it 2 times but i can not load windows afther this reinstall.
I don't try to set windows to be MBR i think its wrilte like this, maybe i need to do this but i don't know how.
Sory my englisch are so bed.


no worries about the english man. As to your problem, heres my advice, keep in mind im not an expert, but the easiest way seems to be to follow this link [http://ubuntuforums.org/showthread.php?t=659573](http://ubuntuforums.org/showthread.php?t=659573) to completely wipe the MBR (which is where grub is installed), wipe all of the patritions using gparted or whatever program you prefer, and then create the partitions. 

1) NTFS partition for windows (best bet is to make this a primary partition and the 1st one on the disk)
2) what ever partitions you want for linux. I personally use 1 partition for root (/) and one for my home directory (/home)

Then install windows to the first partition, once you have it working, install Ubuntu and repair the windows installation if needed. I hope this advice helps, and if any one out there knows a better way than me, please correct me.

EDIT: also, for creating the partitions, make one with what ever size you want for windows, and leave the rest un-partitioned space and let the Ubuntu installer make the partitions. its pretty easy and you can tell it what you want that drive to mount to (like root, or /home, or whatever). From re-reading your posts, i would recommend that you create a bigger partition for linux than 2.5 gb. I would say, if possible, at least 5 or 6 gigs for linux. If you have a laptop, you may also want to create a swap partition if you intend on using the hybernate feature. Typically, swap should be about double the size of your ram. so if you have 2 gigs of ram, then make a 4 gig swap partition. Of course this is optional if your low on space.

-Adam

---

### Post by Rotax on 2009-10-03
In past I having trouble dual boot with Fedora Core and Windows and gave up. 
This time is different. I has 3 drives that are all master and can boot separate. 
ie: 1st drive for WinXP 
     2nd drive Ubuntu without dual boot. Plan to install as dual boot Fedora Project.
     3rd drive blank, or maybe Fedora Project or any window or win 7. 

see website for cable, [http://www.thesataswitch.com/](http://www.thesataswitch.com/)

with that cable, it going to save alot hassle on dual boot, I am sure that dual boot with 
WinXp almost alway in mess. So to this around, put window xp in separate drive and Linux system in other drive.

---

### Post by drakce on 2009-10-04
Thank you this is good link but i would like if is possibile to reinstall ubuntu and use instaled windows xp withotu reinstal.
I would like if is posibile to edit grub or to add some other boot program super grub if i can hold instaled xp. but this is good i didn't know this, thanks one more time :)

---

### Post by Rotax on 2009-10-07
> **drakce said:**
> Thank you this is good link but i would like if is possibile to reinstall ubuntu and use instaled windows xp withotu reinstal.
I would like if is posibile to edit grub or to add some other boot program super grub if i can hold instaled xp. but this is good i didn't know this, thanks one more time :)

I just restore Ubuntu image from external storage to Drive 2 and everything is just fine. 
On Drive 2, it is for Ubuntu system only and on drive 1 that is windows xp residence. I am using Clonezilla to backup and restore on Drive 2. I may try Clonezilla to backup on Drive 1 to external storage to see what result. I think these 3 drives are master to save my hassle problem. I am thinking to install other Linux system (Fedora Project) in Drive 2 along with Ubuntu.

---

### Post by drakce on 2009-10-07
How can i install  Clonezilla on ubuntu, i try Synaptic but i cannot find  Clonezilla in this manager.
If you have comad sudo ... please paste this.

---

### Post by Rotax on 2009-10-07
Need to download from website, and it is [http://www.clonezilla.org/](http://www.clonezilla.org/) and then click download. This is LiveCD mean that backup from boot disk also restore too.

---

### Post by parrotred on 2009-10-08
i have a 3 hard disk
primary master as 60 gb seagate windows
primary salve 160 gb seagate data single ntfs partition
secondary master dvd-ram lg gh22
secondary slave 20 gb samsung ubuntu jaunty


I first installed windows and then unplugged that hard disk and installed ubuntu.
I have been using the system by removing either hard disk but now i would like to use both windows and ubuntu as dual boot.
i tried the following

sudo dd if=/dev/sdc1 of=bootsect.lnx bs=512 count=1 
i copied the bootsect.lnx from dev/home to the ntfs partition and then removed the ubuntu cable and logged in windows and than copied the bootsect.lnx to c drive and modified the boot.ini with following
c:\bootsect.lnx="Linux UBUNTU"

This did not work

so i tried this
sudo dd if=/dev/sdb1 of=bootsect.lnx bs=512 count=1 
i copied the bootsect.lnx from dev/home to the ntfs partition and then removed the ubuntu cable and logged in windows and than copied the bootsect.lnx to c drive and modified the boot.ini with following
c:\bootsect.lnx="Linux UBUNTU"

This did not work


Please guide me what should i do in order to dual boot with windows xp as the main and ubuntu as second.

---

### Post by oldfred on 2009-10-08
[parrotred]("http://ubuntuforums.org/member.php?u=926764") you should start a new thread as it can get confusing on who we are trying to help the orginal OP or you.

What you are trying to do may work, my old OS2 system used to have a script to do just that. Today we install Grub and have a menu to choose which operating system to use.

---

### Post by drakce on 2009-10-15
On end I need to reinstall these 2 systems it's now work fine. 
In future if i need can i only reinstall window xp to tray to save all programms on linux ubuntu?
In this case how i need to edit grub after reinstall win xp?

---

### Post by oldfred on 2009-10-15
If you reinstall windows it will put Windows in the MBR. You have to reinstall Grub to the MBR with your current ubuntu partition as where it will go to boot. From a liveCD:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
#reset grub boot
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd1,0)
root (hd1,0) #use the numbers from the previous command
setup (hd0)
exit

You also can use supergrub
[http://www.supergrubdisk.org/wiki/USB_Boot](http://www.supergrubdisk.org/wiki/USB_Boot)
[http://www.supergrubdisk.org/w/index.php5?title=SuperGrubDisk](http://www.supergrubdisk.org/w/index.php5?title=SuperGrubDisk)

---

