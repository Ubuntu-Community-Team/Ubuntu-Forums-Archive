---
title: "sound annoyances and other things"
date: 2006-05-15
forum: General Help
---

### Post by Polygon on 2006-05-15
Hello, this is like my 5th topic in a week but i have a lot of questions so bear with me =P

I just recently got my sound card (sound blaster live 24 bit) working in ubuntu, and sound works just fine and all, its just when I'm playing music (in general, Ive noticed this thin both xmms and rythmbox) , if another sound plays (like in gnome if you click on some things it will make a drum sounding noise), whenever a sound plays, the music slows down and gets kinda distorted for a second, then returns to normal

i was wondering if there is any way to fix this

I'm thinking its most likely because i was installing the alsa drivers using instructions from the alsa site, but then realized it was installed on ubuntu already (i installed the drivers and the library, i couldn't install the utils cause it required some library, which was when i noticed that it was already installed on ubuntu), could this be the problem?


and also another thing, i have two hard drives, one with ubuntu and one with windows on it. My friend who got me into linux told me the command to mount the windows drive (which has a separate fat32 partition which i keep the "my documents" folder in windows on, which has all my pictures, music, stuff like that) was "sudo mount /dev/hda3 /mnt/windows/", but its kinda annoying that every time i start up ubuntu i have to type in command to listen to music and stuff, is there any way where i can like make it so that ubuntu mounts the drive on start up?

all help is appreciated, thanks a bunch

~Polygon

---

### Post by Dr. Nick on 2006-05-16
[quote=Polygon]Hello, this is like my 5th topic in a week but i have a lot of questions so bear with me =P
.................


and also another thing, i have two hard drives, one with ubuntu and one with windows on it. My friend who got me into linux told me the command to mount the windows drive (which has a separate fat32 partition which i keep the "my documents" folder in windows on, which has all my pictures, music, stuff like that) was "sudo mount /dev/hda3 /mnt/windows/", but its kinda annoying that every time i start up ubuntu i have to type in command to listen to music and stuff, is there any way where i can like make it so that ubuntu mounts the drive on start up?

all help is appreciated, thanks a bunch

~Polygon[/quote] 
Not sure on the sound but the file /etc/fstab controls the partitons
here is a line from mine to mount a fat32 partiton
/dev/hda5 /home/drnick/D vfat uid=1000,gid=1000,auto,rw,users 0 0

just modilfy and add that line to your fstab by editing it as root. I believe changing auto to noauto will make it not mount at boot
try adding this line

/dev/hda3 /mnt/windows/ vfat uid=1000,gid=1000,auto,rw,users 0 0

EDITED due to my example being messed up

---

### Post by Polygon on 2006-05-16
thanks dr. nick! editing that file and simply editing that line to what i have makes the partition auto mount, and i even get a handy dandy icon on my desktop now :D

Hmm... i see that you edited what you told me to enter, i edited the file to this:

> /dev/hda3 /mnt/windows vfat auto,uid=1000,gid=1000,auto,rw,users 0 0

ill remove that extra auto. (before uid=1000)

the line now reads (after i removed the extra auto) is

> /dev/hda3 /mnt/windows/ vfat uid=1000,gid=1000,auto,rw,users 0 0

thanks for the help, but if anyone can help with my sound problem it would be greatly appreaciated!

---

### Post by Dr. Nick on 2006-05-16
[quote=Polygon]thanks dr. nick! editing that file and simply editing that line to what i have makes the partition auto mount, and i even get a handy dandy icon on my desktop now :D

Hmm... i see that you edited what you told me to enter, i edited the file to this:
/quote]

That should work, I had a noauto and a auto in mine by mistake, and it didnt mount at boot. I didnt realize this until I looked it up to answer you. I just removed the no auto and left auto so mine should now work aswell. My origional post is correct now, just didnt know if you had seen the messed up version before I noticed it :)

---

### Post by Polygon on 2006-05-16
bump :D

---

### Post by Polygon on 2006-05-16
double post sorry

---

### Post by Sutekh on 2006-05-16
[quote=Polygon]
I just recently got my sound card (sound blaster live 24 bit) working in ubuntu, and sound works just fine and all, its just when I'm playing music (in general, Ive noticed this thin both xmms and rythmbox) , if another sound plays (like in gnome if you click on some things it will make a drum sounding noise), whenever a sound plays, the music slows down and gets kinda distorted for a second, then returns to normal

i was wondering if there is any way to fix this[/quote] Try turning off those system sounds (I don't like them anyway)

System -> Sound -> Uncheck Sounds for Events

Does this stop the problem?

The default ALSA divers should be okay for the SB Live 24bit, they were for me. The ones in Dapper and the newer ones are even better, I finally got surround sound working with these ones.

---

### Post by Polygon on 2006-05-16
im sure that would stop the problem of when a sound in ubuntu plays, but i dont think that fixes the problem on why it was happening in the first place.

i just tried reinstalling alsa through sypnatic, and no luck. Im thinking its cause i installed the base driver and the library from the alsa site, but then used the utils from the default installation from ubuntu.

how would i go about removing all traces from alsa from my computer, then reinstalling the ubuntu versions from sypnatic? what things in sypnatic do i need to remove, and what files on my hard drive do i need to remove?

---

