---
title: "Am I Stupid? I Lost My Partition"
date: 2011-03-07
forum: General Help
---

### Post by lakelovers on 2011-03-07
I have 10.10 installed. It has worked perfectly. It was a clean install over the latest Windows. Tonight when I booted into Ubuntu, I noticed Windows restore at the bottom of the Grub menue.I thought I had wiped the drive to make my computer 100% Ubuntu. If Windows was still on the drive I wanted to see. So, I clicked on the restore option, and away it went. then on a restart I get the error: no such partition. And under that is a prompt for "grub rescue>." I guess that's what I need to do but what is the command or how do I answer the "grub rescue?" I could make another clean install of 10.10 but I'm guessing there's a way to get back to my Ubuntu without doing that. I don't really want to dual boot.

---

### Post by jerome1232 on 2011-03-07
Yeesh, those things really ought to warn you about what they are about to do before they zip right along!


Well first thing I would do is check to see if the partitions still exist.

Boot into a live cd and post the output of fdisk

```
sudo fdisk -l
```

Even if your partition was wiped out it's possible the application called testdisk can recover your partition table, you can install it while running the live cd but will get to that if we need to.

---

### Post by lakelovers on 2011-03-08
I booted from the 10.10 DVD, got to the option menu and no matter what I selected it ended up with "BusyBox" a built-in shell (ash), and the error: worker [92] failed while handling '/devices/virtual/block/loop0'

Any ideas on what to do next? I haven't tried a fresh install, but I guess I'll go that rout if I don't find another solution. It seems to me that when I get the prompt: "grub rescue," there must be a command that will do the rescue. I'm thinking, now, that my restoring Windows, wiped the Ubuntu partitions.

**Edit**I just tried to do an "install" and the same thing happened: I got Busybox. I tried several of the commands which worked but I don't have enough know-how to put any arguments so I don't get far. At the moment, my laptop is dead. Any help will be much appreciated.

---

### Post by jerome1232 on 2011-03-08
Well the grub rescue prompt can't do much, it drops to that if it fails to find the boot files for grub.

You can type ls at that prompt to get a listing of the devices it recognizes, and look at the file on those devices to try and manually boot the linux kernel.

More on grub2 rescue prompt here: [https://help.ubuntu.com/community/Grub2#Fallback%20mode](https://help.ubuntu.com/community/Grub2#Fallback%20mode)

What version did you originally use to install, try using that live cd.

---

### Post by lakelovers on 2011-03-08
What I get with ls is a list of (hd0,msdos[1thru8]). I tried following instruction on the link you gave me, but nothing worked. I assume that I have grub2 because I installed the latest ubuntu version on a new computer. But, I try one older cd.

**Edit** Ah. . . success. I booted a 10.04 CD and go it up, On the terminal with sudo fdisk -l, I see that Windows accupies /dev/sda1 though 4, and Ubuntu (linux) occupies partitions 5 thru 8 with swap files in 7 & 8. So, where do I go from here?

---

### Post by Bert Mariën on 2011-03-08
It would help if you told us what kind of computer you have.

When you booted the Lucid cd or dvd did you run gparted to check whether your partitions are still there?

It is also very handy to have a cd such as puppy, from which you can always install a new boorloader that works. (grub 0.97)

Also, you should be able to install grub2 again from any cd from Lucid and +.

Because I do not know what kind of computer you have, it is also possible that your computer has 1 or 2 hidden partitions, which means that your fstab might not be correct.

If you have a Dell computer (eg) there are 2 hidden partitions. So the partitions you boot from is not the 1st but the 3rd.

That means that your root (in grub 0.97) is not /dev/sd0 but /dev/sd2

Under Grub2 the story is even different.

---

### Post by cap10Ibraim on 2011-03-08
install grub on dev/sda
```

grub-install /dev/sda

```

---

### Post by Bert Mariën on 2011-03-08
I do not use Grub2 myself, and I do not really know much about it, but one of the essential differences is that Grub2 calles on partitions differently as Grub 0.97 did.

E.g. 
Grub 0.97         -        Grub2 
/dev/sda2         =       /dev/sda3

Personally: I do not like Grub2

Sorry.

---

### Post by Bert Mariën on 2011-03-08
> **cap10Ibraim said:**
> install grub on dev/sda
```

grub-install /dev/sda

```

Okay, installing Grub to to MBR, but that does not change the fact that the partitions should be named as they are.

Just 2 days ago, after I updated Lucid, I also couldn't get in my Lucid system anymore. When installed a new kernel, it asked what to do with the menu.lst file. I choose for the maintainers version. And "wap", I could not log in anymore.

There was NOTHING WRONG with the computer.

The maintainers version of the menu.lst used UUID, and somehow that did NOT work.

I booted from Puppy, changed the menu.lst file from UUID to root (hd0,5), changed in the kernel line the root to root=/dev/sda6 and everything booted and worked again.

Just telling you that the UUID can be wrong, especially when you have hidden partitions on your computer.

---

### Post by lakelovers on 2011-03-08
I just tried "grub-install /dev/sda" and got the message "cp:cannot creat regular file "/boot/grub/915resolution.mod': Permission denied.

**Edit** Gparted shows sda1&2 as "PQSERVICE SYTEM RESERVED." My computer is an Acer laptop with an Intel Pentium process T4500; model 5736Z-4016. The Linux (ubuntu) partitions /sda5&6 are shown as unmounted.The swap files /dev/sda7&8 are mounted.

I have a 350GiB drive. sda3 is ntfs (Acer). sda4 is an extended partition 185.98GiB.

Does any of this provide a clue to recovering my 10.10 ubuntu?

---

### Post by cap10Ibraim on 2011-03-08
with sudo ?
```

sudo grub-install /dev/sda

```

---

### Post by Bert Mariën on 2011-03-08
Did you try

sudo grub-install /dev/sda

Because you need root privileges to install grub.

---

### Post by lakelovers on 2011-03-08
I like the girlies in "netpinky.com" but it doesn't do much for lost files.

I did "sudo grub-install /dev/sda," and got the message : cannot find a device for /boot/grub (is /dev mounted?) No path or device is specified. . . . Please specify the module with the option '--modules' explicitly.

---

### Post by Bert Mariën on 2011-03-08
You still have your Lucid boot cd, haven't you.

Start it up, and run gparted to see whether al yoiur partitions are still there.

If you should have problems, I'll still be here for a while.

---

### Post by coffeecat on 2011-03-08
"sudo grub-install /dev/sda from the live CD is not enough. You need to define Ubuntu's root partition. Have a look here:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

You'll see that the output of...

```
sudo fdisk -l
```... will help you decide which partition to mount before running the longer grub-install command. If you need any help with interpreting the output of fdisk, post the output.

---

### Post by Bert Mariën on 2011-03-08
If gparted is not on the Lucid cd, you should download
 
Puppy: [http://puppylinux.org/main/Download%20Latest%20Release.htm](http://puppylinux.org/main/Download%20Latest%20Release.htm)

Quirky: [http://distro.ibiblio.org/pub/linux/distributions/quirky/quirky-1.4/qrky-140.iso]("http://distro.ibiblio.org/pub/linux/distributions/quirky/quirky-1.4/qrky-140.iso")

-Parted Magic: [http://partedmagic.com/doku.php?id=start](http://partedmagic.com/doku.php?id=start)

Once booted you can startup gparted.

---

### Post by Bert Mariën on 2011-03-08
> **coffeecat said:**
> "sudo grub-install /dev/sda from the live CD is not enough. You need to define Ubuntu's root partition. 

Didn't have a look there, yet, but I think that's a waste of time because you define the ubuntu root partition in the fstab file.

So have a look there (/etc/fstab) 

I know that the UUID is to be safer than the older /dev/hdx, 
In my experiences that is not so.

Try to edit your /etc/fstab file (can only be done as root, so you'll need such a distro like puppy or quirky) and change all the UUID to the old /dev/hdx or /dev/sdx.

I'm sure your problem will be solved.

Keep in mind that numbers vary between Grub 0.97 and Grub2!!!

In Grub 0.97 a partition named /dev/sda0 will be /dev/sda1 with Grub2!!!

---

### Post by coffeecat on 2011-03-08
> **Bert Mariën said:**
> Didn't have a look there, yet, but I think that's a waste of time because you define the ubuntu root partition in the fstab file.

You have misunderstood. So long as the OP's Ubuntu partition is still present - and we can tell that from fdisk if the OP posts the output - then the fix is trivially easy and contained in the link I posted.

When I say "define" the root partition, I mean define as in the command:

```

sudo grub-install --root-directory=/mnt /dev/sda
```... after you have identified which is the Ubuntu root partition that needs to be mounted on /mnt.

---

### Post by Bert Mariën on 2011-03-08
If you should use Puppy or Quirky (I should use the latter) You're automatically logged in as root; so you can change or edit anything you like.
Also your /etc/fstab file.

From Puppy and/or Quirky you can also install the old legacy-grub, so you should be able to log into your ubuntu system again.

From thereon it is just figuring out the problem, change it, and (if you want to) install grub2 again.

My guess (really) is that your problems occur because of your /etc/fstab file.

---

### Post by tredegar on 2011-03-08
I am late to this thread but....
> What I get with ls is a list of (hd0,msdos[1thru8]).

This is a very strange setup. So I wonder if your laptop has a SSD and not a HDD, and it is set up as RAID-0 to improve SSD access times.
[I recently had much trouble installing linux to an expensive sony laptop (not mine) that had this setup. It was a messy fight, but windows lost.]

What, please is the _exact_ model number of your Acer? Or save us the trouble of finding its hardware specs, and tell us if it has such a setup (your laptop's manual *should* tell you, but may not make it clear, because "windows just works, and you don't have to worry about how". *Right*.)

As an aside, booting to "Windows restore" will do just what it says on the tin. Your linux partitions will be gone.
Win is not (never has been and probably never will be) a cooperative OS.

If your partitions were on a RAID-0 disk, which I strongly suspect, and you have booted "Windows Restore" then I believe this to be unrecoverable, but someone may prove me wrong.

Meanwhile, please supply some more information about your hardware and how it is set up.

---

### Post by Bert Mariën on 2011-03-08
Changing your /etc/fstab file can also be done from your Lucid CD.

- Boot it
- Start a terminal
- Type: "sudo passwd root"
- You'll get a question (or not) and you'll have to type a new root password
- Type: "sudo nautilus (if asked for a password, type the one you just entered).
- Search for the /etc/fstab file on your ubuntu system. Open it from within that sudo nautilus (with root privileges).
- Now you can edit and save that file.

Reboot en see what it does.

---

### Post by jerome1232 on 2011-03-08
grub and fstab have very little to do with each other, if fstab was messed up grub would still work, problems would crop up later in the boot process.

OP needs to check the grub2 link given earlier and check out the portion about reinstalling grub 2 from the live cd and follow those steps, since we have confirmed that his partition's are still present, I belive we have a simple bootloader issue here. Once again that has nothing to do with fstab.

---

### Post by coffeecat on 2011-03-08
> **jerome1232 said:**
> grub and fstab have very little to do with each other, if fstab was messed up grub would still work, problems would crop up later in the boot process.

OP needs to check the grub2 link given earlier and check out the portion about reinstalling grub 2 from the live cd and follow those steps, since we have confirmed that his partition's are still present, I belive we have a simple bootloader issue here. Once again that has nothing to do with fstab.

Thank you for saying that, jerome1232. I can see nothing in this thread that suggests /etc/fstab needs editing. This is most likely a simple grub re-installation issue.

---

### Post by Bert Mariën on 2011-03-08
That "someone" would be me.

And be aware: I more than once had problems with updating the kernel, telling that it might use the "maintainers version" and I couldn't get into my system no more afterwards.

But...

Now I come to think of it (thank you for letting me think) it was indeed not the fstab file, but the /boot/grub/menu.lst file.

With Grub2 that'll be the /boot/grub/grub.cfg file.

That is also the mayor reason I do not like Grub2: it always updates and adds kernels to the boot list that are not even wanted.

So; not the fstab file (although it is there it tells the system which partition is the root partition).

So: that leaves the grub.cfg file.

Although you get many messages NOT to edit that file, it is rather easy to do so (as root).

Well... I do not really know anything about grub2 except that it uses different numbers for partitions.

---

### Post by Bert Mariën on 2011-03-08
> **jerome1232 said:**
> grub and fstab have very little to do with each other, if fstab was messed up grub would still work, problems would crop up later in the boot process.

You are slightly wrong.

When Grub (1 or 2) tells to boot from partition /dev/sda5, and your fstab reads that the root system is /dev/sda6, it surely will result in a kernel panic, and you won't be able to boot unless you fix this.

Had this issue many a time.

---

### Post by coffeecat on 2011-03-08
@lakelovers, in case you're still following this rapidly expanding thread, :wink: let's see if we can diagnose exactly what the issue is here. It certainly sounds like a grub issue, but something in your first post suggests a simple grub-install may not be enough.

Boot up with a live Ubuntu CD, make sure you are connected to the internet, and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot script and post the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags. You can use the # icon on the message toolbar for this.

Also, have a look here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

I don't think this is your problem, but let's exclude it. Was the recovery option one of HP, Dell or Samsung?

---

### Post by Bert Mariën on 2011-03-08
Sorry folks, but I forgot what the issue was here.
Sorry again.

If it is a Grub issue, than it'll be a very weird one, well: there ain't no Windows and still it says there is.

So the MBR is not correct either.

Perhaps one needs to overwrite (clean, empty...) the MBR before reinstalling GRUB.

---

### Post by Bert Mariën on 2011-03-08
Don't know how that is done though.

---

### Post by Bert Mariën on 2011-03-08
Peronally, I have a DOS bootdisk with files on from Canadian Mind.

This lets me save the MBR and sector 0 (or is that the same?).

Anyway, it is always a handy disk to fall back on if my MBR gets corrupt. Just boot from the floppy and restore my MBR.

Of course it must be accurate!

As far as I know, a restore of MBR is done from out a windows (or DOS) boot disk.

In this case there really wouldn't be a point for that because there is no more Windows there.

---+---
If (and only if) you should have some other partitions there, perhaps it wouldn't be such a bad idea to install a different distro to that partition. And install that Grub for starters.

Once that seems to work, you should be able to login your Ubuntu system and would also be able to reinstall your Ubuntu Grub.

You can always format the other system drive later and loose it.

Just me thinking...

---

### Post by tredegar on 2011-03-08
To **lakelovers** :

I see lots of well-intentioned advice but precious little *information* or *forensics*. This is not the way to solve problems.

Please re-read my post at #20.

Best wishes.

---

### Post by Bert Mariën on 2011-03-08
> **tredegar said:**
> This is a very strange setup. So I wonder if your laptop has a SSD and not a HDD, and it is set up as RAID-0 to improve SSD access times.


What, please is the _exact_ model number of your Acer? Or save us the trouble of finding its hardware specs, and tell us if it has such a setup (your laptop's manual *should* tell you, but may not make it clear, because "windows just works, and you don't have to worry about how". *Right*.)

If your partitions were on a RAID-0 disk, which I strongly suspect, and you have booted "Windows Restore" then I believe this to be unrecoverable, but someone may prove me wrong.

Meanwhile, please supply some more information about your hardware and how it is set up.

I think it will hardly be a SSD. There are not so many around yet.
Also too expensive!

It surely would be nice to now the exact hardware especially (as I mentioned before) some brands ship their systems with hidden partition,
And THAT (also that) can bring troubles to the grub(2) bootloader.

Knowing about the hardware would surely help.

---

### Post by lakelovers on 2011-03-08
Well, I've tried about everything mentioned on this thread but still can't boot my 10.10 ubuntu. I did get a grub prompt but I didn't have success using the prompt to get into my Ubuntu. The one thing I can do is boot into a live 10.04. I think I may install 10.04 and, if that is successful, then I'll move on up to the 10.10 fresh install. Any comments on this plan? 


My computer is an Acer laptop with an Intel Pentium process T4500; model PEW72. The Linux (ubuntu) partitions /sda5&6 are shown as unmounted.The swap files /dev/sda7&8 are mounted.

I have a 350GiB drive. sda3 is ntfs (Acer). sda4 is an extended partition 185.98GiB.

---

### Post by Bert Mariën on 2011-03-08
So you're /dev/sda3 IS still Windows...

That is not what you mentioned earlier.

Anyway, as I told you before: see that you have a puppy or Quirky cd handy (rather fast) and eventualy install grub (0.97) from there.

Once you have logged in to your Ubuntu system, you can try to find the problem and install your ubuntu-grub back afterwards.

However: it is ALWAYS a good thing to have a CD from Quircky (or Puppy) somewhere near!

---

### Post by coffeecat on 2011-03-09
> **lakelovers said:**
> Well, I've tried about everything mentioned on this thread but still can't boot my 10.10 ubuntu.

No, you have not. Take note of this  comment from tredegar:

> **tredegar said:**
> I see lots of well-intentioned advice but precious little *information* or *forensics*.

Earlier in the thread, jerome1234 asked you to post the output of fdisk. That would have given us a lot of useful information, but you did not. Later on I also asked you to post the output of fdisk. You did not. Then I asked you to post the output of the boot script. The boot script has proven itself time and time and time and time again on this forum to be excellent at diagnosing problems such as yours. Without diagnosis, no one can prescribe treatment. Did you post your boot script output? You did not.

If you want help that is effective you need to provide sufficient information.

---

### Post by Bert Mariën on 2011-03-09
I understand you completely.

You may not think much of me, but I also did ask about his hardware.

And yes: he did not answer that.

---

### Post by coffeecat on 2011-03-09
> **Bert Mariën said:**
> You may not think much of me

@Bert Mariën, if that comment is addressed to me, that is not so. :) You have been trying to help the OP and indeed everyone in this thread has been trying to help the OP. And sometimes discussion amongst thread participants around issues that arise from the OP's problem can be very useful - even the red-herrings. But I think we need to focus at the moment on getting the OP to provide appropriate information. So...

@lakelovers, if you post the output of the boot script I linked to, you need not post the output of fdisk. The boot script includes information from fdisk and much else besides. It may not fully diagnose your problem, but at least it will be a start in trying to see what has gone wrong.

---

### Post by Bert Mariën on 2011-03-09
> **coffeecat said:**
> @Bert Mariën, if that comment is addressed to me, that is not so. :) You have been trying to help the OP and indeed everyone in this thread has been trying to help the OP. And sometimes discussion amongst thread participants around issues that arise from the OP's problem can be very useful - even the red-herrings. But I think we need to focus at the moment on getting the OP to provide appropriate information. So...


Thanks for seeing the upside of it all. 
And indeed: I'm just trying to help.

---

### Post by Bert Mariën on 2011-03-09
So, what can I (we) do to help?

---

### Post by lakelovers on 2011-03-09
Okay, I really do appreciate all the help being offered. I have posted my hardware info a couple of times. I downloaded Puppy, but I couldn't get it burned on a CD or DVD. I have two apps (Brasero and CD/DVD creator)and neither accept the CD/DVD, which are blank. I am accessing the Internet with 10.04 live CD. I ran the boot scrip but the info I got was command definitions I would get by doing "help." I'll try that again, also. My last posting about my hardware is in message #32. I can access gparted in the live CD I'm using. Is there anything I can do with gparted to correct my problem? I'm grasping at straws. While I have used a computer for many years and have used Ubuntu exclusively for over 10 years, never-the-less, I am neither a computer nor a Linux whiz. . . obviously.

**Edit** By the way, I cannot access Windows either, and I don't want it.

---

### Post by Bert Mariën on 2011-03-09
When running gparted, can you see all your partitions?

If so, everything you need is there.

Perhaps you can try a "surprise" force, and first reinstal the windows MBR.
Then booting from a Linux CD install Grub again.

You'll never know unless you try.

---

### Post by Bert Mariën on 2011-03-09
I mentioned gparted before because with that program you can see whether your partitions are still there.

I do not know if you can correct errors with it. I doubt it.

---

### Post by Bert Mariën on 2011-03-09
Do you know how to reinstall the windows MBR?

Start from a windows (DOS) boot disk, and run 

fdisk /mbr

Then reboot.

Your Windows MBR has reinstalled.

Then boot from a Linux cd and reinstall grub.

See if this helps.

I know it seems stupid, but many a bug or error is stupid.

Just try it.

---

### Post by Bert Mariën on 2011-03-09
By the way: do you have a floppy drive?

---

### Post by Bert Mariën on 2011-03-09
Weird you cannot burn a puppy iso...

---

### Post by lakelovers on 2011-03-09
Finally... I think I have what you wanted regard the boot script. I hope this helps.



```
                  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk /boot/grub/core.img

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    27,265,023    27,262,976  27 Hidden HPFS/NTFS
/dev/sda2    *     27,265,024    27,469,823       204,800   7 HPFS/NTFS
/dev/sda3          27,469,824   235,111,535   207,641,712   7 HPFS/NTFS
/dev/sda4         235,112,446   625,141,759   390,029,314   5 Extended
/dev/sda5         365,246,464   489,519,336   124,272,873  83 Linux
/dev/sda6         489,521,152   609,294,335   119,773,184  83 Linux
/dev/sda7         609,296,384   614,486,015     5,189,632  82 Linux swap / Solaris
/dev/sda8         614,500,352   625,141,759    10,641,408  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       85e5f577-4684-44d3-89a3-5cd043f5f63a   ext4                                     
/dev/sda1        FECA72A5CA725A3B                       ntfs       PQSERVICE                     
/dev/sda2        62EE72F5EE72C0B9                       ntfs       SYSTEM RESERVED               
/dev/sda3        0696741996740B85                       ntfs       Acer                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        9e39bc7d-cabe-409a-a8a6-a04725b648ec   ext4                                     
/dev/sda6        ed42def4-5675-418e-bb18-dbacebaf922f   ext4                                     
/dev/sda7        1330d542-a597-43cf-83c0-fc348f120d88   swap                                     
/dev/sda8        9b73aaf1-5022-4873-b743-84040c8984d6   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda3: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

======================== sda3/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
}

if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-25-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 0696741996740b85
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-25-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, Linux 2.6.35-25-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 0696741996740b85
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-25-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 0696741996740b85
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 0696741996740b85
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set feca72a5ca725a3b
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 62ee72f5ee72c0b9
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

============================= sda3/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda3/Wubi: Location of files loaded by Grub: =================


   6.8GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
   2.6GB: boot/initrd.img-2.6.35-25-generic
  13.1GB: boot/vmlinuz-2.6.35-22-generic
  13.1GB: boot/vmlinuz-2.6.35-25-generic
   2.6GB: initrd.img
    .9GB: initrd.img.old
  13.1GB: vmlinuz
  13.1GB: vmlinuz.old

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=9e39bc7d-cabe-409a-a8a6-a04725b648ec /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9b73aaf1-5022-4873-b743-84040c8984d6 none            swap    sw              0       0

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set ed42def4-5675-418e-bb18-dbacebaf922f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set ed42def4-5675-418e-bb18-dbacebaf922f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set ed42def4-5675-418e-bb18-dbacebaf922f
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=ed42def4-5675-418e-bb18-dbacebaf922f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set ed42def4-5675-418e-bb18-dbacebaf922f
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=ed42def4-5675-418e-bb18-dbacebaf922f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set ed42def4-5675-418e-bb18-dbacebaf922f
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=ed42def4-5675-418e-bb18-dbacebaf922f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set ed42def4-5675-418e-bb18-dbacebaf922f
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=ed42def4-5675-418e-bb18-dbacebaf922f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set ed42def4-5675-418e-bb18-dbacebaf922f
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=ed42def4-5675-418e-bb18-dbacebaf922f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set ed42def4-5675-418e-bb18-dbacebaf922f
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=ed42def4-5675-418e-bb18-dbacebaf922f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set ed42def4-5675-418e-bb18-dbacebaf922f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set ed42def4-5675-418e-bb18-dbacebaf922f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set feca72a5ca725a3b
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 62ee72f5ee72c0b9
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=ed42def4-5675-418e-bb18-dbacebaf922f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=1330d542-a597-43cf-83c0-fc348f120d88 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 285.1GB: boot/grub/core.img
 274.6GB: boot/grub/grub.cfg
 251.6GB: boot/initrd.img-2.6.35-22-generic
 300.3GB: boot/initrd.img-2.6.35-25-generic
 250.8GB: boot/initrd.img-2.6.35-27-generic
 285.1GB: boot/vmlinuz-2.6.35-22-generic
 285.1GB: boot/vmlinuz-2.6.35-25-generic
 285.2GB: boot/vmlinuz-2.6.35-27-generic
 250.8GB: initrd.img
 300.3GB: initrd.img.old
 285.2GB: vmlinuz
 285.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb  
```

---

### Post by Bert Mariën on 2011-03-09
Of course you know you have to burn a ISO as ISO and not as data.

---

### Post by coffeecat on 2011-03-09
> **lakelovers said:**
> Finally... I think I have what you wanted regard the boot script. I hope this helps.

This is a complex problem. Grub in the mbr is pointing to sda3 which is one of your Windows partitions. You have evidence of a wubi installation as well as a conventional Ubuntu installation on its own partition. There are also grub files in the Windows partition. I will ask someone with experience of wubi to look at this.

---

### Post by Bert Mariën on 2011-03-09
Also: just as I thought: you have hidden partitions.
At least one.

I have had many a problem with that.

---

### Post by Rubi1200 on 2011-03-09
@ lakelovers: if this is the current state of your computer with the boot script results, you need to take a deep breath before we continue.

Firstly, because, quite frankly, you have a messy setup.

Second, you need to make some decisions about what you want before we make any changes. 

This means, amongst other things, do you want Wubi and Windows or just Ubuntu? Were you aware of the fact that this was the situation?

You also appear to have installed Ubuntu twice??

@ Bert Mariën: I understand you just want to help. Believe me it is appreciated, but I would respectfully ask you to step back here and let some other users sort this out.

---

### Post by coffeecat on 2011-03-09
> **Rubi1200 said:**
> @ lakelovers: if this is the current state of  your computer with the boot script results, you need to take a deep  breath before we continue.

Firstly, because, quite frankly, you have a messy setup.



@lakelovers, I agree 100% with Rubi1200 about both those statements. Before you respond, may I remind you of this in your first post:

> **lakelovers said:**
> I don't really want to dual boot.

You already had the makings of a dual-boot anyway. Not only do you have wubi Ubuntu in the Windows partition and a separate conventional Ubuntu installation on partition sda5, but you have yet another Ubuntu installation on sda6, and two separate swap partitions!

This means you have installed Ubuntu at least three times: once with wubi and twice conventionally to separate partitions. 

Decide which Ubuntu installation you want to use and then listen to what Rubi1200 has to advise. And good luck! I will follow the thread with interest and contribute  if I have something useful to say.

**EDIT**: when you say you don't want to dual-boot, does that mean you want Ubuntu only? Be clear in stating what you want.

---

### Post by Rubi1200 on 2011-03-09
I think the most important question to answer is this:

what do you want as the end result?

Forget about the current setup and focus on how you would like the computer to run.

Once you tell us _exactly_ what you want, we can advise you further.

---

### Post by jerome1232 on 2011-03-09
[COLOR="Silver"]Based on several statements in previous posts, I believe the OP wants to boot Ubuntu and Ubuntu only. The OP did mention not wanting Windows several times.


off subject: I didn't realize how useful that bootscript is, might help me revive an install that I haven't had the time to troubleshoot yet :)[/COLOR]

edit: Sorry post was redundant, This thread keeps jumping by leaps and bounds when I'm away :)

---

### Post by lakelovers on 2011-03-09
Bottom line: **I want only Ubuntu 10.10 on my computer**. No dual boot. The multiple Ubuntu installs are probably there because of my messing around trying to get things working. In review: my problem started when I booted up 10.10 after using it for several weeks without problems. When grub appeared on boot, I noticed for the first time that windows was on the bottom of grub menu. I thought I had wiped it off when I installed Ubuntu 10.10. I clicked on the Windows recovery . . . before thinking (bad move). So, Windows took off and corrupted the Ubuntu boot process. After that, I couldn't get anything to boot. I wish I could be more responsive to everybody's reqest for more information, but my brain doesn't compute as well as it should.

---

### Post by Bert Mariën on 2011-03-09
I know that I need to back off.

I just want to say that the Windows partition you notice on your Grub is probably the Hidden partition and not really the Windows partition which you removed.

---

### Post by coffeecat on 2011-03-09
> **lakelovers said:**
> Bottom line: **I want only Ubuntu 10.10 on my computer**. 

See what Rubi1200 and others say, but I would suggest this would be quickest and easiest:

1 - Use a live CD to copy any personal data off the hard drive onto backup media. If your data is in your wubi installation, I must defer to Rubi1200 on how to do that.

2 - Make a fresh installation of Ubuntu using the whole hard drive. That is the easiest option in the installer. If you want a more complex partition set up with a separate home partition (for example), you need to use the manual/advanced option in the installer.

If you need any help with that, just ask. :)

---

### Post by jerome1232 on 2011-03-09
> **lakelovers said:**
> I wish I could be more responsive to everybody's reqest for more information, but my brain doesn't compute as well as it should.

Really all we need to know is do you have irreplaceable data like documents, pictures, music and etc... that need's to be backed up?

---

### Post by Rubi1200 on 2011-03-09
> **coffeecat said:**
> See what Rubi1200 and others say, but I would suggest this would be quickest and easiest:

1 - Use a live CD to copy any personal data off the hard drive onto backup media. If your data is in your wubi installation, I must defer to Rubi1200 on how to do that.

2 - Make a fresh installation of Ubuntu using the whole hard drive. That is the easiest option in the installer. If you want a more complex partition set up with a separate home partition (for example), you need to use the manual/advanced option in the installer.

If you need any help with that, just ask. :)
I am in total agreement with coffeecat and would have suggested the same approach.

Backup all important data and then start afresh. The current situation, though theoretically fixable, is really not a working solution.

To copy data from the Wubi root.disk, you can use [ext2read]("http://ext2read.blogspot.com/") to recover any important stuff or from the LiveCD by loop mounting the root.disk:

```
sudo mkdir /media/win 
sudo mount /dev/sda3 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
```
Then just navigate to your home folder and recover files from there.

---

### Post by NJPinator on 2011-03-09
As others have said, obviously the first thing to do is **back up all personal and/or needed data!!!** After that's all done, boot from a Live CD/DVD/USB and start GParted at [System > Administration > GParted].

Here you can browse your hard drive(s). Select all the partitions on the drive you plan to install Ubuntu on and delete them, then click the green checkmark in the toolbar at the top of the window. This executes the operations you just did **PERMANENTLY**!
Alternatively, you could select [Device > Create Partition Table...] from the menu in GParted and format to an MS-DOS layout rather than manually removing the partitions one-by-one (just make sure no partitions are mounted on this drive, whichever option you choose).

You can now "Install Ubuntu" from the desktop launcher and use the newly cleaned har-drive as an installation point (just choose "Erase and use the entire disk" if installing 10.04 LTS / "Use Entire Disk" if using 10.10 when the installation procedure comes to partitioning the disk). Continue with installation and all is good!

---

### Post by lakelovers on 2011-03-09
Fortunately, I having nothing of great important on the computer. It's a nuisance to re-enter somethings but I've gone through it before as you might suspect. I figured I'd probably end up wiping the drive and making a fresh install. So, here I go.

---

### Post by NJPinator on 2011-03-09
Great! Let us know how it goes and make sure to mark this thread as "Solved" ;) (if it becomes solved, that is...:D)

---

### Post by lakelovers on 2011-03-09
I'm back in business. I had to install 10.04. The 10.10 DVD would not boot. Thanks to everybody for your help. I still think Ubuntu is best OS available.

---

### Post by Bert Mariën on 2011-03-09
I am not supposed to react any more.

But the problem was not solved.

You just reinstalled everything.

That is not a solution. That is just a new install.

You could have done that from the beginning.

---

### Post by Bert Mariën on 2011-03-09
I was told to back off and leave the solution of the problem by others.

Well, you surely did that. Just a new install.
The problem was not solved then.

Of course it is great you can boot into Ubuntu once more.

---

### Post by Rubi1200 on 2011-03-10
> **lakelovers said:**
> I'm back in business. I had to install 10.04. The 10.10 DVD would not boot. Thanks to everybody for your help. I still think Ubuntu is best OS available.
No problem, I am glad you got things sorted out in the end.

Good luck :)

---

### Post by coffeecat on 2011-03-10
> **Bert Mariën said:**
> But the problem was not solved.

You just reinstalled everything.

That is not a solution. That is just a new install.

You could have done that from the beginning.           

Your criticism of a re-installation is unjustified. You are not being pragmatic.

The OP could indeed have re-installed right from  the beginning, but that would have been a cop out without first finding out what the underlying problem was. When we finally had a view of the OP's boot script output it revealed no less than three Ubuntu installations, one of which was a wubi install inside Windows. I do not criticise the OP for the multiple installations - this can happen if you are new to the installer and try to re-install. Since the OP wanted an Ubuntu-only system, achieving this without a re-installation would involve deciding whether the sda5 or sda6 install was wanted, re-installing grub, and then doing something about the mess of partitions so that the OP could use the whole capacity of the hard drive. Resizing or moving partitions around an in-situ installation always contains the potential for disaster, so a re-install might have been needed anyway. All of this is why Rubi1200 and I recommended a re-install as the quickest and easiest option (and from their wording I guess other posters felt the same way) - but only after we had all the relevant information to hand.

---

