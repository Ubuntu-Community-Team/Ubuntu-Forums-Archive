---
title: "GRUB Lost Option To Boot Into Ubuntun Natty"
date: 2011-05-28
forum: General Help
---

### Post by rykel on 2011-05-28
Hi, I installed Maverick alongside Windows 7. Then I upgraded Maverick to Natty, removed and reinstalled the latest kernel and ubuntu-desktop using Synaptic Package Manager. But now GRUB does NOT show any option to boot into Ubuntu Natty.

Please help me! Thank you.

---

### Post by sanderd17 on 2011-05-28
So what does GRUB show? only windows? or also maverik?

Normally, reinstalling GRUB should fix this, see this:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Rubi1200 on 2011-05-28
Let's see the results of the boot info script please so we have a better idea of what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by rykel on 2011-05-29
I used Karmic LiveCD and got a warning message... so here is the full results. Thank you!

[INDENT][B]$ sudo bash ~/Desktop/boot_info_script.sh

boot_info_script version: 0.60        [17 May 2011]

"gawk" could not be found, using "/usr/lib/initramfs-tools/bin/busybox awk" instead. This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/ubuntu/Desktop/".
[/B][/INDENT]


**RESULTS.TXT**

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8a048a04

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    76,099,904    76,099,842   7 NTFS / exFAT / HPFS
/dev/sda2          76,099,905   116,792,549    40,692,645   5 Extended
/dev/sda5          76,099,968   115,009,334    38,909,367  83 Linux
/dev/sda6         115,009,398   116,792,549     1,783,152  82 Linux swap / Solaris
/dev/sda4         116,792,550   117,210,239       417,690  88 Linux plaintext


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        586041A860418DA6                       ntfs       S3A2109D001
/dev/sda5        c6d864e8-d969-4c89-8022-caa557aa8516   ext4       
/dev/sda6        03f3a1e5-0c67-46d8-92b0-12a2095622c2   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /tmp/BootInfo0/sda1      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /media/c6d864e8-d969-4c89-8022-caa557aa8516 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sr0         /cdrom                   iso9660    (rw)


========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")

```

---

### Post by Rubi1200 on 2011-05-29
Unfortunately, we do not have the full results here. It might be a problem with the latest version of the script, but I am not sure.

Please follow the instructions again and when you are at the download page choose other versions and download the 055 version.

Run it as before and post the results please.

Thanks.

---

### Post by rykel on 2011-05-30
Guys I am sorry but I was SICK of this issue I simply formatted my Linux partition, reinstalled Karmic, and then upgraded sequentially back to Natty.

You guess what? Every single version of Ubuntu works - except Natty.

Natty's GRUB menu is OK, but the moment I select to boot into Linux, my system would go BLANK. If I tried to boot into Recovery instead, my system would go into an infinite loop. (exact same problems I had a week back)

This leads me to believe that Natty sucks, and that its GRUB would exhibit the same problem if I tried to remove any kernels at the moment.

When will Ubuntu Natty be patched??

---

### Post by sanderd17 on 2011-05-30
Natty won't get patched, you can try again in October.

I can understand you switching, Natty is not the best release they gave.

---

### Post by rykel on 2011-05-31
> **sanderd17 said:**
> Natty won't get patched, you can try again in October.

I can understand you switching, Natty is not the best release they gave.

Sad. Now Ubuntu feels like Windows - I am stuck with Windows XP (Maverick) and unable to upgrade further to Windows 7 (Natty) without paying a big price. Has all the talented devs left Canonical/Ubuntu?

What about Linux Mint? Is it possible to "upgrade" Ubuntu online to Linux Mint?

---

### Post by sanderd17 on 2011-05-31
You can't upgrade to linux mint, but the installation is about the same as Ubuntu and you can keep all settings (they are stored in your home directory, so if you copy your entire home, you have your files and settings). The only thing you have to do afterwards is installing the programs you need.

But Mint is in fact just Ubuntu with some enhancements, so you'll probably have the same problems. My family uses Mint, I upgraded them to Mint 11, but now I had to downgrade them again. The wireless connection only lasted for about 5 minutes after reboot, the boot speed was slow, the printer gave wrong colors and some other problems. In short, it was easier to put Mint 10 back on it than to repair it.

I don't think your comparison is right. First, Ubuntu doesn't cost money and you can upgrade or downgrade any time, without license. Second, I would compare 11.04 to vista instead of 7 :P Now we only have to hope that a better version arrives.

I have been using ubuntu for more than 3 years now, and I think the quality goes in a wave. The even years worked well for me, but the odd years gave problems. Maybe that's because the even years are the years in which they release an LTS.

---

### Post by drs305 on 2011-05-31
> **rykel said:**
> Natty's GRUB menu is OK, but the moment I select to boot into Linux, my system would go BLANK. If I tried to boot into Recovery instead, my system would go into an infinite loop. (exact same problems I had a week back)

Do you get to a black screen with a blinking cursor in the upper left corner? If so, it's probably a video driver issue and we may be able to get it sorted out.

---

### Post by Gert Hulselmans on 2011-05-31
@ rykel

Can you copy the grldr file that must be in the root dir on one of your partitions to your home directory?

Then run:
```
dd if="${HOME}/grldr" count=4 bs=128k 2>> /dev/null |  hexdump -v -e '/1 "%02x"' | grep -b -o  'b0021ace000000000000000000000000'
```If it produces any output, post  it.

Else, try:
```
dd if="${HOME}/grldr" count=4 bs=128k 2>> /dev/null |  hexdump -v -e '/1 "%02x"' | less
```(press 'q' to quit)

If this showed, you a lot of hexadecimal characters, try the following:
```
dd if="${HOME}/grldr" count=4 bs=128k 2>> /dev/null |  hexdump -v -e '/1 "%02x"' | grep -b -o '47524c4452'
```And post the  output.

---

