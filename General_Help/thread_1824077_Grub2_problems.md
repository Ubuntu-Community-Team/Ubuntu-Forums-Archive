---
title: "Grub2 problems"
date: 2011-08-13
forum: General Help
---

### Post by meharts on 2011-08-13
Hi again!:)

Starting this thread because I don't think it has anything to do with grub customiser....but who knows....LOL

OK! I should explain that I am dualbooting Windows 7 and Ubuntu 11.04 on a customer computer...

I have written extensive "How To's" on the subject of dualbooting on another forum and it was a while ago before the updates to grub2....

This computer has a 160GB ssd hard drive with Windows 7 on it on its own....

There is a 1 TB drive with Ubuntu 11.04 and backup partitions for windows files....

I already installed Windows for a customer after building a new computer for him when a storm knocked out the other one....sorry, waffeling...LOL

With the windows 100mb partition I am not sure what is best when installing grub2...Do I install it on the Windows ssd drive or at the root of the 1TB drive?

Anyway, I can't remember my choice this time and installed Ubuntu...choosing the old partitions from a previous install (1TB drive was main drive in old computer)....

**More Info:**
Should also explain that before a fresh install of Ubuntu 11.04 I had installed karmic koala about a year back on the 1TB and my customer had crashed his computer with out telling me and lost access to Ubuntu....and reinstalled windows 7 himself, but after the storm.....

So, after doing a fresh install of Windows 7 on the new SSd 160GB drive I installed EasyBCD to see if we could get access to the old Ubuntu installation...sure enough after adding it to EasyBCD I could boot into karmic koala....

I did an upgrade to 10.04 but had issues with OpenFOAM and did a fresh install of Ubuntu 11.04 and set up grub2 on the ssd drive...so I thought...I added a boot splash etc and used the grub customiser to clean up the entries...

When booting to Windows I forgot that EasyBCD was installed, so it went to a boot screen with Windows 7 and Ubuntu and then I could choose Windows 7......

Sorry, for long thread!!

I decided to remove the entry for Ubuntu in EasyBCD, so that when choosing Windows 7 from grub2 it went straight into Windows 7....


NADA!
EasyBCD came up fault and couldn't load windows bootmgr...I thought this is strange...and tried Bcdedit...nada couldn't load it....

I tried everything...fixmbr, fixboot, rebuildBCD (didn't work)...

I had almost given up when I decided to boot into Ubuntu livecd to check partition layout in gparted.....

It wasn't so strange that I couldn't fix the bootmgr...my windows 100mb partition had been wiped?! I am certain in my attempts to reinstate the bootmgr that I didn't remove the partition...

Anyway, I added it again and formated it to ntfs and rebooted to repair cd for Windows and fixed the bootmgr without problems.....

Now we are up to date....LOL:P

I now am going to fix grub2 but was wondering for safety sake where I should install grub2 so that it doesn't mess up my Windows 100mb partition?

I am out of date regarding grub2 and with my dualboot set up on two drives...don't know where it would be best to have grub2 installed?

Really sorry for all the waffle...just wanted to give a complete picture....

meharts

---

### Post by Quackers on 2011-08-13
Grub will not damage a Windows partition unless you install grub to that partition. This should not be done.
It is normal to install grub to the mbr of a drive - not to a partition. Which drive you install it to is up to you. If your Windows drive is currently the first bootable drive in your bios you can install grub there, but it will over-write the Windows bootloader.
Alternatively you can install grub to the mbr of the 1TB drive then change your bios so that the 1TB drive boots before the ssd. Grub will then boot both systems from the grub menu.

---

### Post by meharts on 2011-08-14
Hi Quackers:D

OK! thanks for that...kind of understood that and wanted a little confirmation...

Just realised my problems...Windows 7 was installed on the original 1TB drive and I hadn't wiped that info...Doh!

I didn't realise that I was repairing the partition on the 1TB drive....help!!

I didn't have the bios set up right either....

Just a thought...having a fast ssd drive for Windows only...was thinking it would be a good idea to have the swap on that drive....?


meharts

---

### Post by raja.genupula on 2011-08-14
> **Quackers said:**
> Grub will not damage a Windows partition unless you install grub to that partition. This should not be done.
It is normal to install grub to the mbr of a drive - not to a partition. Which drive you install it to is up to you. If your Windows drive is currently the first bootable drive in your bios you can install grub there, but it will over-write the Windows bootloader.
Alternatively you can install grub to the mbr of the 1TB drive then change your bios so that the 1TB drive boots before the ssd. Grub will then boot both systems from the grub menu.

hey 
what if we place same grub in both hard disks . he said he had windows in 1TB . so without externals normal ubuntu will do its job . if 1tb connected then same grub we have so no issues .
what do you say ?

---

### Post by meharts on 2011-08-14
Hi raja.genupula:)

The Windows7 on the 1TB was from the old installation and will be removed as soon as I back up the info there...

I was confusing myself after doing a new install of Windows 7 on the ssd drive I forgot to remove windows from the 1TB drive....

I will keep probably keep the bootloaders separate from each other in case of issues in the future....


Ubuntu 11.04 will be on the 1TB drive and I will probably install the boot loader to the root of that drive and set it in bios...


meharts

---

### Post by Duncan Williams on 2011-08-14
I might have got something wrong here but.
The whole idea of hving an ssd drive is to give optimum speed to boot and operating system. (thats why I am getting a new motherboard with built in 20 gig ssd)  so...
If it was me I would want (in your case)
Windows 7, ubuntu, grub, and my swap files on the ssd.
You have heaps of room for that...
Then use the 1tb drive for applications and general storage/backup of all other files.
I would also make sure that all caches, etc were nominated to the ssd drive.
How would I do that here?
Install windows 7 on ssd, then install ubuntu as dual boot, after I had it all up and working do full updates for windows and ubuntu, then start installing all other apps and data (mp3's videos, photos, docs, etc) onto the 1 tb drive.
After all that make complete backup onto a partition on the 1 tb drive.

---

### Post by raja.genupula on 2011-08-14
> **meharts said:**
> Hi raja.genupula:)

The Windows7 on the 1TB was from the old installation and will be removed as soon as I back up the info there...

I was confusing myself after doing a new install of Windows 7 on the ssd drive I forgot to remove windows from the 1TB drive....

I will keep probably keep the bootloaders separate from each other in case of issues in the future....


Ubuntu 11.04 will be on the 1TB drive and I will probably install the boot loader to the root of that drive and set it in bios...


meharts

what ever man , maintain same grub will be fine but your problem will be solved in a simple way if you have ubuntu in internal harddisk . ok now what i am thinking is ok say one thing are you able to boot to your ubuntu now ?

---

### Post by meharts on 2011-08-14
Hi Duncan Williams:D

You have a good point there.....;)

I have never installed apps on anything but the C: drive, but as you say, in this case it would be prudent to get max speed from both distros..

Going to look at shrinking the Windows partition to make rome for ubuntu....

and as then create home partition on 1TB as well as partition for Windows apps and user account...

Trying to save some time on this...obviously I will be able to shrink the windows partition easier with gparted...windows is a bit tight when shrinking partitions....:(

Thanks for the info...made me think again...LOL

meharts

---

### Post by meharts on 2011-08-14
Hi raja.genupula!

Sorr, just noticed your post....going to look again at moving ubuntu to ssd drive for speed....

Will post when done to let you know how it goes...

Thanks for your time!

meharts

---

### Post by meharts on 2011-08-14
Hi again!
Just noticed an even bigger cockup on my part....LOL

ssd drive is 120GB and not 160GB

meharts

---

### Post by Duncan Williams on 2011-08-14
still heaps of room if done correctly.
Theres a hell of a lot of dual boot with win7 out there on say an 80gig hd.

---

### Post by meharts on 2011-08-14
Hi Duncan Williams!

Thanks for the info!

I have removed all programs from install and cleaned up the drive and shrunk it now for ubuntu...

Got an emergency job come in...will report back when complete!

Thanks again!

meharts

---

### Post by meharts on 2011-08-17
Hi Duncan Williams:D

OK!I have fixed Ubuntu on the ssd drive now!
I have swap and / on ssd and /home on the 1TB drive. I installed grub2 to the 1TB drive and set the drive in the bios...

All well apart from the login font size which I am trying to sort out in another thread.

Thanks for your help on this!

meharts

---

### Post by Duncan Williams on 2011-08-17
I am glad you ended up getting things how you wanted them. good luck and all the best.

---

