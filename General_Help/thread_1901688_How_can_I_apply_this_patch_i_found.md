---
title: "How can I apply this patch i found?"
date: 2011-12-29
forum: General Help
---

### Post by hopelessone on 2011-12-29
Hi,

I found a patch for my remote for the Asus P7131 Hybrid Tv Card.

How can I apply this to get my remote buttons working?

[http://patchwork.linuxtv.org/patch/4470/](http://patchwork.linuxtv.org/patch/4470/)

Thanks,

---

### Post by dodo3773 on 2011-12-29
> **hopelessone said:**
> Hi,

I found a patch for my remote for the Asus P7131 Hybrid Tv Card.

How can I apply this to get my remote buttons working?

[http://patchwork.linuxtv.org/patch/4470/](http://patchwork.linuxtv.org/patch/4470/)

Thanks,

Are you compiling it from source or have you already done so? If you are rebuilding it I can help you. You just have to look at the file names and the diff lines. If that file exists on your system it should be as easy as:
```
  
patch [OPTION]... [ORIGFILE [PATCHFILE]]

```

-taken from "patch --help"

---

### Post by hopelessone on 2011-12-29
Hi,

Thanks for helping me,

Lets rebuild it..

Please give me baby steps...this is what i got so far:

> git clone git://linuxtv.org/media_build.git
cd media_build 
./build

Source: [http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

How to apply it?
> patch ASUS-My-Cinema-P7131.patch rc-asus-pc39.c

Is the 'Download' patch at the top of the web page the same as the pasted info below?

Whats next?
> ./build.sh
sudo make install

Will this install any missing dependencies? What about Checkinstall? is it better?


Thanks..

---

### Post by dodo3773 on 2011-12-29
Hey, I just got back.

Yeah, definitely use checkinstall. I am looking through that git clone. Where is the "/drivers/media/IR/keymaps/rc-asus-pc39.c" file? We should be able just to edit the source directly and then compile it normally without the need of a patch.

---

### Post by dodo3773 on 2011-12-29
There are patch instructions on the site you linked to. It says to put the patch in the backports directory before you run ./build. It also says to add your kernel version to the packports directory (which I am going to have to assume is in fact the backports directory as well). I do not understand a lot of perl so I got a little lost looking at it. I am thinking you just copy the file to the  "media_build/backports" directory. Then you edit the backports.txt to reflect your changes. You may want to append your kernel version to the name of the file as well. 

What is your kernel version (uname -r)?

---

### Post by hopelessone on 2011-12-31
Turns out that editing lirc/hardware.config and changing load modules from true to false solved this without installing the patch...

But thanks for your help...now I know how to patch things..

---

