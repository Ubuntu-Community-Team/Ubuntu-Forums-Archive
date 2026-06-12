---
title: "GRUB, does it work with Windows 7"
date: 2010-06-13
forum: General Help
---

### Post by RJ12 on 2010-06-13
Ok, so currently I have 9.10 running with a dual boot with Windows 7 using EasyBCD, I want to upgrade to 10.04 doing a clean install. Problem is, I don't think it will work out using EasyBCD, others are saying in my other thread asking if it works, that I should just let GRUB be my boot manager. Well the problem is, although I have never had one problem with GRUB or GRUB2 in my life, that was on an old Dell Machine running XP, now I have my new laptop and it runs Windows 7, should I continue to use EasyBCD or try GRUB, I don't have one of those Windows 7 Repair CDs, and my recovery is on a partition (factory restore), I get into it by holding "0" when I turn on the computer, if I use GRUB, will I lose that functionality? GRUB2 seems like it would work (When I chose Windows 7 after clicking Ubuntu from the Windows Boot Loader, it starts Windows 7). I am just dead scared and already have the shivers thinking of it.

---

### Post by techunit on 2010-06-13
Grub2 is incredibly stable and very easy to use. easyBCD is fine but it is actually more work and can be harder to fix. To fix grub in the event of a problem is pretty easy and all you need to do is have a live cd and a printed copy of the instructions to fix it. Now I hope I haven't scared you but I have never had a problem with GRUB2 and I think that you won't Either. All you got to do is install ubuntu 10.04 and manually partition it so that it only over rights your old ubuntu install and leaves windows 7 unaffected. Good Luck

---

### Post by oldfred on 2010-06-13
I have had no troubles but since this is a trouble site we do see users that have made mistakes and have issues.

Just to have a way to recover windows:
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run check disk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Some windows problems can be repaired from Ubuntu or other linux based liveCDs like rescue disk or parted magic. I have several of the ISOs set up to boot from my flash drive and have my Ubuntu CD. Since I installed XP from CD I also have that. But I never have had to use any of them except to reinstall grub.

---

### Post by RJ12 on 2010-06-13
Is there a way to test GRUB to make sure that it will see Windows? This would make me feel more confident about using GRUB2.

---

### Post by oldfred on 2010-06-13
We can link you to threads where whatever issue a user had was solved. Only a few gave up and reinstalled. Most users do not have issues and we do not even see them here.

Do you have a Dell or HP. They do install software that violates MBR conventions and causes problems with grub2.

---

### Post by philinux on 2010-06-13
Easybcd works just fine.

---

### Post by RJ12 on 2010-06-13
I have a toshiba laptop, do you think I could see some of those links? It might boost my confidence.

---

### Post by hhoyt on 2010-06-13
You wont have a problem. 
Only thing to avoid is installing Windows AFTER linux.

When you install Ubuntu 10.04 and run sudo update-grub you
will see the probe detects win7 just fine.
-----------
Since you ***SHOULD*** be doing this anyway, ensure that you have run clonezilla against your system first (and again after !)
-----------

Howard

---

### Post by RJ12 on 2010-06-13
> **philinux said:**
> Easybcd works just fine.

Can you confirm that this works for 10.04? I thought I saw a post saying that you used it

---

### Post by oldfred on 2010-06-13
I do not use EasyBCD, but some have and said it works. They have to use the beta or ver 2? Also you then have to force grub2 to install to the partition that Ubuntu is in. I have done that and it works at least initially. The developers say it has to use blocklists which are unreliable. If a file gets moved that it uses for booting you have to reinstall grub2 to the partiton.

---

### Post by RJ12 on 2010-06-13
I feel conflicted :(

---

### Post by RJ12 on 2010-06-13
> **oldfred said:**
> 
Just to have a way to recover windows:
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)


Would I be able to make these within Ubuntu? I think I am gonna install with GRUB2 and see how it works. I am also gonna try to create it with a separate home and root partition. Do you think you could guide me on how much space I should use on each? I will probably need help setting up my partitions as here is what it was like when I got it.

1. System Reserved Partition for Windows 7 (100 MB)
2. Windows 7 (Maybe close to 200 GB)
3. Toshiba System Recovery (7 GB Maybe)

I do know you can't have more than 4 Primary Partitions, but I don't know how I will set up more

EDIT: There might be a better way to show you my partition layout (and the current one) is there a Terminal command I might be able to run? Would you prefer a screenshot of Disk Utility Maybe?

---

### Post by oldfred on 2010-06-13
Windows needs 25% to 30% free space to work well. If you are planning on using windows and Ubuntu I also like to have a separate NTFS partition for shared data. You can easily read the data in win7 but I prefer to only write into system partitions in emergencies from other systems. 

root can be primary or logical depending on what is available, home should be the rest of whatever total space you want to allocate :
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical (or RAM size if hibernation planned)

My Toshiba is 3 years old. The first thing I did was create the recovery CDs and put them away and then delete the recovery partition as I have no desire to ever totally erase and reinstall all the junk that came with the system.

---

### Post by wilee-nilee on 2010-06-13
@oldfred I had the OP show the setup with the boot script here if it helps.
[http://ubuntuforums.org/showthread.php?t=1508291](http://ubuntuforums.org/showthread.php?t=1508291)

OP Like I said before it is smart to get this information.;) And oldfred is the one to get it from, along with others of course.

---

### Post by RJ12 on 2010-06-13
Do I have to use a fixmbr command even though GRUB is installed to the Partition? I am hoping to start but I don't want to blow Ubuntu 9.10 away and then... (Bad things)

---

### Post by RJ12 on 2010-06-13
> **wilee-nilee said:**
> @oldfred I had the OP show the setup with the boot script here if it helps.
[http://ubuntuforums.org/showthread.php?t=1508291](http://ubuntuforums.org/showthread.php?t=1508291)

OP Like I said before it is smart to get this information.;) And oldfred is the one to get it from, along with others of course.

Once, again thanks for the comment, also thanks for showing Oldfred the link to the other post with my current boot script :)

@oldfred, I don't know if the boot script helps, but that is my current setup as of now.

---

### Post by oldfred on 2010-06-13
Grub in a partition is only a problem if you put it into a windows partition (maybe someother systems also). Windows has part of its boot loader in the partition boot sector.

From you boot info it looks like you can just install grub2 to the MBR and be good to go. 

Install from LiveCD:
Find linux partition change sda5 if not correct or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda


To reinstall windows boot loader you can run fixMBR from a windows repair CD. or from linux a generic windows boot loader:

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by techunit on 2010-06-13
Ok if GRUB2 Doesn't see Windows then you go into linux and type sudo update-grub

thats it...

---

### Post by RJ12 on 2010-06-13
> **oldfred said:**
> Grub in a partition is only a problem if you put it into a windows partition (maybe someother systems also). Windows has part of its boot loader in the partition boot sector.

From you boot info it looks like you can just install grub2 to the MBR and be good to go. 
May show error messages about the rest of lilo missing, ignore, we just want MBR

So, since I installed GRUB to the Ubuntu 9.10 partition (Which I believe was sda5) can I blow the partition and everything still being fine while I prepare to install Ubuntu 10.04?

---

### Post by wilee-nilee on 2010-06-13
> **RJ12 said:**
> So, since I installed GRUB to the Ubuntu 9.10 partition (Which I believe was sda5) can I blow the partition and everything still being fine while I prepare to install Ubuntu 10.04?

oldfred can confirm this but yes if you just delete sda5 with gparted on the live cd then make a new ext4 the install to whatever partition # it is grub will automatically take over the mbr=sda and you should be set. Just make sure to click on the advanced button on the last gui to confirm grub is pointed at sda. This is a custom install option I assume you know what that is I think the links are on the thread.

---

### Post by RJ12 on 2010-06-13
> **wilee-nilee said:**
> oldfred can confirm this but yes if you just delete sda5 with gparted on the live cd then make a new ext4 the install to whatever partition # it is grub will automatically take over the mbr=sda and you should be set. Just make sure to click on the advanced button on the last gui to confirm grub is pointed at sda. This is a custom install option I assume you know what that is I think the links are on the thread.


Thanks!! I guess I will see you guys with my new install hopefully!!

---

### Post by oldfred on 2010-06-13
If you are just reinstalling to the same partitions you can use manual install, choose which partition sda5 is / and what format. It finds swap on its own.

Did you back up what ever you wanted. Have you installed a lot of programs and would like to reinstall. if so you can save a list.

---

### Post by RJ12 on 2010-06-13
I feel so proud!! And Now GRUB is my best friend!! And here is what my mixed experiences were.

Go into Windows and open EasyBCD to remove ubuntu entry

Reboot... GASP EasyBCD deleted my Windows Entry, and would not let me get into Ubuntu 9.10.

Boot my Ubuntu 10.04 Flash Drive, and do my partitioning in GParted.

Start installer, and set all mount points

Click install! (I started Shivering and Shaking)

Install finished, click restart. Choose the entry Windows 7 (Loader) on /dev/sda2 (remember the first one contains the BAD BOOTLOADER) it boots into Windows 7 perfectly!! I decided, I was afraid of GRUB when the real one I should have been afraid of was Windows Boot Loader!! I then also got over my fear of GRUB2 and it has become my best friend, on the other hand Windows (and there stupid bootloader), EasyBCD (the tool that helped me get into this dumb mess, but also made me realise my mistake in mistrusting GRUB2, and allowed it to become my best friend!!) has become my enemy!! I hope to not have to boot into Windows for a very long time and then one day convert this to an all Linux laptop!!


I am going to save this thread in my subscriptions so I and others can point to this thread to show others that have the same fear as me, that GRUB is in fact the good guy and not to be afraid. Maybe if they see another user get over this petrifying fear, maybe they can get over it themselves.

I thank all who have posted (and those who would have posted, but missed the chance), and feel free to use this thread the same way I hope too!!


Once again thank you, I feel like a free spirit and I thank GRUB for allowing me to do this. I would also like to send out a thanks to:
Linus Torvalds 
Mark Shuttleworth along with the canonical staff
Whoever created this wonderful forum
And finally, you guys!!

---

### Post by wilee-nilee on 2010-06-13
Cool, I have tried to get grub understood on another forum, but it was like the Sisyphus myth I push that rock up the hill only to find myself at the bottom every morning.

Grub is great because you can actually get in there and tweak it.

---

### Post by oldfred on 2010-06-13
Glad you got it working.

Add solved so others can see that grub really does work.

---

### Post by RJ12 on 2010-06-13
Ok, thanks, totally forgot about marking as solved

---

