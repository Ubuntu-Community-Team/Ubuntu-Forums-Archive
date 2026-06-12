---
title: "very slow file transfer"
date: 2010-02-14
forum: General Help
---

### Post by unitedoceanic on 2010-02-14
hi,

i have a bit of a problem and it seems i am not alone, google gave me a lot of hits but no solution.

i'm running a dual-boot system on my laptop.

ubuntu 9.10 is installed on ext3
windows xp sp3 on ntfs
files are on another ntfs partition

if i want to copy a file (or folder) bigger than 250mb my laptop literally gives up until the file transfer is complete. opening up a terminal via keyboard shortcut gives my an idea how long a ice age can last.

this happens with ext3 to ext3; ext3 to fat32; ext3 to ntfs and ntfs to ntfs.

today i wanted to backup some files (12GB ~4k files) the first 4gb ran with 20MB/s (all open applications grayed out). after **2h** i came back to see that only 6GB where done.

this is a huge show stopper any help will be appreciated

thank you

---

### Post by Zaphod69 on 2010-02-20
I'm experiencing the same symptoms.

Similar setup as above - similar results.

File copy / move to or from NTFS is so slow - really frustrating!

Any assistance would be appreciated :)

Thanks

---

### Post by thebigob on 2010-02-20
Transferring very lager files is usually a slow process regardless of the operating system.

This is made even worse by doing so using a graphical user interface.

If you want to retain your desktop whilst doing a transfer I would suggest using the command line interface in a terminal. This will slow down your system but should no longer "grey you out" as mentioned.

To do this:

[LIST]
[*]open a terminal
[*]use the cp command eg (cp /media/usbdisk /home/user)
[/LIST]
cp being the copy command /media/usbdisk being the source and /home/user being the destination. You will need to change these to whatever you require.

The benefit of doing this is that the shell you create by opening the terminal does all the hard work so that your gnome session doesn't have to. 

Bear in mind though that the operation will still slow down your system.

If you want to see the files being transferred you can use the -v flag for verbose output. eg (cp -v /media/usbdisk /home/user)

For other useful information on this command type "man cp" in a terminal

Hope this helps :)

---

### Post by Silvertones on 2010-02-20
My setup is:
1. computer A is WUBI install
2. Computer B is Win XP that has an external drive for backup
Wireless network between A&B
I keep the email TB profiles on A upto date by copying back and forth from .thunderbird & host/... within A . This is quite quick & not a problem. If I now copy the profile to B external drive it takes 2 hours as opposed to 20 min if I do it in windows.

---

### Post by Zaphod69 on 2010-02-23
> **thebigob said:**
> Transferring very lager files is usually a slow process regardless of the operating system.

This is made even worse by doing so using a graphical user interface.

If you want to retain your desktop whilst doing a transfer I would suggest using the command line interface in a terminal. This will slow down your system but should no longer "grey you out" as mentioned.

To do this:

[LIST]
[*]open a terminal
[*]use the cp command eg (cp /media/usbdisk /home/user)
[/LIST]
cp being the copy command /media/usbdisk being the source and /home/user being the destination. You will need to change these to whatever you require.

The benefit of doing this is that the shell you create by opening the terminal does all the hard work so that your gnome session doesn't have to. 

Bear in mind though that the operation will still slow down your system.

If you want to see the files being transferred you can use the -v flag for verbose output. eg (cp -v /media/usbdisk /home/user)

For other useful information on this command type "man cp" in a terminal

Hope this helps :)

Thanks for that information - I'd not figured Gnome would take that much processing speed.

I'm using cp to copy approx 1gb of data to my NTFS partition now - it's really REALLY slow - approx 200kBps. Going to be an over night job.

Yet sometimes I reboot and it will copy at 8Mbps - can copy 1Gb in minutes rather than hours.

I just don't understand why?

Cheers

---

### Post by thebigob on 2010-03-15
Is this back up data or something you have to copy the whole amount every time. 

I do backups across my network (LAN) at about 3mb/s however I use a tool called rsync.

This basically checks if the file has been altered and copies it has else it just skips it. This saves hours!

---

