---
title: "Ejecting cd and i can still see/access it?"
date: 2011-01-22
forum: General Help
---

### Post by police512 on 2011-01-22
Hey i have Linux mint running and i dont know if i should be putting this here but here goes :S

I have this strange problem. When i put CD in i can see it and everything. But when i eject pressing the button on my laptop it ejects fine but i can still see the CD on desktop and in my computer and i can still access it and run programs ect on it still. Even though the CD it ejected. If i eject by right clicking then that works fine but its just annoying! Can anyone help??


THanks

---

### Post by hakermania on 2011-01-22
Ok, so,
1) place the CD in the CDROM
2) see if you can access your files
3) open a terminal and give "eject" (without the ")
If step 3 doesn;t solve your problem (you can still see your files) move to step 4:
4) Give in the terminal "umount /media/MY_CD" (without the ")(where MY_CD is the name of your cd (you can open nautilus and go to /media folder to see what it is)
5) Finally give "eject" again (without the ")
This is AFAIK

---

### Post by police512 on 2011-01-22
> **hakermania said:**
> Ok, so,
1) place the CD in the CDROM
2) see if you can access your files
3) open a terminal and give "eject" (without the ")
If step 3 doesn;t solve your problem (you can still see your files) move to step 4:
4) Give in the terminal "umount /media/MY_CD" (without the ")(where MY_CD is the name of your cd (you can open nautilus and go to /media folder to see what it is)
5) Finally give "eject" again (without the ")
This is AFAIK



Hey thanks ive tried all that but it hasnt worked. i ejected the cd and it went. But when i put it in again open it and press the 'eject' button on my laptop it's still there and i can still open and read the files like th CD is still in :S I Have to right click on it and press eject otherwise when i put a different CD in i cannot see it. I can only see the one i put in before :S

---

### Post by police512 on 2011-01-22
Anyone else?

---

### Post by tredegar on 2011-01-22
> i can still open and read the files like th CD is still in :S 
What is ":S" ?

The CD contents are probably cached. Try "refresh" or "reload".

And you are running "mint" but this is _ubuntu_forums.org

---

### Post by hakermania on 2011-01-22
BTW, :S is "confused" (msn emoticon)

---

### Post by Old_Grey_Wolf on 2011-01-22
Your computer is mounting the CD. You are not unmounting it before you use the CD drive button to eject it. 

If there is an icon on your desktop when the CD is in the drive, right click on the icon and select eject. That will unmount the CD and eject it.

You can also go to the menu "Places > Computer" and select the CD in the display. Then click on the triangle next to the CD's name to unmount it.

---

