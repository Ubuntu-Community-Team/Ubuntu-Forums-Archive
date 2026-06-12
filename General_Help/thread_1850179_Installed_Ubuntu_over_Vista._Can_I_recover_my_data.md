---
title: "Installed Ubuntu over Vista. Can I recover my data?"
date: 2011-09-26
forum: General Help
---

### Post by lilnaka on 2011-09-26
Hi everyone i need help my windows VISTA i don't know what happened but it wasnt booting so i gave it to a friend they installed UBUNTU and they said i can access my vista files from ubuntu since he installed this ubuntu i cannot find my vista files anywhere, teh are very important files and pics on my vista and i really need to get access to them can anyone help me out please and tell me how i can get hold of my vista files.
 
im not a computer wizz so please be patient with me.
 
im gonna be very mad at my friend if i have lost everything that was on my vista 
 
thanks in advance

---

### Post by Megaptera on 2011-09-26
When you boot up on starting up the machine, do you get a choice of operating systems - Ubuntu and Vista?

---

### Post by lilnaka on 2011-09-26
> **Megaptera said:**
> When you boot up on starting up the machine, do you get a choice of operating systems - Ubuntu and Vista?
 
 
No it loads str8 to ubuntu its like my computer was never vista before ubuntu was installed my laptop wasnt booting right it would load to a blank screen with just the cursor.

---

### Post by Megaptera on 2011-09-26
This is a link to a "script" that'll produce a log that'll show people here what's on your hard drive. Please post the results here, the instructions are step by step:

Quote "boot_info_script is a bash script which searches all hard drives attached to the computer for information related to booting and displays it in a convenient format. Its primary use is for troubleshooting booting problems."

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by lightwarrior on 2011-09-26
First you need to protect your files, so do not install anything on your computer hard disk drive (HDD).
Now, to boot ubuntu, just get the downloadable Ubunutu Live CD .iso file image and burn it to a CD with a software capable of managing .iso files.
Insert CD into your machine and when booting, select DC/DVD tray as boot media.
When Ubuntu LIVE boots, you will be able to "navigate" into your hard drive... you will see the usual C:/ tree directory, including windows and your user files (pics, music, programs).
Insert a USB HDD or flash to copy files from your vista HDD to USB device.

---

### Post by elliotn on 2011-09-26
do u see any NTFS partition in your Ubuntu.? if u see the drive just click on it and open its files u will c windows files. navigate to the folder with all your staff

---

### Post by lilnaka on 2011-09-26
ok iv tried everything you all have said and i get lost its so frustrating would it be best to take it to an actual I.T tech??
 
am i guranteed to get all my files back? documents, pics music movies etc
 
Now my laptop screen is really dark like its hard to see : i dont have much luck with laptops god damnit lol

---

### Post by nothingspecial on 2011-09-26
The best thing to do would be to run the boot info script posted above.

Failing that, boot into Ubuntu

Open a terminal (Ctrl-Alt-T)

Then copy and paste this

```
sudo fdisk -l
```

Then post what it says back here.

---

### Post by lilnaka on 2011-09-26
> **nothingspecial said:**
> The best thing to do would be to run the boot info script posted above.

Failing that, boot into Ubuntu

Open a terminal (Ctrl-Alt-T)

Then copy and paste this

```
sudo fdisk -l
```Then post what it says back here.


Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track


did i do it right thats what came up.

---

### Post by nothingspecial on 2011-09-26
Hi, I think you maybe typed -1 instead of -l

It is a lowercase L

Not a number one.

---

### Post by lilnaka on 2011-09-26
> **nothingspecial said:**
> Hi, I think you maybe typed -1 instead of -l

It is a lowercase L

Not a number one.

LOL sorry on the other laptop it looked like a "1" lol

it wasnt letting me type my password but this is what came up

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000533fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37832   303880192   83  Linux
/dev/sda2           37832       38914     8688641    5  Extended
/dev/sda5           37832       38914     8688640   82  Linux swap / Solaris

---

### Post by nothingspecial on 2011-09-26
> **lilnaka said:**
> LOL sorry on the other laptop it looked like a "1" lol

it wasnt letting me type my password but this is what came up

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000533fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37832   303880192   83  Linux
/dev/sda2           37832       38914     8688641    5  Extended
/dev/sda5           37832       38914     8688640   82  Linux swap / Solaris

If you only have one hard drive in your laptop, and you have posted the entire output, then I'm sorry to be the one to tell you but Vista is gone :(

You may be able to recover some files if you take it to a data recovery specialist but that would cost a lot of money.

I would be very mad if my friend had done this.

---

### Post by lilnaka on 2011-09-26
> **nothingspecial said:**
> If you only have one hard drive in your laptop, and you have posted the entire output, then I'm sorry to be the one to tell you but Vista is gone :(

You may be able to recover some files if you take it to a data recovery specialist but that would cost a lot of money.

I would be very mad if my friend had done this.


OMG are you serious?? iv lost everything damnit what would be best to do just re-install vista or am i stuck with ubuntu?

---

### Post by nothingspecial on 2011-09-26
Check your friend hasn't copied your stuff across.

Is there anything in our Music, Documents, Videos folders?

As for what to do after this, that's up to you. Either install Vista or try Ubuntu for a while.

I'd also have a word with your friend before you do anything. Did s/he make a backup first?

---

### Post by lilnaka on 2011-09-26
yeh i was just on the phone to him had a big argument, he said he didnt back it up.

i looked in the ubuntu folders music  etc and theres nothing completely empty i cant belive this if anything i really just wanted to pics on there of my daughter that will teach for not backing it up before so. :(

is it possible at all to get my files back or are they completely gone for good?

---

### Post by nothingspecial on 2011-09-26
I would say they are gone.

But I'm not a recovery expert. I'll change the title of your thread so that someone who is has a chance of seeing it.

---

### Post by lilnaka on 2011-09-26
what would i change the title to?? so sorry if im being a pain and askin 100 questions its horrible knowing iv lost everything

Just relised you changeed it thank you :)

---

### Post by Mark Phelps on 2011-09-26
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, my suggestions are the following (based on my experience at doing this successfully):
1) Find someone with a working Windows PC
2) Remove your drive from this PC.
3) On the Windows PC, download and install the trial version of GetDataBack for NTFS from Runtime Software.
4) Connect your old drive to this Windows PC.
5) Run GetDataBack in deepest discovery mode -- probably best to let it run overnight.
6) In the morning, check the recovery logs and see if GetDataBack was able to find your lost files.
7) If it was, you will have to purchase it to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, BTW, it is not HUNDREDS of dollars for this product. Last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---

### Post by lilnaka on 2011-09-26
> **Mark Phelps said:**
> In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.
 
Since your data was on a Windows partition, my suggestions are the following (based on my experience at doing this successfully):
1) Find someone with a working Windows PC
2) Remove your drive from this PC.
3) On the Windows PC, download and install the trial version of GetDataBack for NTFS from Runtime Software.
4) Connect your old drive to this Windows PC.
5) Run GetDataBack in deepest discovery mode -- probably best to let it run overnight.
6) In the morning, check the recovery logs and see if GetDataBack was able to find your lost files.
7) If it was, you will have to purchase it to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.
 
And, BTW, it is not HUNDREDS of dollars for this product. Last time I checked, GetDataBack for NTFS was $80, USD.
 
Your data ... your money ... your choice.
 
can i download it using ubuntu? and i have no idea how to set up the hard drive thats deleted vista with a working windows laptop its all abit techy lol but ill give it a try if so thanks
 
Or by any chave could i use a external usb hard drive in my laptop that im trying to recover man this is all so confusing lol

---

### Post by nothingspecial on 2011-09-27
Here is a good guide on some free recovery tools

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by fixerdave on 2011-09-27
> **lilnaka said:**
> yeh i was just on the phone to him had a big argument, he said he didnt back it up.

i looked in the ubuntu folders music  etc and theres nothing completely empty i cant belive this if anything i really just wanted to pics on there of my daughter that will teach for not backing it up before so. :(

is it possible at all to get my files back or are they completely gone for good?

If you just want the pictures, there is a chance... a CHANCE that you can pull them off the drive.  You need to do what's called "file carving" and you can do it under Linux.  There are lots of guides out there... I wrote one while trying to figure it out.  It's probably not the best, but it will describe the basic process... you can look up the details.  ( [http://datadave.blogspot.com/2008/08/data-recovery-with-ubuntu-linux-live-cd.html](http://datadave.blogspot.com/2008/08/data-recovery-with-ubuntu-linux-live-cd.html))

Pictures are easier to carve than most, mostly because they're easier to sort afterwards.  Also, Ubuntu will not use nearly as much drive space as Vista, so your data is probably on a part of the drive that didn't get overwritten.  There is a chance... but don't get your hopes up too much.  If I were in your place, I'd give it a shot though... if you've already written the pictures off, you don't have too much to lose, besides time.

---

### Post by Mark Phelps on 2011-09-28
> **lilnaka said:**
> can i download it using ubuntu? 
You can download it using anything you want -- but it's a Windows program and requires a Windows PC to run it.

> i have no idea how to set up the hard drive thats deleted vista with a working windows laptop its all abit techy lol but ill give it a try if so thanks
Laptop not the best choice, desktop would be better. 

Laptop will require you connect via USB -- which means you will have to acquire a SATA or IDE adapter with a USB cable on it.  You plug the drive into the proper SATA or IDE port on the adapter and plug the adapter into a USB port on your PC.

With a desktop, you would open the case and connect the hard drive to a cable and then to your motherboard.
 
> Or by any chave could i use a external usb hard drive in my laptop

If the drive you are recovering data FROM is in your Laptop, you will have to REMOVE it first.  You can't run from that drive and do file recovery.

Also, the more you use that drive, the lower the chance of being able to recovery ANYTHING from it as it is constantly overwriting the data that was there previously.

---

