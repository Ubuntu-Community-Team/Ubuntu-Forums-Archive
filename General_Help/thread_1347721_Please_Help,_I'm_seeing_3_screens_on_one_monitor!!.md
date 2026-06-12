---
title: "Please Help, I'm seeing 3 screens on one monitor!!!"
date: 2009-12-06
forum: General Help
---

### Post by Mysterchr on 2009-12-06
I'm new to ubuntu and linux, I'm a Windows guy that wanted to see if I couldn't learn to compile the Chomium OS. On their blog they suggested using ubuntu 8.04 to compile the code, but unfortunately since the moment I threw the live cd I've been looking at three different screens on the one monitor. They all three overlay on top of each other which makes it impossible to see what's going on. I've managed to go ahead and install the operating system hoping that once it was installed I could connect to the internet and update the drivers. 

Everything's installed, all updates have been applied, and in the restricted drivers list nothing is listed! Can someone please help me?

---

### Post by bacardiandwatermelon on 2009-12-06
[http://chromeos.hexxeh.net/](http://chromeos.hexxeh.net/)

And follow the windows instructions, this will make chrome bootable of a flashdrive. But personally I don't see what the big deal is, I hate the fact you can't install stuff :-(

---

### Post by ugm6hr on 2009-12-06
Sounds like a Graphics card issue.

Theoutput from the following might help us work out what's up.

```
lspci
sudo lshw -class display
```

---

### Post by Mysterchr on 2009-12-06
Well thanks for the help but I got it solved somehow...I tried plugging the laptop into my monitor to see if it was doing the same thing there or not...While pressing FN F8 to get it to display on the monitor it, which wasn't working FYI, I slipped and hit FN F7 all of a sudden the screen did a little flicker and then rearranged itself real quick. I guess the display options were set incorrectly or something. I really don't know...

Also Thanks for the thumb drive loader of chrome I haven't seen that yet. It's downloading now and I plan to play with it a bit. Personally so far I've been running chrome on VM which you can get here [http://www.mysterchr.com/?page_id=182](http://www.mysterchr.com/?page_id=182) I'm trying to learn to compile the code to see if I can't play around with it a little. It's just a new project. If you know of any good forums for chrome os stuff I can check out that would be awesome... You can email me at [email]me@mysterchr.com[/email]

---

