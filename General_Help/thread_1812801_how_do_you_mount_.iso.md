---
title: "how do you mount .iso?"
date: 2011-07-26
forum: General Help
---

### Post by KEE on 2011-07-26
hello,
I am wondering how do you mount an .iso? i have a file and it is an iso but i cant burn cause my dvd burner is not working on linux only windows but i want mount it so i can watch it. please help

---

### Post by 3602 on 2011-07-26
There is a program called GMount-ISO. It is in Software center.

---

### Post by WorMzy on 2011-07-26
I don't have an iso to test on, but I think this should work:

```
sudo mount -t auto -o loop /path/to/file.iso /mnt
```

---

### Post by KEE on 2011-07-26
ok its mounted but how would i use it? 
i mount it so i can watch the movie or run it. would this be the way to go though gmount

---

### Post by sisco311 on 2011-07-26
> **KEE said:**
> hello,
I am wondering how do you mount an .iso? i have a file and it is an iso but i cant burn cause my dvd burner is not working on linux only windows but i want mount it so i can watch it. please help

Watch it? If it's a video DVD, you can play it in xine, mplayer (smplayer if you need a nice GUI) or vlc without mounting it.

---

### Post by KEE on 2011-07-26
my dvd wont work on linux same with games so i copied the iso and now im trying to run it here

---

### Post by KEE on 2011-07-26
> **sisco311 said:**
> Watch it? If it's a video DVD, you can play it in xine, mplayer (smplayer if you need a nice GUI) or vlc without mounting it.

see [IMG]http://i222.photobucket.com/albums/dd124/assripp3r/Screenshot-15.png[/IMG]

---

### Post by 3602 on 2011-07-27
Modern Warfare Three? That game cannot be played on Linux unless you know your way around WINE.
That said, you're just missing a directory. Put
```
sudo mkdir /media/cdrom0
```
In the Terminal.

---

### Post by TBABill on 2011-07-27
An iso is just a disk image or file image. Think of it like a zip file. You can't just "open and use" it. It's meant to be used to transport the date and be extracted as a data image to another media. Think of Ubuntu's iso. You download that one file, then burn it as an image to a CD or DVD and you end up with files and directories on the target media.

---

