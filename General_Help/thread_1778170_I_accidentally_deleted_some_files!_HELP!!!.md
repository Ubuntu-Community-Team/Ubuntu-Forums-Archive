---
title: "I accidentally deleted some files! HELP!!!"
date: 2011-06-08
forum: General Help
---

### Post by link15 on 2011-06-08
is there any way to recover deleted .sb files (scratch files) [http://scratch.mit.edu/]("http://scratch.mit.edu/")?

---

### Post by marohds on 2011-06-08
There is a way but it depends if a process maintains opened the file...

[http://www.linux.com/archive/articles/58142](http://www.linux.com/archive/articles/58142)

good luck

---

### Post by grahammechanical on 2011-06-08
Where are these Scratch files stored? On-line or on your computer? If there are stored on the computer then when you deleted them they got figuratively put in the trash can or waste bin. Just click on it and file manager will open the waste bin and you can restore the files. If you have emptied the waste bin, then you need more help than I can give.

I do not know how this Scratch system works or where files/projects are stored. sorry.

Regards.

---

### Post by link15 on 2011-06-08
it stores them in /home/user/documents/scratch files and I permanently deleted it by emptying the trash not realizing they were in there

---

### Post by dFlyer on 2011-06-08
Chances are they are gone. You can try photorec but no guarantee.

---

### Post by link15 on 2011-06-08
I also tryed this [http://www.webupd8.org/2009/03/recover-deleted-files-in-ubuntu-debian.html]("http://www.webupd8.org/2009/03/recover-deleted-files-in-ubuntu-debian.html") but I don't know how to get that file type to work with scalpel or foremost

---

### Post by link15 on 2011-06-09
is there any way to search for a certain file extension (.sb) within a folder within 974 folders (photorec outputed 974 folders) all at the same time?, because it will take FOREVER to look for them in nautilus

---

### Post by wolfen69 on 2011-06-09
I've used MagicRescue (in the repos) in the past with success. An example would be:
```
magicrescue -r jpeg-jfif -r jpeg-exif -d ~/output /dev/hdb1
```

Of course, you would need to change the extensions and output.

---

### Post by link15 on 2011-06-09
that doesn't make any sense, how do i use magicrescue?

---

### Post by wolfen69 on 2011-06-09
> **link15 said:**
> that doesn't make any sense, how do i use magicrescue?

[http://www.irongeek.com/i.php?page=backtrack-3-man/magicrescue](http://www.irongeek.com/i.php?page=backtrack-3-man/magicrescue)

---

### Post by link15 on 2011-06-09
```
sudo find '/home/scooterbirk/Documents/Scratch Projects' *.sb

``` apparently photo rec wasn't able to recover them. I searched for it with that command, but it didn't have what I was looking for

---

### Post by linuxinstalledfromhdd on 2011-06-09
are you sure you are using photorec right?

check out this demo:

[http://cinderbox.net/2011/05/12/photorec-digital-picture-and-file-recovery/](http://cinderbox.net/2011/05/12/photorec-digital-picture-and-file-recovery/)

---

### Post by link15 on 2011-06-09
i'm sure i'm using photorec correctly, i found some of my mp3's:) that i accidently deleted, but it didn't find my scratch files:(

---

### Post by linuxinstalledfromhdd on 2011-06-09
Did you try magic rescue?

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

It's about half the way down the page.

---

### Post by link15 on 2011-06-09
can someone helo me make a recipe file for .sb files?

---

### Post by link15 on 2011-06-10
how do you make a recipe file for magic rescue?

---

