---
title: "Blank splash screen after custom kernel compilation"
date: 2006-06-07
forum: General Help
---

### Post by barros on 2006-06-07
HI all.
I've spent my past few days trying to compile a custom kernel. I'm new to ubuntu, so I got some time. After some trial and erros and finnaly got an "almost" acceptable kernel. I got everything work, my network cards, wireless (rt2570), etc...
The only problem I have now is that the boot splash screen is not showing. The framebuffer is initialized, but I get a blank screen. After a little while this blank screen goes away and KDE shows up. Then, when I reboot, I got this blank screen instead of the kubuntu splash, and sometime, I got a totally weird collored screen, but everything goes right behind the scene..
I have a nvidia GFORCE2. I've compiled the kernel this way:

got the linux-source package, then, make menuconfig, removed some modules, made some optimization (P4 SMP) and then make-kpkg --initrd kenel_image

I think everything is right, I didnt removed any module that I was not sure I could..

anyone experienced this on compiling custom kernel?

PS: I'm using Kubuntu 6.06 Final release

thanks
Carlos Barros

---

### Post by tseliot on 2006-06-07
Try this:

```
sudo nano -w /boot/grub/menu.lst
```

look for this line:

```
# defoptions=quiet splash
```

Remove the word "splash" from it. 

Save and exit: press CTRL+X 

Then type this in Terminal or Konsole:

```
sudo update-grub
```

and restart your computer 

After that, you will have no pretty usplash screen to look at anymore but the blank screen should be gone.

---

### Post by barros on 2006-06-07
Ok, thanks for the answer!
If nothing works I'll do that and remove the splash!

Just one doubt, do I have to enable any specific option in the kernel? One I know is that I have to enable the vgafb (or something, dont remember exactly).. There is another options, called Boot logo, is this option related to this splash screen?

regards
Carlos Barros

---

### Post by barros on 2006-06-07
I think I found the problem, but didnt test it.. 
I was looking through the linux-source package, and it seems to be lacking the bootsplash patch.. I've just searched for it and didnt find. then I got the bootsplash patch and applied successfully. Now, when I do make menuconfig, and can see the bootsplash option. I cant test it right now, but this should be the problem..

regards
Carlos Barros

---

### Post by smylie on 2006-06-08
[QUOTE=barros] I got the bootsplash patch and applied successfully. Now, when I do make menuconfig, and can see the bootsplash option. [/QUOTE]

how did you get on with this? i'm having pretty much exactly the same issue.
if it did work, where do you find the boot splash patch?

cheers
smylie

---

### Post by barros on 2006-06-08
Hi..
actually, i gave up of this!
I've just downloaded a vanilla kernel and will apply the bootsplash patch.. 
The only reason for me to use the linux-source package was becouse the rt2570 support, but it didnt work as expected. Now I'll compile a vanilla kernel and use ndiswrapper, just like I used to use!

regards
Carlos Barros

---

### Post by barros on 2006-06-08
sorry, I forget the link..
[http://http://www.bootsplash.org/]("http://www.bootsplash.org/")
and there is a tutirial (in portuguese only) about this here:
[http://www.guiadohardware.net/artigos/308/]("http://www.guiadohardware.net/artigos/308/")

Keep in mind that bootsplash is not the same as usplash (that is used in ubuntu).

regards
Carlos Barros

---

### Post by smylie on 2006-06-09
[QUOTE=barros]sorry, I forget the link..
[http://http://www.bootsplash.org/]("http://www.bootsplash.org/")
and there is a tutirial (in portuguese only) about this here:
[http://www.guiadohardware.net/artigos/308/]("http://www.guiadohardware.net/artigos/308/")

Keep in mind that bootsplash is not the same as usplash (that is used in ubuntu).

regards
Carlos Barros[/QUOTE]

ahh, in that case, any ideas how to get usplash going again? or did it just work for you once you went back to the vanilla kernel?

---

### Post by madonion87 on 2007-04-06
i would really want to know how to fix the splash screen too

---

### Post by skibrianski on 2007-05-22
> **madonion87 said:**
> i would really want to know how to fix the splash screen too

This is bizarre. I'm having this problem on two machines, one amd64, the other x86. Here's hoping the bump in this thread will do something...

---

### Post by skibrianski on 2007-05-22
Could this be something related to restricted drivers not loading? B/c on my laptop I also don't get wireless support on the kernel I built.

I've been following the instructions here:
  [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

But my guess is those instructions don't cover how to make restricted drivers work properly...

---

### Post by skibrianski on 2007-05-22
This looks promising, altho I haven't tried it yet so I can't vouch for it.

[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)

Scroll down to the bit about restricted drivers.

---

### Post by skibrianski on 2007-05-22
At last, I found ze solution!

[http://ubuntuforums.org/archive/index.php/t-24534.html](http://ubuntuforums.org/archive/index.php/t-24534.html)

echo vesafb | sudo tee -a /etc/initramfs-tools/modules
echo fbcon | sudo tee -a /etc/initramfs-tools/modules
sudo dpkg-reconfigure your-linux-package-name #e.g. linux-image-`uname -r` for the running kernel

---

### Post by iDleR on 2007-09-18
Hi, did you try to use the linux-source from ubuntu repository? Maybe the patch is applied there.

---

