---
title: "Accessing USBs Through the Terminal"
date: 2011-10-20
forum: General Help
---

### Post by Gnome1984 on 2011-10-20
This is a newbie question first and foremost. I am trying to access a USB stick through the terminal and are unable to. I AM able to access it through the GUI. Do I need to mount the USB through the Terminal. I understand it should auto-mount and that is why I can access it through the GUI.

---

### Post by hhh on 2011-10-20
I'm currently running Debian, but this should be the same in Ubuntu. If the USB automounts, you can access it in /media. So change to the media directory, list the contents, change to the USB directory. For me (and I listed the USB contents to verify I was in the right folder)...```
hhh@hhh:~$ cd /media
hhh@hhh:/media$ ls
C0F4-E5B6  cdrom  cdrom0  cdrom1
hhh@hhh:/media$ cd C0F4-E5B6
hhh@hhh:/media/C0F4-E5B6$ ls
cwm                                     libnl1_1.1-6_i386.deb
firmware-ralink_0.28_all.deb            libpcsclite1_1.5.5-4_i386.deb
interfaces                              wireless-tools_30~pre9-5_i386.deb
libdbus-1-3_1.2.24-4+squeeze1_i386.deb  wpasupplicant_0.6.10-2.1_i386.deb
libiw30_30~pre9-5_i386.deb
hhh@hhh:/media/C0F4-E5B6$
```

---

### Post by Gnome1984 on 2011-10-20
eh1@eh1:/mnt/usb$ cd /media
eh1@eh1:/media$ ls
3AD6E390D6E34B29  ERIK Hxxxx
eh1@eh1:/media$ cd ./ERIK Hxxxx
bash: cd: ./ERIK: No such file or directory
eh1@eh1:/media$

---

### Post by hhh on 2011-10-20
Why is terminal starting in /mnt/usb instead of your home directory? Why'd you put the ./ before ERIK? Is ERIK really the folder for your USB (you could navigate to it in Nautilus or whatever file manager you use to check)? Why'd you add the Hxxxx folder too?

---

### Post by Gnome1984 on 2011-10-20
It was in the /media directory I just started from the /mnt directory.  The xxxx are added because I named the USB my full name in Windows, in case I left it at school.

---

### Post by hhh on 2011-10-20
You're going to have to rename it to something like ERIK_Hxxxx, terminal will bork on a space and just read the folder as 'ERIK'.

---

### Post by Gnome1984 on 2011-10-20
Thanks thought the space might be screwing it up.

---

### Post by hhh on 2011-10-20
No problem, if it's working you can mark this thread "solved", I think in "thread Tools".

---

### Post by mcduck on 2011-10-20
> **hhh said:**
> You're going to have to rename it to something like ERIK_Hxxxx, terminal will bork on a space and just read the folder as 'ERIK'.

No need to rename, you can simply enclose file and directory names with quotes if there are spaces in the name. Or escape the space with a backslash.
```

cd 'ERIK Hxxxx'
cd "ERIK Hxxxx"
cd ERIK\ Hxxxx
```

---

### Post by Grenage on 2011-10-20
As above, you can work around spaces when you encounter them; the experience will probably be enough to stop you using spaces in future.

Remember that you can also use the tab key to auto-complete directory and file names, which should automatically handle such syntax.

---

### Post by Gnome1984 on 2011-10-20
Thanks the 'xxx' quotation marks worked. Like I said I named through Windows because of school, but definately not use spaces anymore. 

Thanks Guys...

---

