---
title: "How do i format xp partition to ubuntu?"
date: 2006-03-11
forum: General Help
---

### Post by mistamcgoo on 2006-03-11
Hi, i have an acer aspire 1300 laptop. It originally came with an xp home preinstalled, i run it with breezy in dual boot. Now my xp has given up (again, 3rd or 4th time)

I cannot do a repair install because the cd's that came with this device are modified by acer. When i put them in, they reformat the entire hd to fat32 (for win xp !) and do everything "automated". I did this once before but i don't even know what will happen to grub or the ubuntu partitions.  Now i just want to get rid of xp alltogether. What would be my best option (also on longer term)

-delete everything and do a fresh ubuntu install? 
  I still have some data on the windows d: partition that i want to keep.   i just managed to mount my windows partitions (in /media)n but no cdrw, so i'd have to back everything up via usb memstick. And i'd have to redo all my "modifications" on ubuntu (kde, other programs, setting up my wireless nic in ndiswrapper, ...)

is there a good way to just make these partitions (a c:\ fat32, and d:\ ntfs) 
into linux format and add them to my ubuntu partition or some as extra swap?
This way i can just copy all my files to my /home folder, and make new folders
for them after i format the win partitions.

---

### Post by aysiu on 2006-03-11
[QUOTE=mistamcgoo]
is there a good way to just make these partitions (a c:\ fat32, and d:\ ntfs) 
into linux format and add them to my ubuntu partition or some as extra swap?
This way i can just copy all my files to my /home folder, and make new folders
for them after i format the win partitions.[/QUOTE] Yes!

Just ```
sudo apt-get update
sudo apt-get install gparted ntfsprogs
sudo gparted
``` and delete the Windows partitions (make sure they're not mounted first!). Then recreate them as Ext3.

You'll have to create folders (mount points) for them and add them to your /etc/fstab.

Just let us know if you need help with that.

---

### Post by mistamcgoo on 2006-03-11
Thanks for your help
the update and gparted install work, but when i do 
sudo gparted
i get
segmentation fault

program doesn't start up.

btw, i think i know  how to create new mount points ( is it same way like i did for win partitions?) but i don't know
what fstab is .

---

### Post by aysiu on 2006-03-11
You may find the answers [here](http://www.google.com/search?num=100&hl=en&lr=lang_en%7Clang_fr&safe=off&q=segmentation+fault+gparted+site%3Aubuntuforums.org&btnG=Search&lr=lang_en%7Clang_fr), but I clicked on a few of those threads, and it wasn't looking promising.

---

### Post by mistamcgoo on 2006-03-11
that doen't look promising  indeed. 

but i think i found something else. i also have Kde 3.5 installed (i use gnome 
or kde depending on my "mood".) in its start menu there's a program called 
disks-admin. i used this to mount my win partitions. i just unmounted them with it, and i noticed a "format" button. i clicked on it, chose my old win c: (nothing important on it) , and reformat to ext3(went pretty quickly) . i mounted it as a "data" folder in /home. 
Is this a good way? if so i can copy the important files from my old win d: to it and format that partition too.

what do i have to do to that /fstab thingie? (don't even know what that is sorry)

---

### Post by plors on 2006-03-12
[QUOTE=mistamcgoo]Thanks for your help
the update and gparted install work, but when i do 
sudo gparted
i get
segmentation fault

program doesn't start up.
[/QUOTE]

My guess is you're using an old version of gparted, please download the latest [gparted livecd]("http://gparted.sourceforge.net/livecd.php"), it's only 30 MiB in size and will most likely help you out.

If you still experience problems you should consider filing a [bug]("http://gparted.sourceforge.net/bugs.php")

---

### Post by mistamcgoo on 2006-03-12
livecd won't boot for me. i get an error message about "could not find kernel image" or something, after the screen with the blue "livecd" logo loads and i press enter. 
sigh, think i'm just going to give it a fresh install.

---

### Post by plors on 2006-03-12
doesn't sound good, please file a [bug]("http://gparted.sourceforge.net/bugs.php")

---

### Post by cotcot on 2006-03-12
I also had segmentation fault in Breezy and Hoary. I do not have it in Dapper. 

So you can consider Dapper. Install it on the XP partition. Delete the XP partition during install;
Or you can delete the XP partition with a live CD (Kanotix, Knoppix, ...)

---

### Post by mistamcgoo on 2006-03-13
> doesn't sound good, please file a bug

i just checked the bug list, problem is already known there 

i just gave my laptop a fresh install with kubuntu. I always been curious to see
the difference between kubuntu and ubuntu. (ubuntu on my desktop i'm typing on now). learning to work with adept atm. i don't know why but its really different from synaptic for me.

---

