---
title: "Stuck at boot-up, on black screen."
date: 2012-01-24
forum: General Help
---

### Post by tomwcd on 2012-01-24
Hello everyone !
This is my first post here so first: hello everyone.

I'm posting here because I'm pretty new on Ubuntu, and I just ran into a serious (well I hope not) problem.

My computer is not starting anymore, I have absolutely no clue on what to do. Basically, my boot-up gets stuck on this screen:

[IMG]http://i43.tinypic.com/y2khf.jpg[/IMG]

(Sorry for the size of the image)

I tried pretty much all the options of the recovery mode, but nothing happened.

If someone has a clue and can reassure me, it'll be awesomely awesome !

Oh, and I'm using a dual boot computer with win 7.

Thanks in advance !

Thomas

---

### Post by hwttdz on 2012-01-24
Can you "alt+ctrl+f1" (try f2, f3... as well) when you're at that screen to get a login prompt?

If you can, you can login and start debugging.  I'd start by looking at /var/log/{dmesg,syslog,boot}

---

### Post by tomwcd on 2012-01-25
Thanks a lot for the answer.

So I can indeed type some code after pressing alt ctrl F1, then I'm left with this screen.
(Yes I'm VERY new to Ubuntu and Linux in general... I've been using it on an everyday basis for maybe a month, and without getting into the deep of it all...)

Are there some commands I can try to type to make it boot ?

Oh, and I forgot to mention that before this arrived, I did too things: 
- I tried to remove my password to get rid of the authentification all the time. I set it to none in the Ubuntu UI, and then I typed some code I don't remember in the Terminal, probably something like "sudo passwd delete".

- Second thing I did that might have messed things up is I tried to have my HDMI plug working in Ubuntu, so I tried to update my Nvidia geforce 520M driver, and maybe I have done something wrong in this.

So yeah, here is the screenshot.

Thanks in advance guys :)

[IMG]http://i39.tinypic.com/25untr6.jpg[/IMG]

---

### Post by BC59 on 2012-01-25
Try to uninstall NVIDIA driver
```
sudo sh NVIDIA* --uninstall
```

---

### Post by tomwcd on 2012-01-25
I just tried, I got:

"sh: Can't open NVIDIA*"

---

### Post by BC59 on 2012-01-25
Look this:
```
sudo rmmod nvidia
```

---

### Post by tomwcd on 2012-01-25
Weird, I have "Module nvidia does not exist in /proc/modules"...
Maybe the whole nvidia driver thing ****** up during the update?

---

### Post by BC59 on 2012-01-25
If you can, try to run the command from recovery mode.

---

### Post by tomwcd on 2012-01-25
I can access only a "limited read-only menu", what does it mean?
When typing the codes you nicely gave me nothing happened here neither.

---

### Post by BC59 on 2012-01-25
Try to boot with Recovery mode. In the recovery menu select the alternativ root. Drop to root shell promt. At the prompt type exit and then select Resume to normal boot.

---

### Post by tomwcd on 2012-01-25
OK, I got the same responses, aka:

for "sudo sh NVIDIA* --uninstall":
sh: Can't open NVIDIA*


for "sudo rmmod nvidia": 
ERROR: Module nvidia does not exist in /proc/modules

When resuming to normal boot, I'm in what I believe is the terminal version of the OS, right? I can type stuff now.

---

### Post by BC59 on 2012-01-25
Try to completely remove NVIDIA:
```
sudo apt-get purge nvidia*
``` and ```
sudo rm /etc/X11/xorg.conf
``` then reinstall xorg
```
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64
```
```
sudo dpkg-reconfigure xserver-xorg
```
and reboot
```
sudo reboot
```

---

### Post by tomwcd on 2012-01-25
THANK YOU a lot !!!

It is perfectly working now! So now I know it was linked with my Nvidia driver... It is very nice for the effort of checking the post often, and giving really cool advices, copying the code and stuff. Thanks again man :)

Can set this to "solved now" :)



I'm wondering, is it possible at all to get HDMI to work with an NVIDIA-GPUed laptop on Ubuntu? I'm a little afraid to try again to mess with this driver now ;)

---

### Post by BC59 on 2012-01-25
I'm not sure for this driver.
In any case the best way to have installed the latest NVIDIA driver is to install it through repository:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
```

---

