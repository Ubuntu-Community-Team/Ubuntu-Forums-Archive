---
title: "error: no such partition. grub rescue&gt; PLEASE HELP!"
date: 2011-06-15
forum: General Help
---

### Post by dandandrums on 2011-06-15
okay, so heres what i done and why i need help.

i was given a Windows XP machine, dualbooted it with Ubuntu and all was good. I removed Windows XP by doing a fresh install of Ubuntu so Ubuntu was the only operating system on the hard drive, all was good.

I then dual booted with Elementary OS, after some time i became bored of the OS (as happens sometimes) so i deleted the partition. rebooted the computer. UH OH, NO SUCH PARTITION!

at this time i gathered i must've corrupted the bootloader (which i believe was grub) hence grub rescue appearing.

after using the command "ls" the drives (hd0) and (hdo,msdos1) came up, i assume this is the partitions on the drive (but i'm not sure which partitions they are, or whats on them). i then typed "help" to see if the normal module was there, it came back as an error, leading me to thing it isn't.

i attempted to use a Live CD to simply install Ubuntu only again and never to touch OS's or dualboots or anything again, but the Live CD couldn't even "see" the hard drive, making me thing the partitions are unreadable. i then took the hard drive out, put it into a USB Disk Caddy thing and on a windows machine it found the caddy but didn't see the drive.

so, no LiveCD solutions, not sure what to type into grub rescue BUT the only thing i'm glad about is that i had everything backed up.

does anyone have a solution? i'd be very grateful.

---

### Post by prodigy_ on 2011-06-15
> **dandandrums said:**
> the Live CD couldn't even "see" the hard drive, making me thing the partitions are unreadable. i then took the hard drive out, put it into a USB Disk Caddy thing and on a windows machine it found the caddy but didn't see the drive.
Looks like a hardware issue to me. Check BIOS. If the HDD in question isn't listed there then most probably it's dead.

---

### Post by oldfred on 2011-06-15
If you get grub rescue or grub> it would seem drive is working. It would be normal that windows would not see it as it cannot see Linux partitions.
But the liveCD should have seen drive & partitions. Your MBR probably had the grub from your Elementary OS, not Ubuntu. So that would be why it cannot boot now.

Try running this from liveCD:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Some tools to repair boot loaders if you do not want to manually do it:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)
[http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk](http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk)
Howto: Easy GRUB Bootloader Repair Windows,unetbootin, Supergrub 2008
[http://ubuntuforums.org/showthread.php?t=690912](http://ubuntuforums.org/showthread.php?t=690912)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by dandandrums on 2011-06-15
the HDD comes up in Bios, so i will try your solution, thanks very much. i will post back when i can.

---

### Post by dandandrums on 2011-06-16
I have decided to get a 1TB external hard drive, install ubuntu on it, use that to "see" the partions, wipe it clean, install ubuntu to that, then wipe the external hard drive for use as storage, will this work?

much thanks for all help :)

---

### Post by oldfred on 2011-06-16
You need to use manual install, so you get the choice to install grub2's boot loader to the MBR of the external. Otherwise it just defaults to the sda drive.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by dandandrums on 2011-06-16
thanks for that, will let you know how i get on, the external hard drives arrives on saturday so should have a reply on here on sunday letting you if success or not.

thanks again, this is why i love the ubuntu community!

---

### Post by dandandrums on 2011-06-21
got the external hard drive, ensured the bios pointed at the DVD drive to boot off first, booted up the LiveCD, actually managed to get to the install point, got cheeky and actually reformatted the internal harddrive and installed ubuntu there and then.

internal hard drive works and i now have a terabyte to play with and store everything.

thanks for all the help, i very much appreciate everything :)

---

### Post by Brushstroke on 2011-06-21
For future reference dandandrums, if you ever get a "grub rescue" prompt again you can just reinstall grub to the Master Boot Record of the hard drive from the Live CD. That probably would have done the trick.

---

### Post by dandandrums on 2011-06-24
i had tried doing that, the livecd would simply crash and couldn't read the partitions. after i got the external hard drive, i then managed to get the livecd to function.

---

