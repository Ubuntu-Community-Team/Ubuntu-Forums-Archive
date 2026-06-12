---
title: "Installing Tupi 2D animation software"
date: 2011-05-18
forum: General Help
---

### Post by higashi on 2011-05-18
In an attempt to install Tupi, I downloaded the tar.gz from [here]("http://www.maefloresta.com/portal/download_counter"). I would've loved to just install the .deb, but it seems that there's only an i386 deb available.

Unfortunately, I have no idea how to install the tar.gz package so I was hoping that someone can help me out with that.

Also, say I get this installed from the tar.gz, will updates for the program appear in my update manager?

Thanks in advance

---

### Post by xtingray on 2011-05-19
Hi! :)

You have two ways to install Tupi in your system. I'm guessing you have a 64bits Ubuntu version, so:

1. If you want to compile the Tupi source code manually, just follow the instructions described in this article: [http://www.maefloresta.com/portal/howCompileTupi](http://www.maefloresta.com/portal/howCompileTupi)

or

2. You can try to install the .deb installer for 64 bits in your system running next commands from console:
```
  
  *% sudo add-apt-repository ppa:xtingray/tupi*
  *% sudo apt-get update*
  *% sudo apt-get install tupi*

```
>> Also, say I get this installed from the tar.gz, will updates for the program appear in my update manager?

Currently, Tupi is not part of the Ubuntu official repositories (someday it will, but not now), so I think you have to look for update notifications from other sources, like these:
- [http://twitter.com/#!/maefloresta](http://twitter.com/#!/maefloresta)
- [http://identi.ca/maefloresta](http://identi.ca/maefloresta)

Good luck!

---

### Post by higashi on 2011-05-20
Thanks, I'll try compiling it :)
As for option 2, that didn't work since I'm running Natty.

---

### Post by xtingray on 2011-05-21
>> As for option 2, that didn't work since I'm running Natty. 

Next revision will be available for Natty in one month I guess.
Just pay attention to the announcements from the website ;)

---

