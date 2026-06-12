---
title: "Nautilus Places Icons"
date: 2011-01-02
forum: General Help
---

### Post by johnproyal on 2011-01-02
I keep all my media on a separate partition. I'm dual booting as well, running Windows 7 and Ubuntu. What I'd like to do is have the icons in my home folder act as links to where the appropriate media is on my third - well, fifth; my drive is partitioned as sda1 (Windows Recovery), sda2 (Windows), sda3 (Ubuntu), sda4 (Ubuntu swap) and sda5 (Media) - partition. I can easily make links and place said links in the Home folder, that isn't a problem. What is is keeping the icons for those consistent. What I'd like is to have the icons in the Places sidebar stay the same as those in the Home folder.

I'm using Nautilus-Elementary under Ubuntu 10.10. This is a relatively fresh install (I reinstalled last night in hopes of a new slate), with only a few things installed that I doubt would do anything to Nautilus program.

If I make a link and rename it, it changes the icon, but doesn't change the icon in Places. Same if I change it using Ubuntu Tweak, or via the text file located at ~/.config/user-dirs.dirs.

I read that using symbolic links might work, but I couldn't figure that out completely. I believe I made one successfully, what I put in terminal was: 

```
ln -s /home/john/download/ /media/Storage/Download/

```
and it even said it created it. Alas, clicking on the Download icon in Home took me to the Download icon in Home.

Thanks for any help, it's something that's been bugging me since I started using Ubuntu. My goal is to have a unique icon in Places that points to the same place the icon in Home would.

The attached pictures are What I'd Like to have happen in Nautilus, and what is the current result with each thing I tried, which I talked about in the second paragraph.

---

### Post by johnproyal on 2011-01-02
Anyone?

---

### Post by veggen on 2011-01-02
Is [this](http://ubuntuforums.org/showthread.php?t=1648219) what you need?

---

### Post by johnproyal on 2011-01-03
That is exactly what I needed, thank you very much.

How does one mark solved?

---

