---
title: "Getting Compiz Working in Xubuntu 11.10"
date: 2011-10-16
forum: General Help
---

### Post by Calcipher on 2011-10-16
I am attempting to get Compiz working in Xubuntu 11.10 (sadly for only two plugins, the grid plugin and the window snapping pluggin) and I'm having a bit of trouble.  Off in CCSM I set the window decorator to be gt-window-decorator, but whenever I fire up Compiz all of my window decorations appear to be the clear looks ones instead of greybird (the one I have set).  Changing the theme in the settings manager does change the color of the window decorations, but they remain un-styled.  Does anyone have any advice on this?

---

### Post by gsmanners on 2011-10-16
You ever try "winwrangler"? It's kind of old, but it's in the repos. It looks like it might be what you want. It might be less trouble than trying to get Compiz to work in Xubuntu.

---

### Post by Calcipher on 2011-10-16
I'll take a look at that, thanks for the idea.

---

### Post by ckankiewicz on 2011-10-18
Xubuntu has window snapping without compiz.  Grid on the other hand they do not.

I too tried to get compiz working, but every time I enabled it my window decorations would disappear.  I even made sure to set xfwm4 as the window manager in CCSM.  Any idea what I did wrong?

---

### Post by jamesford on 2011-10-18
if anyones interesting in my approach its smt like this
-install xubuntu
-in xubuntu install ubuntu-desktop (yes i know)
-disable some ubuntu/gnome autostarts and those lame new scrollbars
-keeping gedit as because i like it :)
-this way i have xubuntu and compiz working, using unity-window-decorator as my window borders, sadly theres no more emerald, if there was installing ubuntu-desktop wouldnt be needed
-compiz is rock stable with the unity plugin disabled

if i could figure out how to get unity-window-decorator without installing ubuntu-desktop that would be better of course

[IMG]http://i.imgur.com/xANvq.png[/IMG]
[http://i.imgur.com/xANvq.png](http://i.imgur.com/xANvq.png)

---

### Post by gsmanners on 2011-10-18
I guess that's better than actually being stuck using Unity. :P

---

### Post by jamesford on 2011-10-18
much better, its just like gnome2 with compiz :D

---

### Post by Calcipher on 2011-10-18
I may have to give this a try.

---

### Post by jamesford on 2011-10-18
hey, i dont remember the exact procedure here, was lots of trying and failing, but to get a window manager that isnt xfwm4 and that works with compiz my setting in ccsm > window decoration > command is: 
gtk-window-decorator --replace

i also remember that didnt work right away but after a reboot

i also got the ubuntu notify-osd, dont know how, but i prefer that to the xfce one

thinking of replacing thunar with nautilus as well but havent gotten that far yet

---

### Post by Calcipher on 2011-10-18
I also have gtk-window-decorator, but all of my windows are decorated with what appears to be the clearlooks theme and I can't change them :-/

---

### Post by iamnotthemessiah on 2011-10-18
i know it says gtk-window-decorator --replace but when i ran that in a terminal the output said that it found unity-window-decorator and it used that...

---

### Post by gap on 2011-10-22
Calcipher, you may find useful the instructions at this address:

[http://askubuntu.com/questions/68219/how-do-i-enable-alt-middle-mouse-button-window-resizing-in-xubuntu/68272#68272](http://askubuntu.com/questions/68219/how-do-i-enable-alt-middle-mouse-button-window-resizing-in-xubuntu/68272#68272)

Make sure you read Pablo Zubieta's last comment, the one with the gconftool-2 commands.

If you find a better way, please post here, as I'm interested as well.

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-23
[B]ppa:malteworld/compiz

has emerald... it is a ppa, so it may be kinda iffy.... but I am gonna try it.
[/B]

---

### Post by Calcipher on 2011-10-23
> **TREESofRIGHTEOUSNESS said:**
> [B]ppa:malteworld/compiz

has emerald... it is a ppa, so it may be kinda iffy.... but I am gonna try it.
[/B]

I can't seem to find the reason why, but I'd be wary said ppa. I think it had something to do with the builds of emerald being customized, but I may be remembering wrongly.

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-24
i think they are working on a replacement 4 emerald anyway...  I tried it and it worked.  I don't use it long term, so no telling if there are any major bugs or anything

---

### Post by Calcipher on 2011-10-24
> **TREESofRIGHTEOUSNESS said:**
> i think they are working on a replacement 4 emerald anyway...
Oh?  Any details anywhere!?

---

### Post by kaefert66014235 on 2011-10-27
> **jamesford said:**
> if anyones interesting in my approach its smt like this
-install xubuntu
-in xubuntu install ubuntu-desktop (yes i know)
-disable some ubuntu/gnome autostarts and those lame new scrollbars
-keeping gedit as because i like it :)
-this way i have xubuntu and compiz working, using unity-window-decorator as my window borders, sadly theres no more emerald, if there was installing ubuntu-desktop wouldnt be needed
-compiz is rock stable with the unity plugin disabled

if i could figure out how to get unity-window-decorator without installing ubuntu-desktop that would be better of course


You don't need to install ubuntu-desktop, you get the same effect by using the package compiz-gnome.

But if someone would know a method to start compiz without loading xfwm before that (like described here [https://wiki.archlinux.org/index.php/Compiz#Method_3](https://wiki.archlinux.org/index.php/Compiz#Method_3)) but the methods described here didn't work for me with Xubuntu 11.10

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-27
> **kaefert66014235 said:**
> You don't need to install ubuntu-desktop, you get the same effect by using the package compiz-gnome.

But if someone would know a method to start compiz without loading xfwm before that (like described here [https://wiki.archlinux.org/index.php/Compiz#Method_3](https://wiki.archlinux.org/index.php/Compiz#Method_3)) but the methods described here didn't work for me with Xubuntu 11.10

A useful tool for this compiz biz is the Fusion Icon

sudo apt-get install fusion-icon

Anyhow... here goes

Applications-Settings-Settings Manager-Session and Startup-Application Autostart
or
Applications-Settings-Settings Manager-Session and Startup-Session



enable compiz instead of xfwm

Applications-Settings-Settings Manager-Session and Startup-General

(Check) Automatically Save session on Logout

@Calcipher not sure really about the replacement...  I searched for days about emerald, and tried to figure out what happened and I ran across a post in this forum, where someone was talking about the development of a replacement.  It is probably not a huge priority, with Unity (and the unity decorator ) being the main focus....

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-27
[http://ubuntuforums.org/showthread.php?t=1866889](http://ubuntuforums.org/showthread.php?t=1866889)

here is the post... the person posting it seemed pretty credible to me, being a forum staff member,

---

### Post by jesuisbenjamin on 2012-01-25
Hi there,

I installed Compiz onto Xubuntu 11.10. As a result the default "Greybird" window decoration is overriden by gtk-window-decorator using "Adwaita".
I have found a Gtk Greybird equivalent here: [http://shimmerproject.org/project/greybird/](http://shimmerproject.org/project/greybird/)
Now I am trying to figure out how to install it and change it. I have put the theme into my ~/.themes and used dconf-editor to change the value of gtk-theme at org.desktop.interface from Awaita to Greybird. But no results ... :(

Did I miss something? Can you help?

How come Compiz uses gtk-window-decorator? What is the default decorator of XFCE?

---

### Post by jesuisbenjamin on 2012-01-25
OK I found I could set the window-decoration theme using gnome-tweak-tool

---

### Post by Calcipher on 2012-01-25
> **jesuisbenjamin said:**
> Did I miss something? Can you help?

For me, and I can't claim this will work for anyone else, the solutions was to get the latest version of Emerald window decorator.  I installed that, set the command in Compiz's Window Decorator plug-in to emerald --replace.  I then found the Emerald version of Greybird and set that as default.

I also had to install the Compiz Fusion Icon application and fiddle with what was doing what as far as Window decoration.  After that, everything seems to decorate correctly.

---

