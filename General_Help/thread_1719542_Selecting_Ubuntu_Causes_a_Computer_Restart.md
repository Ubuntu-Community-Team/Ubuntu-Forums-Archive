---
title: "Selecting Ubuntu Causes a Computer Restart"
date: 2011-04-01
forum: General Help
---

### Post by bellsworth46 on 2011-04-01
I have Ubuntu installed on a dual boot with Windows XP. I haven't used Ubuntu for a while and when I tried to start it up, my screen went black and my computer restarted. No error messages or dos lines. I tried a few times and the same thing occurred. Any ideas on how to fix this would be great. I do not want to loose my documents on it if at all possible. 


P. S. Because I haven't ran it in quite a while, I have not updated Ubuntu for some time.

---

### Post by ApocryphalAuthor on 2011-04-02
What are all of the options that your GRUB bootloader have?  Which one are you selecting when you boot?  Is there a safe or recovery mode?

---

### Post by Rubi1200 on 2011-04-02
Hi and welcome to the forums bellsworth46 :)

Is this a Wubi install or regular to a partition on the drive?

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by bellsworth46 on 2011-04-02
@ApocryphalAuthor:  I don't even get to the grub selections. I get to the screen to choose a partition and it restarts after selecting the Ubuntu one.

@Rubi1200: It was a Wubi install, so I do not have a live CD/USB to run Ubuntu off of.

---

### Post by Rubi1200 on 2011-04-02
Okay, I understand.

However, in order to fix this you will need an Ubuntu CD.

Here is the link:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Further down the page you will find instructions on how to burn the image to CD and run it as a live CD.

Of course, all this can also be achieved with a USB stick, in which case I recommend using UNetbootin:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

If all this seems too much, you can use [ext2read]("http://ext2read.blogspot.com/") to recover any important data from the Ubuntu root.disk.

Then, remove Wubi using Add/Remove in Windows and reinstall or do a proper install on a partition of the drive.

Let us know if you need more help or have other questions.

---

### Post by Razmear on 2011-04-02
> **bellsworth46 said:**
> 


P. S. Because I haven't ran it in quite a while, I have not updated Ubuntu for some time.

Have you changed the drive setup since you ran it last? Added any new drives or changed a master to slave? 

I had the same issue when adding a new drive on a dual boot system, Grub was looking for hd1 which had just become hd0 and it caused the same symptoms.

eb

---

### Post by bellsworth46 on 2011-04-02
> **Razmear said:**
> Have you changed the drive setup since you ran it last? Added any new drives or changed a master to slave? 

I had the same issue when adding a new drive on a dual boot system, Grub was looking for hd1 which had just become hd0 and it caused the same symptoms.

eb

I recently got a portable USB hard drive that I have connected to my computer on occasion. Could that have caused it perhaps? I haven't run Ubuntu since I got the hard drive.

---

### Post by bellsworth46 on 2011-04-02
@Rubi1200

I made a live CD, but when I tried to run it, this message came up:

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on filesystem.squashfs

Any ideas?

---

### Post by Rubi1200 on 2011-04-03
Hi,

not sure if adding a USB drive would cause this. I still suspect this is a Wubi issue.

Another thing you can try is running chkdsk in Windows and then boot back to see if Ubuntu will start:
[http://support.microsoft.com/kb/315265](http://support.microsoft.com/kb/315265)

Regarding the CD, that sounds like either a bad burn or a corrupted image.

Check the integrity:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Burn at the lowest possible speed for best results:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

