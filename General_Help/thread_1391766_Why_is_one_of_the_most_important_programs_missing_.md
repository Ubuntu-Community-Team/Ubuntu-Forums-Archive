---
title: "Why is one of the most important programs missing in Ubuntu?"
date: 2010-01-27
forum: General Help
---

### Post by susanne260 on 2010-01-27
I'm trying to install Karmic Koala on a friend's laptop and the following has happened three times already:

The installer goes up to 94% and says "Configuring Bootloader" or something similar... and then the installer window just disappears, however the hard disk activity light stays on. I waited for 20 minutes and nothing happened. But the HDD light is still on. So I'm assuming files are still copied onto the hard drive, no? Or has it crashed?

I don't know. How would I know? **There is absolutely no feedback from the system whatsoever.** :(

Come to think of it, on my own computer a similar issue has very often also been extremely annoying:
Sometimes the HDD light starts flickering for 30 seconds for no reason and **I have no idea which files are being accessed and by what.**

When I was still using Windows, I found out that the best program ever created is FileMon. It told you exactly which files were being accessed and by what. Thus fulfilling the most BASIC need when using a computer: knowing what is going on. Otherwise you're like a hedgehog in the mist.

So, is there a FileMon alternative to Ubuntu? :)
Or any other tool that just gives you basic information about your computer in real time? And why isn't it included on the Ubuntu CD by default? :confused:

---

### Post by Morbius1 on 2010-01-27
> So, is there a FileMon alternative to Ubuntu? :smile:

Maybe **gnome-system-monitor** is what you're looking for.

---

### Post by pastalavista on 2010-01-27
Open a terminal and run the following (one at a time)

```
top

atop

ps -A
```

---

### Post by bluefrog on 2010-01-27
command line:
lsof

---

### Post by susanne260 on 2010-01-27
Thanks for the replies, but all those programs just seem to list the open files, no?

However with FileMon in Windows you can filter out the files that are currently being written to HDD in real time, so it's especially useful when the HDD light suddenly starts flickering and you have no idea why. It just tells you which program is responsible for 99% of the HDD activity at that time, while filtering out all the unnecessary stuff.

Is there something like that for Ubuntu as well? :)


/Edit: I think I just found what I was looking for:
[http://packages.ubuntu.com/intrepid/iotop](http://packages.ubuntu.com/intrepid/iotop)

Therefore the **iotop -ob** command seems to do exactly what FileMon does in Windows... simple, effective and very informative. :KS

---

