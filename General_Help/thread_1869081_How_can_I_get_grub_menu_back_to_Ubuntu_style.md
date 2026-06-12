---
title: "How can I get grub menu back to Ubuntu style?"
date: 2011-10-25
forum: General Help
---

### Post by fallenshadow on 2011-10-25
I want to get the Ubuntu menu back to the Ubuntu style. At the moment its Debian style which I don't like.

I used the command:
> sudo update-grub

and it found an image at: /usr/share/images/desktop-base/desktop-grub.png

However all the images here are Debian images.. anyone know how to restore the normal grub menu style?

---

### Post by Mark Phelps on 2011-10-25
There is no "normal GRUB" image.  GRUB is text-based.

If what you're asking is how to change the GRUB background, an easy way to do that is to install Grub Customizer and use the Preferences option to browse for and select an image file.

---

### Post by fallenshadow on 2011-10-25
Is there no way to restore the original background image?

---

### Post by cryptotheslow on 2011-10-25
What original image? I've used a few versions of Ubuntu now and the GRUB2 menu has not had any background unless I deliberately added one. At least as far as I remember :)

When did the image change for you? Did you do a distribution upgrade or something?

You might find the image you are looking for in:
/usr/share/images/grub

Then use Mark Phelps suggestion to get it loading up by GRUB2 or one of the many other tutorials littered around the internet or on here - although I've yet to see one specific to Ubuntu 11.10. Just make sure it is a GRUB2 (GRUB v1.98+) tutorial not GRUB.

---

### Post by drs305 on 2011-10-25
As with the previous posters, I don't know of a 'default' Grub 2 background. However, if you have just 'dropped' an appropriate image file into the /boot/grub/ folder Grub 2 will probably use it automatically.

You can set one in /etc/default/grub with the following setting:
> GRUB_BACKGROUND=</path/filename>
Use a png, jpg or tga file with the correct path and filename, then save the file and update-grub.

Here's a link to a forum guide I wrote on how to use background images in Grub 1.99, including the 'drop in' option for placing one in /boot/grub:

[http://ubuntuforums.org/showthread.php?t=1739412]("http://ubuntuforums.org/showthread.php?t=1739412")

---

### Post by fallenshadow on 2011-10-25
Well maybe I confused people be calling it a background but the default Ubuntu has plain purple behind it and not the Debian background.

Somehow I fixed this... I compiled Grub customizer and tried to set a background image. It failed to do so but the original purple is back. :D

---

### Post by rplantz on 2011-10-25
I believe that fallenshadow is referring to the login screen. Mine has also switched to the Debian background image. The only thing I know that may have caused this is my installing xfce. (Can't be sure; I did not keep accurate notes.)

I'm still looking for a way to change this. I'm not sure what fallenshadow means by "compiling Grub customizer" but there must be a better way besides recompiling a program.

Edit: Okay, I found the image file:
```

/usr/share/images/desktop-base/login-background.svg

```
I'm guessing that just removing this file from this location will solve the problem. I'm in the middle of a download now so cannot check.

---

### Post by drs305 on 2011-10-25
@ rplantz,

You can install Grub Customizer without compiling. You can add Daniel Richter's ppa and install as you would any other software.

The background image used by Grub is, in priority:
[LIST]
[*]Designated by GRUB_BACKGROUND in /etc/default/grub
[*]A suitable image file found in /boot/grub
[*]/usr/share/images/desktop-base scripts
[*]/usr/share/images/desktop-base default image
[/LIST]

You might want to quickly check the priorities before the 'desktop-base' image just in case one of those is responsible for the image you are seeing.

---

### Post by cryptotheslow on 2011-10-25
Well as the reference is to a purple background I think you are correct rplantz about it being the login screen. Can't see how doing anything at all with GRUB2 would have any effect on that.

Does anyone sit at the login screen long enough to worry about what it looks like :confused:

It's all a bit mysterious still - might help if we knew what version of Ubuntu we are even talking about :D


Edit: Oh..  11.04....   still a mystery :D

---

### Post by Is Mise on 2011-10-25
@cryptotheslow: No he means GRUB, by default in the last few Ubuntu releases GRUB has a purple background colour.

---

### Post by cryptotheslow on 2011-10-25
I'll get my coat on the way out then :D

Anything newer than 10.04 I've been messing with in virtual box so thinking about it I've never had a reason to even see the GRUB2 menu in anything more recent than that.

---

### Post by rplantz on 2011-10-25
> **cryptotheslow said:**
> Well as the reference is to a purple background I think you are correct rplantz about it being the login screen. Can't see how doing anything at all with GRUB2 would have any effect on that.

Since I have a red-green color deficiency, I have trouble distinguishing purple from blue. I will just have to trust others when they say it's purple

> 
Does anyone sit at the login screen long enough to worry about what it looks like :confused:

What? You don't stop and enjoy the beauty of the login screen before you actually log in? ;-)

Anyway, removing the file 
```

/usr/share/images/desktop-base/login-background.svg

```
got rid of the Debian background for me.

---

### Post by rplantz on 2011-10-25
> **rplantz said:**
> Anyway, removing the file 
```

/usr/share/images/desktop-base/login-background.svg

```
got rid of the Debian background for me.

Oops! I was wrong! I had only logged off when I wrote this. Rebooting reminded me of what fallenshadow was talking about.

This removed the Debian background from the login screen, but fallenshadow is right. When grub brings up the choice for which system to boot, there is a portion of the earth at the bottom of the screen, "debian" is at the lower right, and the debian logo is at the top right of the screen. The OS has not even booted yet, so they must be coming from grub. (I still cannot say anything about the colors.)

---

### Post by drs305 on 2011-10-25
You can remove the *desktop-base* package and it will most likely get rid of any images used by Grub which you have not specifically designated in the configuration files or placed in /boot/grub. Don't forget to run update-grub.

---

### Post by fallenshadow on 2011-10-28
Thanks for all the advice folks.. its solved for now!

I was most definitely not talking about the login screen. I was talking about the purple colour behind the grub menu.

Im using Ubuntu 11.10 by the way! :)

---

### Post by rplantz on 2011-10-30
I found exactly where this is coming from:
```

bob@bob-desktop:~$ cat /usr/share/desktop-base/grub_background.sh 
WALLPAPER=/usr/share/images/desktop-base/desktop-grub.png
COLOR_NORMAL=light-gray/black
COLOR_HIGHLIGHT=white/black

```

I copied /usr/share/images/desktop-base/desktop-grub.png to my home directory and viewed it with Image Viewer.

This change in my grub background took place when I installed xfce4. Now that I know exactly where it comes from, I actually prefer seeing it to remind me of Ubuntu's heritage.

---

### Post by fallenshadow on 2011-10-30
Ah interesting that you mention about XFCE4 as I just recently installed it. That must be the cause of the problem alright! :)

---

### Post by rplantz on 2011-10-30
> **fallenshadow said:**
> Ah interesting that you mention about XFCE4 as I just recently installed it. That must be the cause of the problem alright! :)

I was not sure in my earlier response. But I did a clean reinstall of the entire system this time and paid attention to this issue when I installed XFCE4. ;-)

BTW, I had several problems with XFCE4. For example, double-clicking on folders would not open them, and it was flaky on files. I finally removed it. I'm not completely satisfied with Unity, but I want to give it a fair trial. I bad-mouthed Windows for many years and avoided it. Almost a year ago I installed Windows 7 (dual boot with Ubuntu) and have to say that I actually prefer it for some things I do. And it's almost necessary (or a Mac) for things like software that comes with a camera, etc. I shouldn't bad-mouth things I'm not familiar with. :redface:

---

### Post by fallenshadow on 2011-10-31
Yeah I feel the same way about XFCE... it seems actually sluggish now in comparison to Gnome in normal Ubuntu.

Then again its not like there is much developers working on XFCE. I don't really want XFCE to be honest but my brother doesn't really like Unity! :D

Oh yeah I recently setup a dual boot with Windows 7 to try getting my graphics card to work... I was sure that Windows would get it working of course. However I was really surprised when Windows completely crashed whenever I tried installing the Nvidia driver.

For now Ubuntu is the better gaming OS for me! :D At least the opensource Nvidia driver works and I can play some games! :)

---

