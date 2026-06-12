---
title: "Adding splash image to legacy grub ???"
date: 2009-12-10
forum: General Help
---

### Post by madmax.santana on 2009-12-10
I tried to add a splash image to grub2 but I thought it was a bit tricky so I decided to start at a lower level. Since I have been messing around with legacy grub for some time, I reinstalled legacy grub on my system (that's a long and sad story) but I got it installed eventually.
Now, I have read a few tutorials on adding splash image to legacy grub. After careful study of all of them, I did this.

 -- I downloaded a standard splash image which was usplash.xpm.gz
 -- I copied the mentioned image in /boot/grub/images directory.
 -- I edited my menu.lst file and added this line in the file
>  splashimage (hd0,5)/boot/grub/images/usplash.xpm.gz 

Now, when I run update-grub it says that it didn't find any splash image. And of course, there is no splash image at the grub OS choice menu either. Can anyone point what might be the problem?

Adding to it, I know I have installed my grub at (hd0,5)... However, in case, how to find out where grub is installed anyway? Or what should be the text of the > splashimage (hdX,Y)/.../usplash.xpm.gz in my menu.lst anyway?

---

### Post by ranch hand on 2009-12-10
We have a problem here.

You say you are using grub2 but talk about editing your /boot/grub/menu.lst.

Grub2 does not have that file.  That is grub-legacy.

How about running and posting the results here of;
```

grub-install -v

```This will tell us what grub you are using.

If it is grub1.97beta4 we will go from there.

If it is grub0.97 you will have to forget it or go to grub1.97beta4.

Edit;
Adding a splash (background) to grub2 is easy.  You have actually gone to more trouble than needed.

---

### Post by madmax.santana on 2009-12-10
No actually I mentioned I [COLOR=Red]was[/COLOR] using grub2 before but I decided to go back to legacy grub and try adding splash image to it. That was why I [COLOR=Red]uninstalled [/COLOR]my grub2 and [COLOR=Red]installed[/COLOR] **legacy grub** again. right now I am using legacy-grub and that is where this menu.lst file came from.
Anyway here is the output you asked about.
> madmax@Mean-Machine:~$ grub-install -v
grub-install (GNU GRUB 0.97)

See, it's legacy grub...

And once that is decided, what do you mean forget it, man??? :( :( :( I just took a lot of labor and set up legacy grub just because I read it on the forums that it was more that possible to add a splash to the legacy grub... Here;
[http://wiki.debian.org/Grub/SplashImage](http://wiki.debian.org/Grub/SplashImage)
[http://ubuntuforums.org/showthread.php?t=30341](http://ubuntuforums.org/showthread.php?t=30341)

And by the was it was the Ubuntu HOWTO method mentioned above that I tried in order to add splash to my Ubuntu. But something is not working fine. I know it is not a big problem. It's just one small thing that I am overlooking or doing wrong. Can anyone point that out please? Or is there any other method to add splash to grub 0.97?

---

### Post by ranch hand on 2009-12-10
Well, we live and learn (hopefully).

I will tell you what, I still have a couple OS' that run grub-legacy.

My night time production OS does.  Right now I am on my daytime OS (10.04-testing) so that won't work.

When I switch over I will give it a whack and see what I can do.  This is my second testing cycle and you get pretty good at doing different things.

This, by the way, takes about a minute in grub2 if you have the image ready.

You do need to keep in mind that grub-legacy is not supported by the grub project any more.

I am looking forward to this.  It will be a while before I get back on here.  Real life is interfering with my computer time.  Some time tonight.

---

### Post by ranch hand on 2009-12-10
OK, I gave it one whack and it did not work.

When I got thinking about it I had heard of folks doing this so I know it can be done.  I can see why most don't though.  It is a royal pain.

I have a couple theories why it didn't work.  I will be trying them as time allows.

I certainly am not going to give up now.

---

### Post by ranch hand on 2009-12-11
Well, I have had some progress.  I do have the ability to have some weird colored, very small, very irritating pokadots for a background.

I think this is a problem with the image itself (current theory).  It does need to be an xpm file.  It works as well in the existing "splashimage" file as the new "images" file.

I could have done, remotely, at least 3 grub2 images in the time it takes to reboot to check this bugger.  I have no idea what problem you ran into there.  In grub-legacy it is obviously a hack.  Grub2 is actually designed to do this.

None the less, the bit is in the teeth and I will have to run with it.  It will be tommorow night before I fool with it again, but I will be doing some more research.

I really shouldn't be doing this but it is FUN.

---

### Post by madmax.santana on 2009-12-11
@ ranch hand!
That's very nice of you pal. Actually, I am enjoying your step by step sceintific method of solving the problem. I hope you find the answer soon. Am not at my Ubuntu box right now. But I am sure the image I tried was an xpm.

---

### Post by ranch hand on 2009-12-11
Yes that is what you downloaded was.  Thank goodness for Gimp.  I am just trying to put on a plain background that I use for wallpaper images that do not fit my screen right.  I had it in .png and .jpg but not .xpm.

I do now.

These image formats are interesting.  Grub2, as used in 9.10 calls for a .png or .tga image.  When we first got it .tga was all it called for.  Where do the y come up with these things and why?  Gimp can convert to any of them though.

---

### Post by madmax.santana on 2009-12-11
So, ranch hand, you got something on it?
Here is my progress.
In my opinion, the image was alright but I made some mistake while editing the menu.lst file. I have been changing that (hdA,B) argument with many combinations. No luck so far.
As I am not an expert, I can't look deep into it and figure out what the problem was. Therefore I am relying on your analysis pretty much.

Goodluck.

---

### Post by akashiraffee on 2009-12-11
Did you all pay attention to the bit about the color depth, etc?  Grub will reject inappropriate images.  I have a splash that I put in, I remember that being very irritating -- the depth is not the normal depth for an xpm, it is less, and the image MUST be 640x480.

---

### Post by ranch hand on 2009-12-11
Well I am on my Stoned Lizard install right now (I know they call it Lucid Lynx but a bunch of us prefer Lounge Lizard and derivatives for 10.04) so I can't try any thing untill this evening.

But, the guide in the forums is very old.  The thread goes on and I have found some interesting things from page 6 (I have not looked at 5 or before yet) and on to the end.  Page 6 looks like a good place to start.  One of the posters is herman.

He does a lot of research on Linux issues for his blog (I link to his grub2 page as the first link in the link in my sig).  His blog is difficult to navigate but his experimentation is great and he shares it well.

There are some very interesting xmp.gz files available there too.

It seems that the OP of tht thread was working with Warty.  There seems to have been a change in grub-legacy around the time of Hardy.

I am going to try one of those images this evening and I will be surprised if I can't get it to work.

I was not converting my .xmp to an xmp,gz.  I was trying to do that today, here on 10.04 but this testing OS seems to have a bug in that functionality.  I will also be trying that when I get back to a stable release tonight.

---

### Post by ranch hand on 2009-12-11
> **akashiraffee said:**
> Did you all pay attention to the bit about the color depth, etc?  Grub will reject inappropriate images.  I have a splash that I put in, I remember that being very irritating -- the depth is not the normal depth for an xpm, it is less, and the image MUST be 640x480.
Yes and no more than 14 colors.

---

### Post by ST3ALTHPSYCH0 on 2009-12-11
I added a background to my legacy grub... I think that it involved using startup-manager. It's in my Mac4Lin guide. You can d/l it via the link in my sig and read through to that point.

---

### Post by ranch hand on 2009-12-11
```

# Pretty colours
#color cyan/blue white/blue
## Splash image!
splashimage (hd0,5)/boot/grub/splashimages/ibex-splash.xpm.gz

```
Works perfectly in my 9.04.

---

### Post by ranch hand on 2009-12-12
The directions for creating your own image are rather shaky.

Use gimp to get your image at 640x480 and 14 colors (gimp "image" menu>mode>indexed).

Save as .xpm.

I had my image on the Desktop for working on this.  To get your .gz extention on your image you need to cd (in terminal) to where your image is and run;
```

gzip whatever.xpm

```
That will give you the .gz.

It might be a good idea before you try that to make sure "gzip" is installed on your system.

---

### Post by madmax.santana on 2009-12-13
It ain't working with my Karmic. I have tried everything you mentioned here!!! Is it a bug? What? I seem to have got everything right, even then it's not working!!!

---

### Post by ranch hand on 2009-12-13
HMM, first, make sure that you are using grub-legacy by running;
```

grub-install -v

```
It should read grub0.97 or grub.97 for grub-legacy.

Next, I am assuming that the grub version is right, post the entry in the /boot/grub/menu.lst for that "color" section where this stuff gets entered so I can see it.

There are a number of variations that people have had to use to get this to work.  Let us see if we can do some thing on that line.

Did you put the image in /boot/grub/splashimages?  This probably does not matter too much if you got the path right but it is where grub wants them.  This was a change from 05 when that thread was started (Warty which was used by the OP was the first Ubuntu, I think, that came out in 04).

Just to rub it in, in grub2 you put the image in /usr/share/images/desktop-base as a .png (I think .jpg worrks) or .tga (I use a simple file name like "menu.png"), go to /etc/grub.d/05_debian-theme and change the line with the background image in it to read "menu" instead of "moreblue-orbit-grub", change the default color fro the font (optional) and run "update-grub".

---

### Post by madmax.santana on 2009-12-13
Here is my menu.lst from that portion...

> 
.
.
.
.
.
.
timeout        5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu


# Pretty colours
#color cyan/blue white/blue

##Splash Image!!!
splashimage (hd0,5)/boot/grub/splashimages/biospalsh.xpm.gz
.
.
.
.]

---

### Post by ranch hand on 2009-12-13
Try deleting the blank space in the section.  I think that space is not putting you command in that section and that may be keeping it from working.

---

### Post by madmax.santana on 2009-12-16
Still not functional!!!

---

### Post by ranch hand on 2009-12-16
Hmm, I hate to go to an outside app to deal with this but I think I would try SUM at this point.

If it works then look at your me,u.lst and see what was changed.

when you pull up SUM there should be a tab that will let you set the splash (I am not on 9.04 now and it is not installed here on 10.04-testing and I am not going to do it).  But there is a drop down box for all your .xpm.gz files there.  If you just have the one it should be there if the file is good and if it is in the right place.

---

### Post by madmax.santana on 2009-12-17
Thanks ranch hand... But I dunno what is SUM and how to install it. If you could mention that as well, that's be great.

---

### Post by ST3ALTHPSYCH0 on 2009-12-17
**S**tart **U**p **M**anager

---

### Post by ranch hand on 2009-12-17
Apt and synaptic list it as "startupmanager".

---

### Post by madmax.santana on 2009-12-18
I got it. It's done. It shows a nice splash screen without any hitches. StartUpManager did the same to my menu.lst except for one thing.
It has added

> splashimage=/boot/grub/splashimages/myimage.xpm.gz

I was doing "almost" the same...

> splashimage=(hd0,5)/boot/grub/splashimages/myimage.xpm.gz

I guess I didn't need to add that HDD reference because my /boot mount point is the same as my root mount point.
Anyway, I bothered you too much ranch hand. Special thanks to you man! And everybody else who has helped me. I am really obliged.

---

### Post by madmax.santana on 2009-12-18
I have also tried to create my own image and then gzip it and use it as a splash image. It works perfect.
Thanks all. Should I mark this  thread solved now? I think I should :P
Thanks again, a lot.

---

### Post by ranch hand on 2009-12-18
It is fun to learn something new.

It is still easier in grub2.

Thanks for the FUN.

It would be good to go to thread tools (top of page) and mark this "solved" for anyone looking later.

---

