---
title: "&quot;Out of disk space&quot; while there is space (Wine and Crossover))"
date: 2011-10-01
forum: General Help
---

### Post by thunderbirdje on 2011-10-01
Hello everyone,

I've tried to install TI-Nspire(TM) Student Software (CAS v3.0). // Need it for school. 

I am installing from /media/TINSpireStudent. 

The setup screens show up properly. However when arriving at the step "Install location" the location (which I left default being "C:\Program Files\TI Education") and pressing "Next" a window pop-ups (see attached image) titled: 

*"**TI-Nspire Student Software**" with the message **"Out of disk space". The highlighted volumes do not have enough disk space available for the selected features. The installation requires at least 714.65Mb, please select other location".** *

To be clear: there is enough space on my physical drive (40GB left). 

The window looks like a Java-style messagebox. Probably the 'available virtual bottle/disk space (or how should I call it?)' is not correctly detected by the TI-Nspire installation program.  

Looking for a solution. Maybe someone can pin it down? Or you can setup some wine/Crossover variable to report back a "big enough disk space"?

If you have more questions, feel free to ask! 

I am using Ubuntu 11.04 and installed the Crossover 10 demo and using Wine 1.2.2. 

I really hope I can avoid partitioning my HD and having to put the nasty Windows back BESIDES Ubuntu ;) on my laptop.  

[image=http://www.box.net/shared/eglh9a8hr1yihxvqrcgy]
If you cannot see the image click here [link=http://www.box.net/shared/eglh9a8hr1yihxvqrcgy]image[/link]

---

### Post by peragrate72 on 2011-10-01
That happened to me today, and I couldn't figure it out. I installed filelight and found I'd made a humongous 15gb mp3 file the night before and forgot about it.

Try this app and see if it helps you find your mystery data:

```
sudo aptitude install filelight -y
```

It takes a bit of concentration, but you'll find all data on all mounted partitions represented graphically with extra hover information.

It's a great tool.

Hope that helps.

---

### Post by thunderbirdje on 2011-10-01
Already tried that (I used Disk Usage Analyze) -> 39.8GB free. I also emptied the trash.

Btw: I can install other programs like matlab while TI-NSpire complains in an Java-styled window about the disk space. My guess it's Java & Wine combined  related problem???

However thank you for trying to help me! :D

---

