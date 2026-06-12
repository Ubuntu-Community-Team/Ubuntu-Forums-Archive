---
title: "Make an iso"
date: 2009-07-21
forum: General Help
---

### Post by nmaster on 2009-07-21
If I have a CD/DVD, whats the best way to make an iso file?  I have recovery discs and it would be nice to back these up. Thanks.

---

### Post by grayn0de on 2009-07-21
Personally, I like AsetoneISO. It's alot like Alcohol for Windows.

[http://www.acetoneteam.org/](http://www.acetoneteam.org/)
[http://www.getdeb.net/search.php?keywords=acetoneiso](http://www.getdeb.net/search.php?keywords=acetoneiso)

---

### Post by jerome1232 on 2009-07-21
Brasero, the default cd/dvd buring program in Ubuntu can do this, long as we aren't talking about copy protected discs/encrypted dvd's that is.

---

### Post by lukeiamyourfather on 2009-07-21
When the disc mounts and shows up on the desktop, right click it and there's an option to duplicate the disc. A dialog comes up with an option to copy to another disc drive or to copy to an image. Probably won't work on copy protected discs though. Cheers!

---

### Post by Cheesemill on 2009-07-21
```
 
dd if=/dev/cdrom0 of=filename.iso

```You may have to change /dev/cdrom0 to correspond with your drive.

---

### Post by lukeiamyourfather on 2009-07-21
> **Cheesemill said:**
> ```
 
dd if=/dev/cdrom0 of=filename.iso

```You may have to change /dev/cdrom0 to correspond with your drive.

Haven't seen that before. Just searched the command, nifty!

---

### Post by nmaster on 2009-07-21
thanks everyone.  i used brasero

---

### Post by synapsys on 2009-07-21
> **Cheesemill said:**
> ```
 
dd if=/dev/cdrom0 of=filename.iso

```

+1 I use that all the time. It's quick, easy, and no waiting for clicky gui's.....

---

### Post by KeyserSoze93 on 2009-07-22
If you install dd_rescue, it allows you to see the progress and speed of the copy:

```
dd_rescue /dev/cdrom disc.iso
```

---

### Post by t4thfavor on 2009-07-22
I love me some dd* either regular dd or dd_rescue. both are better than the GUI if you need to create an ISO in a hurry. 

Remember when you start learning more about the CLI, you will use less and less GUI apps. GUI's are great, but the mouse is way slower then the keyboard.

maybe it has less RAM? I dunno, but thats my $.02

---

