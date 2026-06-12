---
title: "How do I make an HDD image for restore purposes?"
date: 2009-06-25
forum: General Help
---

### Post by solwic on 2009-06-25
I'm wondering if there's a way to make an image of my whole hard drive to make restoring the system easier than having to set everything up again.  I know it can be done, I just don't know what software I would need to do it.  

Any recommendations?  And how does it work, exactly?  Any known issues?  I know these are broad, vague questions...but I'm just looking for some advice, not concrete right/wrong answers.  

Thanks. :biggrin:

---

### Post by Therion on 2009-06-25
I think you'd want something like **Clonezilla** for that.

---

### Post by Cheesemill on 2009-06-25
+1 for CloneZilla

---

### Post by Therion on 2009-06-25
> **Cheesemill said:**
> +1 for CloneZilla
Yeah, obvious choice, but why are all the links to it dead?

---

### Post by mattgyver83 on 2009-06-25
I havent used Clonezilla however have used Partimage.  Its pretty simple to use and I think i found a video on youtube that explained it pretty well.  If you are using an ext4 filesystem this will not be an option though.

---

### Post by howefield on 2009-06-25
> **Therion said:**
> ...but why are all the links to it dead?

clonezilla.org seems fine.

---

### Post by jimv on 2009-06-25
You can also use Gparted to copy and paste partitions...doesn't create an image, it just creates a replica of the partition on another drive.  Easiest way to backup IMHO.

---

### Post by mk1w86 on 2009-06-25
> Yeah, obvious choice, but why are all the links to it dead?

Do you mean the website which seems to work?

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by izizzle on 2009-06-25
TIP:

Next time you do a fresh install, you may want to create a separate /home partition so if anything goes wrong, all your personal files would remain untouched an you could just reinstall into the / partition.

---

### Post by solwic on 2009-06-25
Thanks for all the replies.  I'm looking at clonezilla, but I have another question or two:

1)  I've read that the dd command can do this, as well.  I've used dd before to make copies of CDs to .iso, but never to make an image backup.  would something like ```
 dd if=/dev/sda of=/dev/sdb bs=16k
``` work?  

2)  How would I restore from the image, once I've made it?  Is it a matter of copy/paste from the backup media to the main drive?  Or is it more involved than that?  

Thanks for the snappy replies.  :)

---

### Post by solwic on 2009-06-25
> **izizzle said:**
> TIP:

Next time you do a fresh install, you may want to create a separate /home partition so if anything goes wrong, all your personal files would remain untouched an you could just reinstall into the / partition.

That's what I have set up now.  What I want to do, though, is find something faster for this lappy of mine.  It's a little slower than my old desktop, so I'm looking at things like Zenwalk or Xubuntu, which ought to be faster on this machine.  

I know I can install xfce to Ubuntu, but I've always had problems when installing two DE's to the same core.  Don't really have the space to dual boot, so I thought I'd make an image of my Ubuntu install and then wipe the drive and install Zenwalk.  If I don't like it, Ubuntu would be very easy to install from an image backup.  I love Ubuntu, but setting everything up the way I like it is tedious.  

:)

---

### Post by mk1w86 on 2009-06-25
Although dd would probably work I think it would be safer to use Clonezilla.

---

### Post by Therion on 2009-06-25
> **howefield said:**
> clonezilla.org seems fine.
Bizarre... It's timing out for me.  :confused:

---

### Post by solwic on 2009-06-25
> **Therion said:**
> Bizarre... It's timing out for me.  :confused:

Works for me.  Now I just gotta figure out how to restore from a backup image.  Heh.  

Thanks again for all the snappy replies.

---

### Post by howefield on 2009-06-25
> **iRun said:**
> Works for me.  Now I just gotta figure out how to restore from a backup image.

I wouldn't worry too much about that, if you work out how to make the image in the first place, you'll work out how to restore. 

Seriously.

---

