---
title: "Stuck in Grub command line First Boot"
date: 2012-05-29
forum: General Help
---

### Post by RonanZer0 on 2012-05-29
I just got wubi and installed Ubuntu and when I booted it up for the very first time, I somehow got a grub cmd thing... I have no idea why I am here, obviously I couldnt update because I NEVER was able to make it into the desktop...Also trying with XUbuntu now! Same problem...when I try to use a fix
> # Add the ntfs module
**[COLOR=Navy]insmod ntfs[/COLOR]**
# Set root (normally would be sda1, or hd0,1  Change as necessary
[B][COLOR=Navy]set root=(hd0,1)
loopback loop0 /ubuntu/disks/root.disk[/COLOR][/B]
# Yes, set root for a second time. I don't know why...
**[COLOR=Navy]set root=(loop0)[/COLOR]**
# Set the kernel. You can (and should) use Tab (twice) to complete  entries such as the kernel when possible - type vml and then TAB twice  and it will autocomplete to the point where there are two possibilities.  Tab complete ensures the path/file names as typed exist. Additionally,  if you suspect the new kernel is the problem, you might want to select  an earlier one. vmlinuz.... should be a complete kernel entry such as  "vmlinuz-2.6.31-15-generic-pae" *
**[COLOR=Navy]linux /boot/vmlinuz.... root=/dev/sda1  loop=/ubuntu/disks/root.disk ro[/COLOR]**
# Set the initrd image - complete or tab to get the full name  Example: "/boot/initrd.img-2.6.31-15-generic-pae"
[COLOR=Navy]**initrd /boot/initrd/initrd.img... **[/COLOR]
[B]# Boot.
[COLOR=Navy]boot[/COLOR][/B]                                 I tried that and on the line linux /boot/vmlinuz.... root=/dev/sda1 loop=/ubuntu/disks/root.disk ro

Well...It told me unknown file system! Please help I really want to use Ubuntu with XUbuntu desktop environment!! Also using Windows 7 64 Bit ;) (I have modified the boot screen of Windows and the startup sound, could this be a problem? probably not, just saying incase though, And I can boot into windows just fine)

---

### Post by RonanZer0 on 2012-05-29
Bump... I want to use Ubuntu so bad I use ubuntu theme for win7 lol...NEVER REPLACING WINDOWS THO...

---

### Post by wilee-nilee on 2012-05-29
> **RonanZer0 said:**
> Bump... I want to use Ubuntu so bad I use ubuntu theme for win7 lol...NEVER REPLACING WINDOWS THO...

Post a link to this thread here.

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

There are only a couple of helpers for wubi installs.

In the future make sure you mention Wubi in the thread header if it is associated with wubi to get their attention. ;)

---

### Post by RonanZer0 on 2012-05-29
I dont know very much about Ubuntu and all that crazy stuff and I just looked at that thread i dunno what sda's are and other stuff so I cant tell whats my problem and I have a root.disk in my Ubuntu Disks directory

---

### Post by wilee-nilee on 2012-05-29
> **RonanZer0 said:**
> I dont know very much about Ubuntu and all that crazy stuff and I just looked at that thread i dunno what sda's are and other stuff so I cant tell whats my problem and I have a root.disk in my Ubuntu Disks directory

Yes, but read my last message carefully it is to get you help.

I did not send you there but to post a reference to this thread.

Without a [COLOR=Red]BIG RED WUBI FLAG[/COLOR], you're likely to not get helped.

---

### Post by wilee-nilee on 2012-05-29
All you need to do is go to that thread and post a reply like I have a problem with my wubi set up, my thread is here, and give this threads HTTP address. :)

Cool the thread header was modified, the helper is on daily and will see your thread.

---

### Post by bcbc on 2012-05-29
If you go straight to a grub prompt it probably cannot see the root.disk.

Enter:
```
search -s -f -n /ubuntu/disks/root.disk
echo $root
```

If it comes up with nothing then... not sure. If you installed on an external drive, it only works if the BIOS can see it. To see what the BIOS sees enter (lower case LS):
```
ls
```

You'll see drives as (hd0), (hd1) (sometimes ('/dev/sda')). And partitions as (hd0,1) (sometimes (hd0,msdos1) or ('/dev/sda',msdos1)).

You can examine the contents of the partitions. The following will list the root contents on the first partition:
```
ls (hd0,1)/
```

But maybe the best thing would be to boot an Ubuntu CD and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") so we can see if there is something that might explain this. (Note that link isn't completely accurate on how to run the bootinfoscript anymore - I think it's 'sudo bash bootinfoscript' to run it now).

---

### Post by RonanZer0 on 2012-06-07
i tried that doesent work and i dont want to boot from cd BECAUSE I DONT HAVE A BLANK CD and my dad wont buy me a blank cd or ubuntu disc cause I already have windows :( but i have usb

---

### Post by wilee-nilee on 2012-06-07
> **RonanZer0 said:**
> i tried that doesent work and i dont want to  boot from cd BECAUSE I DONT HAVE A BLANK CD and my dad wont buy me a  blank cd or ubuntu disc cause I already have windows :sad: but i have usb

Download the ubuntu release use unetbootin to load it to the usb, and boot it and follow the instructions.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

run this command once you are on the live cd, the results.txt will be in the home and copy and paste all the text to a reply.
```

wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript
```

---

