---
title: "Windows on the second hard drive?"
date: 2009-09-10
forum: General Help
---

### Post by Screatch on 2009-09-10
I have 2 hard drives connected to my computer, on the first one i have installed Linux Mint Gloria,  and the second i use for all sort of stuff like downloads and other. I am thinking of formatting the second hard drive for Windows 7, so many cool games are coming out and i want to try them out. I tried looking for the manual in the google but it gave me not exactly what i need. Let's skip the part where i install Windows on 2nd HD, what do i need to add to GRUB boot loader so the Windows would be an Option to launch.

---

### Post by longtom on 2009-09-10
> **Screatch said:**
> I have 2 hard drives connected to my computer, on the first one i have installed Linux Mint Gloria,  and the second i use for all sort of stuff like downloads and other. I am thinking of formatting the second hard drive for Windows 7, so many cool games are coming out and i want to try them out. I tried looking for the manual in the google but it gave me not exactly what i need. Let's skip the part where i install Windows on 2nd HD, what do i need to add to GRUB boot loader so the Windows would be an Option to launch.

Windows will grab the MBR no doubt. You will have to reinstall grub indeed.  There are loads of guides on the I-net or in this forum.  You'll find them.

---

### Post by s1mple_M4N on 2009-09-10
I had a similar set-up when I started out with Ubuntu. Try these threads - they helped me a lot.

[http://ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings](http://ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings)

[http://ubuntuforums.org/showthread.php?p=677880#post677880](http://ubuntuforums.org/showthread.php?p=677880#post677880)

RoyJ

---

### Post by Screatch on 2009-09-10
Everything looks a little bit complicated and i am kinda lost..
Look, i got 2 hard drives, /dev/sda/ where is Ubuntu and is my main OS, and /dev/sdb/ where i am planning to set Windows, if i understood well, when i install Windows, it replaces grub-loader with linux loader, what do i need to do to return linux-loader and add a line to choose launching from /dev/sdb?

---

### Post by Screatch on 2009-09-10
Can anyone please write a small manual from me? Pleease :(...
There is hardly i undarstand in those articles, everything sounded so complicated and i feel lost..

---

### Post by nikhilbhardwaj on 2009-09-10
a simpler solution is 
plug out your ubuntu hard drive
and install windows on your second harddrive
after completing the windows installation
power off your computer and plug in the ubuntu drive
boot into ubuntu and add a grub entry for windows 
and thats it

---

### Post by Screatch on 2009-09-10
Any other solutions, without plugging out and in?

---

### Post by confused57 on 2009-09-10
> **Screatch said:**
> Any other solutions, without plugging out and in?
The safest solution would be to unplug your Ubuntu drive, but if you decide not to do this, then I would advise you to backup your important data...partitioning & installing OSes can in rare instances cause you to lose data.

Here is how I would do it if it were my system:
1.) Make a ntfs partition on your 2nd hard drive for installing Windows 7 to, make it a primary partition preferably at the beginning of the drive.
2.) Before you boot the Windows 7 install DVD, set your bios to boot first to the drive you're installing it to.
3.) During the installation of Windows 7, reformat the ntfs partition you made previously, then install Windows 7.
4.) Windows 7 "should" install it's bootloader to the mbr of your 2nd hard drive, but if it doesn't you can reinstall grub to the 1st hard drive's mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
then you can add an entry to grub to boot Win 7, which we can show you after you have Win 7 installed.

Note:  If you don't pre-format an ntfs partition, Win 7 may automatically make a 100 Mb fat partition to install bootloader files to...this has been my experience.

---

### Post by nikhilbhardwaj on 2009-09-10
i think that you've never opened your computer
its really a lot easier than you think it'll be
but confused57's method is perfectly fine too

if that overwrites your mbr then you'll find it a little tricky to get grub back
atleast i did 
only the first time though

best of luck

PS: DO BACK UP IMPORTANT DATA BEFORE YOU PROCEED

---

### Post by Screatch on 2009-09-11
I decided to try out turning off one drive while installing another OS, but i have a small questions, when i finish installation i will have to add to menu.lst something like this

> title		Microsoft Windows 7
root		(hd0,1)
savedefault
makeactive
chainloader	+1
But how does sustem know, on which hard drive to search Microsoft Windows 7? How do i tell him he should do searches on /dev/sdb?

---

### Post by longtom on 2009-09-11
> **Screatch said:**
> I decided to try out turning off one drive while installing another OS, but i have a small questions, when i finish installation i will have to add to menu.lst something like this


But how does sustem know, on which hard drive to search Microsoft Windows 7? How do i tell him he should do searches on /dev/sdb?

Mine looks like this:

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Microsoft Windows XP Professional
root		(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

I am not a grub expert at all - but that might give you a clue where to go.

---

### Post by Screatch on 2009-09-11
Is yours installed on the same hard drive or second?

I still don't get it how the system will know what hard drive is Windows on?

---

### Post by 73ckn797 on 2009-09-11
> **Screatch said:**
> Is yours installed on the same hard drive or second?

I still don't get it how the system will know what hard drive is Windows on?


The grub entry given by "longtom" will tell the system where to find Windows 7.

If Win7 is on the second drive then "(hd1,0)" is the location. Being that the first hard drive will be listed as "hd0" and the second as "hd1". The numbering of drives begins with "0" and counts up from there.

---

### Post by Screatch on 2009-09-11
Done what i wanted to..
Installed Window on the second hard drive and made a grub entry.
Tried the unplugging method.

Everything works perfectly, thanks.

---

### Post by nikhilbhardwaj on 2009-09-11
```

rootnoverify (hd1,0)
and not root (hd0,1)

```

hd0 means your first hard disk
and hd1 means the second disk
thats how grub knows where to search

---

### Post by 73ckn797 on 2009-09-12
> **nikhilbhardwaj said:**
> ```

rootnoverify (hd1,0)
and not root (hd0,1)

```hd0 means your first hard disk
and hd1 means the second disk
thats how grub knows where to search


ibid!

---

