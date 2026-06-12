---
title: "How to burn image file?"
date: 2006-06-19
forum: General Help
---

### Post by wr0x2 on 2006-06-19
I have a .cdr file, which I believe to be a roxio cd image. How can I burn this under linux? I tried opening it with gnomebaker, but it does not reccognize it as an image and gives me a warning. And no, the file is not a coreldraw document, it *is* a CD image of some sort.

---

### Post by user1397 on 2006-06-19
did you try just right-clicking on the file and selecting "write to disc"?  

alternatively, you could try installing k3b and see if that recognizes it. 
```
sudo aptitude update && sudo aptitude install k3b
```

---

### Post by msak007 on 2006-06-19
.cdr seems to be a raw audio-cd format from what I can gather. It's also used a a Corel extension, so it's kinda hard to find info on it (google strips the period in front of it and treats it as "cdr" - quite annoying). A few references I saw mentioned that this is a format used by CDRWin. Not sure if k3b supports it or not, couldn't find any info on that and I've never dealt with anything using that extension but it's worth a shot. I found a thread in another forum that's a little old (from 2004) indicating that k3b didn't support it, but that might've changed by now. [Here's]("http://forums.linuxiso.org/viewtopic.php?p=106436&sid=2706811257702a9ae2d5c701e21dccff") the thread for reference, but someone suggested in there renaming it to a .iso and see if it's recognized. If that doesn't work, see if you can download a trial copy of [CDRWin]("http://www.goldenhawk.com/") and use it with Wine to mount the image and convert it, or just find an ISO convertor that maybe supports that extension. Hope you get this figured out, let us know what happens.

---

### Post by wr0x2 on 2006-06-19
I have k3b installed, but I haven't used it in a while. I'll give it a try.

---

### Post by longinus on 2006-06-19
I don't think you will find a program to burn this image for linux... I would convert it to wav first, and them burn a normal music CD...

Search for "Raw Audio-CD" and you'll find some programs (didn't find linux ones, but a few for windows) that can open and convert CDR

---

