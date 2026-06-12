---
title: "Windows Boot Loader"
date: 2010-02-14
forum: General Help
---

### Post by Serpher on 2010-02-14
I have a friend trying to install Ubuntu on a computer, but however doesn't want GRUB to show up as apparently his parents know nothing about computers and think he'll break it. I suggested install Ubuntu (he used the live CD for a while), and tell grub to boot from hd0,0 for Windows and hd0,1 for Windows:

```
$sudo grub
>setup (or root don't remember which one comes first) (hd0,?)
>root (hd0,?)
```

After doing hd0,0 he now gets an error when trying to load either Ubuntu or Windows with GRUB. He's using the version that comes with Ubuntu 9.10. Does anybody know how to get the Windows boot loader to start by default right now? He's currently using a live CD.

---

### Post by Dayofswords on 2010-02-14
i dont think windows bootloader can boot linux distros

---

### Post by flippo on 2010-02-14
At my school they have the windows bootloader as the initial bootloader with the options of grub or windows vista, so it is possible, but I have no idea what they went through to get to that point.

---

### Post by HelpMe2000 on 2010-02-14
My problem is, niether will load right now. I load Ubuntu, and I get a black screen and thats it. I load Windows, and it starts up for a bit, doing the microsoft loading thing, then a screen comes up saying; Windows will now check the C Drive. Something from when I installed Ubuntu. After it finishes, thats it. Nothing. Black screen.

---

### Post by HelpMe2000 on 2010-02-14
Okay, it seems that the screen issues have fixed themselves out. But i'd still like to get it so Windows runs automatically instead of having to choose. It's a family cmoputer, and tho I use it the most, I don't want them to know exactly what I've done.

---

### Post by Richard1979 on 2010-02-14
> **HelpMe2000 said:**
> But i'd still like to get it so Windows runs automatically instead of having to choose.

You need to modify the Grub 2 boot list.
The boot order is set in /etc/default/grub but BE CAREFUL.
I'd advise you backing it up by doing "cp /etc/default/grub /etc/default/grub.bak". (under sudo of course)

---

### Post by bobpress on 2010-02-14
If you have Windows Vista or Windows 7, you can restore the Windows bootloader and download and install EasyBCD from NeoSmart [http://neosmart.net](http://neosmart.net).  It will allow you to boot into Windows normally, but have a boot item so you can boot linux also from the usual Windows boot menu.

---

### Post by HelpMe2000 on 2010-02-14
Yeah, just know this. This is my first time actually REALLY using bash, grub, and linux. I'm completely new at this, relying on help from my friend. I don't know any scripting really, and I'd like to get this fixed asap before soemoen realizes whats happened.

---

### Post by oldfred on 2010-02-14
If you refer to Windows by its number, you will have to edit on every update. But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

find your windows entry in this and copy to grub default like this Vista entry in red. Title must be exact that is why it is best to copy.
gedit /boot/grub/grub.cfg
and copy here
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to:
#GRUB_DEFAULT=0
GRUB_DEFAULT="[COLOR=DarkRed]Windows Vista (on /dev/sda1)[/COLOR]"
Then do:
sudo update-grub

---

### Post by HelpMe2000 on 2010-02-14
Okay. Just one question. Where do I copy all that to once I have the grub.cfg open? I'm really new at this, so bear with me.

---

### Post by HelpMe2000 on 2010-02-14
If anyone else has any ideas or can help, I'd be much obliged.

---

### Post by oldfred on 2010-02-15
HelpMe2000
You are opening grub.cfg just to find "your windows"  the exact windows title (similar to the red entry in my example). It will be near the bottom of grub. 
You then copy the exact title of your windows entry into /etc/default/grub as a new line for 
GRUB_DEFAULT= "your windows" 
under the existing line which I add a #, so it is commented out.

---

### Post by HelpMe2000 on 2010-02-15
Okay, after I do this, how would I run Ubuntu again? I want to make sure I know how to do this all before I do something I can't undo.

---

### Post by cj.surrusco on 2010-02-15
Why not install ubuntu inside of windows? That way you would be able to use the windows bootloader.

---

### Post by oldfred on 2010-02-15
We have not hidden the menu, just made the default after 10 seconds boot into windows. If you want to hide the menu or reduce the count down times you need to review all the grub2 settings.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

