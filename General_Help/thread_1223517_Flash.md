---
title: "Flash"
date: 2009-07-26
forum: General Help
---

### Post by Kd40 on 2009-07-26
Hey i just downloaded Ubuntu yesterday and found that firefox didn't come with flash, i did a lot of searching over the Internet and found that adobe does have a place to download flash (there were 3-4 different types of files that i could download) firstly im not sure what the difference is between them and which is the best to get secondly the instructions that came with it made no sense, i did all the terminal stuff and kept getting "no such file or directory".

i'd like to be able to get flash going so i could use my beloved youtube but i cant at the moment. any anwsers? i was fluent in mac and windows but some things to ubuntu does confuse me alittle. (and for your info i've never used any terminal kind've apps).

thanks in advance.

---

### Post by 1/0 on 2009-07-26
Just follow [these instructions](https://help.ubuntu.com/community/Medibuntu) and you'll have it installed in no time.

---

### Post by Kd40 on 2009-07-26
I posted here because i couldnt make heads or tails over that tutorial and others, firstly which part would i be looking at? secondly which part was to do with flash? and all that, also as you've prob guessed im a complete newb when it comes to linux.

---

### Post by 1/0 on 2009-07-26
Actually, there's no need to go through all that hassle. The package is now days available in the multiverse repository so just bring up the Synaptics package manager (*System - Administration - Synaptic Package Manager*) and mark the package called *flashplugin-nonfree* and hit *apply*. The package will install and configure firefox. Restart Firefox if it was started during this.

---

### Post by nikgare on 2009-07-26
Try this command:

**sudo apt-get install flashplugin-installer**

If it doen't work could you please post the resultant error messages.

---

### Post by Kd40 on 2009-07-26
kd40@*****-******:~$ sudo apt-get install flashplugin-installer
[sudo] password for kd40: 

@nikgare: it got to this point where im guessing i was supposed to type my admin password which it would'nt let me do.


@1/0: can you post a link to where i can download "*lashplugin-nonfree*" thanks, i downloaded a few flash packages but none had that name.

edited to take out laptop name.

---

### Post by nikgare on 2009-07-26
the admin password is your password!

---

### Post by Kd40 on 2009-07-26
done 

kd40@tango-laptop:~$ sudo apt-get install flashplugin-installer
[sudo] password for kd40: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-installer
kd40@tango-laptop:~$ 

seems not to be working?

---

### Post by lovinglinux on 2009-07-26
> **Kd40 said:**
> done 

kd40@tango-laptop:~$ sudo apt-get install flashplugin-installer
[sudo] password for kd40: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-installer
kd40@tango-laptop:~$ 

seems not to be working?

Try this:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash 
sudo apt-get install flashplugin-nonfree
```

---

### Post by nikgare on 2009-07-26
> E: Couldn't find package flashplugin-installer

This could mean that you will need to enable the repsoitory - go to **System->Administration->Software Sources**, I think you'll need to enable the Third PArty Partney repo

---

### Post by Kd40 on 2009-07-26
It works now thanks guys :)

---

