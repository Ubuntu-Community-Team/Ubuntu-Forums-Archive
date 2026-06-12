---
title: "Editing the grub"
date: 2010-09-12
forum: General Help
---

### Post by Snitz on 2010-09-12
I have finally installed ubuntu 10.4 alongside windows 7.
However, the grub doesn't show windows 7 so I can't boot into it.

Attached is a screenshot of "gparted". Windows 7 is installed on "sda2" and Ubuntu is on "sda6". How do I edit the grub to be able to load into windows 7?

And I faced another problem after installation. The pc kept freezing, I couldn't enter ubuntu nor use the live version on my usb stick. It kept freezing.

EDIT: I restarted and it froze again. I had to restart at least  times before it allowed me into ubuntu. I'm wondering if it's a hard-disk issue since it's giving me a hard disk error whenever I login. Even though I've been running windows 7 for the past 9 months without any problem.

---

### Post by Lukas666 on 2010-09-12
I had problems with Lucid and Windows 7. I think grub does not interact with Windows7 well.

This helped:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by oldfred on 2010-09-12
I see swap in sda1 which was your /boot  & recovery (hidden) partition for win7. You will have to use a windows 7 repair CD to reinstall the missing boot & bcd files. Windows repairs of the install with the separate boot partition do not seem to repair the boot partition but will repair the main install. Your swap also is too small if it is only the 100MB.

Grub will only boot windows that works as it just transfers the boot to the windows boot sector to continue booting.

[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)

Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by Snitz on 2010-09-13
Thank you for the detailed response.
I got the win7 repair cd, the problem is it wouldn't boot.
I'm trying to fix that or get another cd and try again.

That was my final act, to fix the mbr through win7 cd.
I'll try it and see what happens.

---

### Post by oldfred on 2010-09-13
Windows repair is probably trying to repair a windows install where the boot flag is, but that is swap and windows cannot read a swap partition. If you move boot flag to sda2 it may then work.

You can set boot flag with gparted, Disk Utility or command line.

set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda
Some bios refuse to boot a hard drive without a boot flag. Although linux does not need one.
More precisely: Some Bios require a boot flag on a primary partition.

---

### Post by Snitz on 2010-09-13
I booted from windows 7's dvd, went to the prompt command.
I followed your steps, /fix mbr and chkdsk c: (it took 3 hours)
When I reached step 3, the command didn't work and it kept giving me options and recognized commands. so I had to abort this and restart but I was still facing the same problem.

The problem is bigger than I thought.

When I booted back into win7 command prompt, I tried this command:

```
bootsect /nt60 c:\ 
```

Apparently C: is missing and all the other drives as well.
This is the error it gave me.

```
Target volumes will be updated with BOOTMGR compatible bootcode.
Could not map drive c: to an associated volume device object.
```

So I don't know what to do now with all drives missing in windows 7 and in ubuntu as well, nothing shows on gparted other than 1 unallocated partition 1.91GB.

Please advise.

---

### Post by oldfred on 2010-09-13
Windows 7 will not see anything but NTFS/Fat partitions, so that does not mean anything about Ubuntu. 

Try running the boot script:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by Snitz on 2010-09-14
I have the results attached below.

Note that I am on ubuntu now and I can't access windows from the boot loader. I just need to add windows 7 to it.

---

### Post by philinux on 2010-09-14
Snitz,

Open a terminal and run this.

```
sudo update-grub
```

See if it picks up the windows bootloader.

---

### Post by Snitz on 2010-09-14
> **philinux said:**
> Snitz,

Open a terminal and run this.

```
sudo update-grub
```

See if it picks up the windows bootloader.
Nope, that didn't do anything. :(

---

### Post by coffeecat on 2010-09-14
People helping on this thread, might like to be aware of this concurrent thread:

[http://ubuntuforums.org/showthread.php?t=1573998](http://ubuntuforums.org/showthread.php?t=1573998)

The OP also has an intermittent hardware fault which I don't believe has been resolved.

---

### Post by oldfred on 2010-09-14
The osprober almost always finds windows so I am surprised it did not find it. The only thing I see in your results.txt is that you still have a menu.lst even though you are booting with grub2 and grub.cfg.

I would delete (or rename menu.lst to menu.lst.old) and add this stanza to 40_custom, then run sudo update-grub to add it to grub.cfg.

menuentry "Windows 7 (loader) (on /dev/sda2)" {
insmod ntfs
set root=(hd0,2)
chainloader +1
}

gksudo gedit /etc/grub.d/40_custom

after all changes:
sudo update-grub

---

