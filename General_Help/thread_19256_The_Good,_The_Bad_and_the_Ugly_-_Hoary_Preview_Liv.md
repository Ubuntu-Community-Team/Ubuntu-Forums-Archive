---
title: "The Good, The Bad and the Ugly - Hoary Preview Live"
date: 2005-03-11
forum: General Help
---

### Post by Tapeworm on 2005-03-11
Not being the patient type, I download the Hoary Preview Live ISO as soon as I saw the news of it's posting. Time to run some experiments to tide me over for the month left before Hoary is released officially.

Here is my 5-minute review of things that jumped out at me compared to the Warty Live CD.

The Good: My USB "memory stick" now works as a Plug-and-Play device.  :)   :-)  :-P In Warty Live, it was only recognized if connected at boot up. In Hoary, it works exactly as expected. Haven't tried disconnecting the device while it is being accessed, but that can go screwy on any OS...

The Bad: Existing hard drive partitions do not automount like they did in Warty Live. Was this a design decision or an oversight? In Warty Live, all 3 of my NTFS partitions appeared in the Computer / Disks menu and in /mnt. They are understandably Read-Only but at least I could see them. The Places / Computer menu in Hoary Live only has CD-ROM and filesystem and /mnt is empty. Can this be changed before the Warty Live release to put things back the way they were? 

The Ugly: Still no way of building a persistent home directory on removable media like my USB memory stick. There is a posting on how to do this in Warty-live, but things have changed and this really needs to be a no-brainer process. Not sure how Knoppix handles this... will research...

Otherwise things look great and Ubuntu is just getting better and better.

Tapeworm

---

### Post by furunculus on 2005-03-11
[QUOTE=Tapeworm]

The Bad: Existing hard drive partitions do not automount like they did in Warty Live. Was this a design decision or an oversight? In Warty Live, all 3 of my NTFS partitions appeared in the Computer / Disks menu and in /mnt. They are understandably Read-Only but at least I could see them. The Places / Computer menu in Hoary Live only has CD-ROM and filesystem and /mnt is empty. Can this be changed before the Warty Live release to put things back the way they were? 

[/QUOTE]
i would like to know an answer to this.

i am building a dual boot Win/Lin box in the near future, and i want to be able to access my books/music/vids from one drive regardless of which OS i am in. I am not a techie so a distro that auto-mounts NTFS partitions would be much appreciated.

---

### Post by Tapeworm on 2005-03-11
[QUOTE=furunculus]i would like to know an answer to this.

i am building a dual boot Win/Lin box in the near future, and i want to be able to access my books/music/vids from one drive regardless of which OS i am in. I am not a techie so a distro that auto-mounts NTFS partitions would be much appreciated.[/QUOTE]

If you are installing Ubuntu to your hard drive, you will have to edit the etc/fstab text file and then you will be able to see your existing partitions after a reboot. See the HOWTO forum for lots of information. It's not hard. You can do it. Plus you can't call yourself a "Real Linux User" until you've edited your first configuration file by hand. One thing to keep in mind is that Linux can only access NTFS partitions as READ-ONLY. If possible, you want to keep all of your "books/music/vids" on a FAT32 partition so it can be written to by both operating systems.

My problem is with the Live CD where you can't make any permanent changes to the etc/fstab file or any other part of the system.

Tapeworm

---

### Post by 303 on 2005-03-13
I agree about the mount issue. HOW ANNOYING! I'm a total n00b and I can't even get mount to work! I guess they go hand-in-hand, eh?
What I don't like since Warty:
1. Can't delete items from menus by right-clicking anymore
2. "Disks" menu item has been deleted (??!!!)
3. Gaim was updated to latest, but not Firefox (Again, ??!!!)
4. Going through all that config junk @ boot was very annoying (OK, I know, it's just a preview release, so maybe that's why?)
What I like since Warty:
1. My city has been added to the Weather Report Applet (hahaha)
2. Updated system level stuff and some apps (of course)
3. The Ubuntu Wallpaper (Bring back the old ones too!)
What I don't like in general, for now:
1. Can't save sessions (oh joy, 5+ minutes of config every boot)
2. Feeling like I'm working in dirt, with that ugly default brown theme/colors (yeah, I can change it, but it's still ugly!)
3. No NTP!
What I like in general:
1. Ubuntu Linux :D

PS
Why is some of the Ubuntu Website Encrypted? I'm not talking about the login part...

---

### Post by rykel on 2005-03-13
hi,

do u mean to say tat ubuntu used to load ur partitions by default?

i would indeed like to see them automounted!

anywae, hope tat e final release will do tat, coz it's a convenient feature...

or at the very least, do it like mepis kde, leave the device icons on e desktop for u to "activate", thus no real automounting has occurred (for e technical among us), & yet, no fstab has to be edited (for e newbie among us).

btw, i also hope distros can be compatible with the last version... ie. do NOT change tis/tat, or break tis/tat - eg. it's illogical tat a device can work out of the box in version OLD, but not in version NEW    ](*,)

---

### Post by Tapeworm on 2005-03-13
303 - I am working on a HOWTO on mounting drives via the terminal  or using a script you can save to USB device. My short term goal is to boot off the Live CD, run my script and have all of my disks show up on the desktop. Each person will need to edit the script to reflect their hard drive/partition setup.

My long term goal is to use the same script to install NDISWrapper and load drivers for my wireless NIC. Or at least VLC so I can watch more types of movie files...

Tapeworm

---

### Post by 303 on 2005-03-13
Neh, in Warty you just went to the "Disks" section in the Places Menu and right-clicked on the drive and mounted it... I believe... can't think right now. Maybe I'm thinking of when I help my dad with OS X?
Two more bones to pick... why not use XMMS or another program that *actually* works to play MP3's? Or even net radio? The "Music Player" does none of these. This would increase the user base by Ten fold, I guarantee it! 
I accidentally screwed myself out of using Sudo... I get this:
/etc/sudoers is mode 0777, should be 0440
Hmm ok I'll just chmod it to 0440
OH WHOOPS I can't do that because you need SUDO to run Chmod!!
I smell some kind of protection lockout with this message?
Sudo Root Sudo runaround!

BTW
I got mount to work... finally.... what a pain. But a *good* learning pain! hahahaa

---

### Post by Tapeworm on 2005-03-13
[QUOTE=303]
Two more bones to pick... why not use XMMS or another program that *actually* works to play MP3's? Or even net radio? The "Music Player" does none of these. This would increase the user base by Ten fold, I guarantee it! 
[/QUOTE]

An evil company named Fraunhofer Institute invented the technology behind MP3's and holds all of the patents on the technology. They have the rights to charge fees for any use of their technologies even just listening to a file. Fraunhofer uses this as a legal stick on occasionally to sue companies distributing MP3 software (players, encoders, etc).

Ubuntu is all about the freedom to use and distribute software. Instead of risking a Fraunhofer lawsuit, it supports the patent-free music file format OGG Vorbis (which is better than MP3 BTW...). RhythmBox (AKA "Music Player") plays Ogg files fine. My music library is about half MP3 and half Ogg. One day I will re-rip the rest to Ogg or FLAC (another free format). 
 
Anyone with the installed version of Ubuntu can go out and download whatever software they desire. Us Live CD users don't have that option. You may want to check out another Linux Live CD called Knoppix. It is more mature than Ubuntu and has different policies on what software can be included (it includes XMMS for example).

[https://www.ubuntulinux.org/wiki/RestrictedFormats](https://www.ubuntulinux.org/wiki/RestrictedFormats)
[http://www.woltec.com/mp3faq.html](http://www.woltec.com/mp3faq.html)
[http://www.knoppix.org/](http://www.knoppix.org/)

> BTW
I got mount to work... finally.... what a pain. But a *good* learning pain! hahahaa

Congrats. In the immortal words of G.I. Joe "And knowing is half the battle"


Tapeworm

---

