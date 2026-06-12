---
title: "How to restore login wallpaper in 12.04?"
date: 2012-04-28
forum: General Help
---

### Post by The Bright Side on 2012-04-28
Hey guys!

I used Ubuntu Tweak to change my login wallpaper in 12.04, and now there's no wallpaper at all on the login screen.

Do you know how I can get the Ubuntu wallpaper back (or the functionality that picks the current user's wallpaper, which stopped working a couple of hours after I installed 12.04, even without my intervention)?

Hope you can help me!

---

### Post by GameX2 on 2012-04-28
Hi,

This usually happen when Ubuntu try to find the wallpaper you've set, but it *can't*.  Perhaps you've put your wallpaper on a partition that isn't mounted as default, for example.

The best is to use a wallpaper in /usr/share/backgrounds.  Still with Ubuntu Tweak, choose the wallpaper you've previously had -  which is probably in this folder.  This should fix the issue.

---

### Post by PhantomTurtle on 2012-04-28
This happened to me as well, but for some reason it worked in the beta. It didn't work for me at all. I was going to make a thread about it as well, but you beat me to it. Hopefully someone has a solution.

---

### Post by GameX2 on 2012-04-28
It work without problem, in my case;

Make sure you copy the wallpaper you want in "/usr/share/backgrounds" as root - Then check the permissions.  When you copy the wallpaper as root, is seems fine, but if you run Nautilus not as root and check in the folder, it can happen that the permissions to the wallpaper you've copied are incorrect (the wallpaper has a padlock on the icon).

Open Nautilus as root, and give all the permissions to the wallpaper.  This solved the problem for me.

Good luck;

---

### Post by fantab on 2012-04-28
OR you can put your images in Pictures folder but the images should be .png only. For some reason .jpeg or .jpg does not work (at least for me) from pictures folder.

---

### Post by PhantomTurtle on 2012-04-28
> **fantab said:**
> OR you can put your images in Pictures folder but the images should be .png only. For some reason .jpeg or .jpg does not work (at least for me) from pictures folder.

.png files did not work for me and jpeg pictures worked fine in the Ubuntu 12.04 beta. Hopefully they will fix it.

---

### Post by GameX2 on 2012-04-28
> **PhantomTurtle said:**
> .png files did not work for me and jpeg pictures worked fine in the Ubuntu 12.04 beta. Hopefully they will fix it.

I used to get a corrupted JPG file when trying to copy it in /usr/share/background; try opening GIMP as root, open your wallpaper, then export it *again* to JPG, directly in /usr/share/backgrounds.

Odd, but worked.  Hope this work for you as well.

---

### Post by PhantomTurtle on 2012-04-28
> **GameX2 said:**
> I used to get a corrupted JPG file when trying to copy it in /usr/share/background; try opening GIMP as root, open your wallpaper, then export it *again* to JPG, directly in /usr/share/backgrounds.

Odd, but worked.  Hope this work for you as well.

For me copying to /usr/share/backgrounds doesn't seem to work either.

---

### Post by The Bright Side on 2012-04-28
GameX2's tip worked for me!

I sudo-ran Gimp, then saved the file I wanted in /usr/share/backgrounds and selected it in Ubuntu Tweak. I changed the permissions, too, but it even works with the images present in the folder by default.

PhantomTurtle, did you change the permissions on the file after saving it in the "backgrounds" folder?

---

### Post by grahammechanical on 2012-04-28
Are you people aware that the option to set a wallpaper as a background image for the login screen only works is you select a static wallpaper. It does not work when we select the wallpaper slider show.

Also, the default background that gets selected is called warty-final-ubuntu.png.

So, if you rename that image to something else and then rename your image to warty-final-ubuntu.png, well that should work as well.

But you need to be root to do this.

Regards.

---

### Post by PhantomTurtle on 2012-04-28
I just installed updates and tried again, this time it works(yes, even with jpeg files). Just run update manager and install all the new updates (well maybe not the Firefox one, but do the rest). It seemed to work fine after that.

---

### Post by Zukaro on 2012-04-28
I'm also having a problem with changing the login wallpaper.
I've copied the image I want to use to /usr/share/backgrounds and used Ubuntu Tweak Tool to change the login screen but it doesn't work (I just get a blank purple screen).
(and I've installed all updates, yet it still doesn't work)

---

### Post by PhantomTurtle on 2012-04-28
> **Zukaro said:**
> I'm also having a problem with changing the login wallpaper.
I've copied the image I want to use to /usr/share/backgrounds and used Ubuntu Tweak Tool to change the login screen but it doesn't work (I just get a blank purple screen).
(and I've installed all updates, yet it still doesn't work)

Well I didn't use Ubuntu tweak, I just set the wallpaper, but this only worked after I installed updates. I'm not sure why this worked but it did. Also I'm using the amd64 version, if it makes a difference.

---

### Post by Zukaro on 2012-04-28
I'm using the same version.  How did you change the login screen wallpaper?
(did you just put a new file in and rename it to the default? (pretty sure someone said they did that))

---

### Post by PhantomTurtle on 2012-04-28
> **Zukaro said:**
> I'm using the same version.  How did you change the login screen wallpaper?
(did you just put a new file in and rename it to the default? (pretty sure someone said they did that))

I just set a picture that was in my Pictures folder as the desktop background and it just worked. This, however did not work before I installed the updates for some reason(but the updates might not have anything to do with it).

---

### Post by Zukaro on 2012-04-28
Okay.
Are you using some program to make what you set as your desktop wallpaper also the login wallpaper?
(I've heard of a program that can do that, although I forget the name)

---

### Post by PhantomTurtle on 2012-04-28
> **Zukaro said:**
> Okay.
Are you using some program to make what you set as your desktop wallpaper also the login wallpaper?
(I've heard of a program that can do that, although I forget the name)

No, however you did need one for Ubuntu 11.10, it was called Simple LightDM Manager. I just opened the image with the image viewer, right clicked on it and clicked "Set as Background" and it worked.

---

### Post by Zukaro on 2012-04-28
Oh.  That doesn't seem to work for me.

---

### Post by micFroloZoome on 2012-04-29
[http://abaywashere.com/social/index.php?p=blogs/viewstory/52539](afetam a imagem real da pele)
 
[http://comsaudebrasil.com/falecomigo/index.php?p=blogs/viewstory/116097](na verdade)
 
[http://jalinansobat.biz.uz/index.php?p=blogs/viewstory/889](exatamente o que deve ser fixado)
 
[http://wikiclase.com/red/pg/blog/beggaiwo/read/106035/certifiquese-de-clicar-em-em](vocé”š precisa ler as alé“†neas seguintes)
 
[http://www.twplinks.com/index.php?p=blogs/viewstory/5876](bem como as suas vantagens)
 
que vocé”š acabou de vestir

---

### Post by Zukaro on 2012-04-29
[https://bugs.launchpad.net/ubuntu-tweak/+bug/888186](https://bugs.launchpad.net/ubuntu-tweak/+bug/888186)

I've managed to get it working based on the posts in there.

The issue is due to a bug.  To get around this issue you need to copy  your wallpaper to /usr/share/backgrounds and then set the permissions to  read only (there's 3 permissions sections, set the last two to read  only and leave the first on as read/write).

That should fix it.

---

### Post by The Bright Side on 2012-04-29
Hey guys,

please also note that we're playing with fire here:
[ubuntuforums.org/showthread.php?p=11887414](ubuntuforums.org/showthread.php?p=11887414)

I f*cked up my whole (desktop) system by messing with the login wallpaper. I'm locked out now and will probably need to reinstall.

(It's fine on my laptop, though I did get the "Logging in..." issue 2-3 times at first)

---

### Post by Pedymerlall on 2012-04-29
[hé…¶jere CO2-stæ°“l](http://forum.bernida-ega.site90.net/index.php?p=blogs/viewstory/1347) [stijl en geeft de klant marketing communicatie](http://crosstalknet.com/community/index.php?p=blogs/viewstory/123442) [Fé…¶lg en ordentlig rutine i forbindelse med tandhygiejne](http://yanasoo.com/Foamvywe/blog/f-248lg-en-ordentlig-rutine-i-forbindelse-med-tandhygiejne/) [som moderne vå¿™rkté…¶jer behov.](http://www.zamalkawyana.com/social/index.php?do=/Foamrozr/blog/som-moderne-v-230rkt-248jer-behov/) [Marmoreret Hund Urner For den kå¿™re Venner](http://crimenewsagency.com/dolphin/blogs/entry/s-vel-som-du-vil-finde-st-rre-typer-for-enkeltpersoner) [http://imsnationwide.com/avareneeplumb.com/blogs/224/5904/n-r-k-ret-jet-hurtigt](http://imsnationwide.com/avareneeplumb.com/blogs/224/5904/n-r-k-ret-jet-hurtigt)

---

### Post by Zukaro on 2012-04-29
> **The Bright Side said:**
> Hey guys,

please also note that we're playing with fire here:
[ubuntuforums.org/showthread.php?p=11887414]("http://ubuntuforums.org/showthread.php?p=11887414")

I f*cked up my whole (desktop) system by messing with the login  wallpaper. I'm locked out now and will probably need to reinstall.

(It's fine on my laptop, though I did get the "Logging in..." issue 2-3 times at first)

I read the post you've linked to; you say you've replaced lightdm with gdm?

I don't really know all that much about this stuff, but I've heard lightdm is required for the unity-greeter (which is the login screen).  Try re-enabling lightdm?  I'm not sure if that'd help or not.

Also, once you've done that look at my previous post (on the last page) about permissions and such.  That worked for me without any issues.
(or once you reinstall)


If you use one of the default Ubuntu wallpapers your login screen will change to that like it's supposed to since they have the required permissions and are in the right folder (/usr/share/backgrounds).  Just move the wallpaper you want into there and set the permissions for group and other to read only.  You'll need to be root to move your wallpaper to there, so lets say you've stored your wallpaper in your pictures folder, you'll have to type "sudo mv /home/username/Pictures/wallpaper.jpg /usr/share/backgrounds" (make sure there's a space between your first string (/home/Pictures/wallpaper.jpeg) and the second one).  This should work.  Setting permissions should be much more simple; just right click, go to permissions and set groups and other to read only (you should have read/write permissions on this file as you're still the owner, but you've moved it into a folder owned by root).

If you want your wallpaper to be the same as your desktop wallpaper then just move your wallpaper into the backgrounds folder and after setting the permissions choose it for your desktop and it will automatically be set as your login screen wallpaper also.

---

