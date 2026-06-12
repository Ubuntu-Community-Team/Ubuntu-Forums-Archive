---
title: "Not enough space on disk..."
date: 2010-09-11
forum: General Help
---

### Post by Kareta on 2010-09-11
I'm new to Ubuntu, first time using it. 

I was installing WoW when it gave me an error message saying I didn't have enough space on disk. I went to google and typed 'not enough space on disk linux' and clicked the first relevant thing I found. I misread it, I thought it said something like:
"...Virtual disk doesn't know how much memory you have..."

I don't know what I did, I ended up getting to my windows partition (I don't know how) and I just copied the file location of my wow folder into my home directory, computer started lagging. After the copying of files was complete, it gave me a couple of error messages saying "No room on disk left" with corresponding files that could not be copied because of this error.

This is when I started wondering if I really didn't have any space on my linux partition, looked up 'linux repartition' and found a question (which had been answered), someone had responded saying "Maybe you need to repartition your linux drive" or something like that and posted a command to be executed in the terminal:

```
$ sudo get-apt gparted
sudo gparted
```

I don't know what any of the drives mean or what they do. I have it set up as dual boot with windows 7, I installed ubuntu via wubi.

The guy who provided the code later said that I couldn't unmount the root drive. I think my windows drive is set up as my root drive.

I don't know :\.

Help?

---

### Post by Capt_Scribble on 2010-09-11
I've never used wubi, but are you using wine to run WOW or a virtual machine?

---

### Post by Kareta on 2010-09-11
> **Capt_Scribble said:**
> I've never used wubi, but are you using wine to run WOW or a virtual machine?

I was going to use wine, but I ran out of disk space. 

So I never ran WoW, ran out before files finished copying.

Here's a picture of Gparted, by the way: 
[IMG]http://i52.tinypic.com/21m9clu.jpg[/IMG]

---

### Post by Kareta on 2010-09-11
Anyone know what to do?

Uninstall windows and start from scratch?

:s.

help please.

EDIT: Never mind, figured it out myself.

---

### Post by cgroza on 2010-09-11
You have plenty of space left according to the screenshot.

---

