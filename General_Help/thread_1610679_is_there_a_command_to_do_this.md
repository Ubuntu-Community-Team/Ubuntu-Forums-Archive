---
title: "is there a command to do this?"
date: 2010-11-01
forum: General Help
---

### Post by coreyscx on 2010-11-01
say ive got a folder..containing music, mp3 files, inside folders..is there a way to open the terminal and write out a code to DELETE ALL OF THE ALBUM ART? thanks guys..someone earlier mentioned a "bash command"??

---

### Post by HiImTye on 2010-11-01
you could do something like
```
rm -R *.jpg
```from within whatever main folder you want to run it from

i.e. if your music is stored like
~/Music/Black Eyed Peas
~/Music/Beach Boys

you would run it from ~/Music

edit: that is assuming your album art is all .jpg format and the album art is inside those folders

---

### Post by KeyserSoze93 on 2010-11-01
> **HiImTye said:**
> you could do something like
```
rm -R *.jpg
```from within whatever main folder you want to run it from

i.e. if your music is stored like
~/Music/Black Eyed Peas
~/Music/Beach Boys

you would run it from ~/Music

edit: that is assuming your album art is all .jpg format and the album art is inside those folders

Run ```
ls -R *.jpg
``` first to check that it's matching what you hoped and nothing you wanted to keep.

---

### Post by blueridgedog on 2010-11-01
Will through in *.JPG for good measure as the OS is case sensitive.

---

### Post by coreyscx on 2010-11-01
okay guys my music is located obviously in my music..so if im in that directory on the terminal (/home/corey/music) then what exactly do i type in?? cause i keep tryign and it isnt working, it will say there is no such file or directory.

---

### Post by HiImTye on 2010-11-01
```
rm -R *.jpg *.Jpg *.JPG *.JPEG *.jpeg *.Jpeg
```
this aught to catch all of them unless there are some weird jPg formats (but unlikely)

---

