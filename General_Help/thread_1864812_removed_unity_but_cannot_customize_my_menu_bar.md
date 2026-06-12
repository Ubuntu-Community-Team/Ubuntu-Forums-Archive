---
title: "removed unity but cannot customize my menu bar"
date: 2011-10-19
forum: General Help
---

### Post by nethero on 2011-10-19
I upgraded to 11.10 and since I hate Unity so very much I removed it using the [instructions posted here]("http://askubuntu.com/questions/6302/how-can-you-remove-unity").

However, now when I right click on the menu bar at the top of my screen to add things like "show desktop" or to add a launcher, the menu does not give me an option to do this.  Obviously I'm missing a package that contains these options.  Any ideas what it is?

---

### Post by haqking on 2011-10-19
> **nethero said:**
> I upgraded to 11.10 and since I hate Unity so very much I removed it using the [instructions posted here]("http://askubuntu.com/questions/6302/how-can-you-remove-unity").

However, now when I right click on the menu bar at the top of my screen to add things like "show desktop" or to add a launcher, the menu does not give me an option to do this.  Obviously I'm missing a package that contains these options.  Any ideas what it is?

I imagine that is due to the fact you are using Gnome 3.2 and not Gnome 2 used previously.

---

### Post by irv on 2011-10-19
> **nethero said:**
> I upgraded to 11.10 and since I hate Unity so very much I removed it using the [instructions posted here]("http://askubuntu.com/questions/6302/how-can-you-remove-unity").

However, now when I right click on the menu bar at the top of my screen to add things like "show desktop" or to add a launcher, the menu does not give me an option to do this.  Obviously I'm missing a package that contains these options.  Any ideas what it is?

I am not a lover of Unity either, so I dumped it and install Kubuntu 11.10 with KDE, and I still loaded Unity desktop so I could play around with it. But I still don't like it.
Your problem sound like part of what you removed needs to be reinstalled. Sounds like something got broken. Sorry I am not sure what it is. Maybe some one else can help.
[ATTACH]204835[/ATTACH]

---

### Post by nethero on 2011-10-19
> **haqking said:**
> I imagine that is due to the fact you are using Gnome 3.2 and not Gnome 2 used previously.

So maybe this behavior is normal for gnome 3.2?  When I get home I'll check the documentation for gnome 3.2 and see if there is a different way to add the widgets/shortcuts I want to add.

EDIT:
[Says here]("http://www.webupd8.org/2011/08/installing-using-classic-gnome-desktop.html") that I have to Alt-Right Click to add widgets/shortcuts/applets to the gnome panel.  I'll try it as soon as I get home.

---

### Post by Frogs Hair on 2011-10-19
Gnome 3 uses a different panel configuration than Gnome 2 , so the right click add to panel option is not present .

---

### Post by haqking on 2011-10-19
> **nethero said:**
> So maybe this behavior is normal for gnome 3.2?  When I get home I'll check the documentation for gnome 3.2 and see if there is a different way to add the widgets/shortcuts I want to add.

EDIT:
[Says here]("http://www.webupd8.org/2011/08/installing-using-classic-gnome-desktop.html") that I have to Alt-Right Click to add widgets/shortcuts/applets to the gnome panel.  I'll try it as soon as I get home.

yes but you have to install gnome-session-fallback

it doesnt happen just from removing unity

---

### Post by nethero on 2011-10-19
> **haqking said:**
> yes but you have to install gnome-session-fallback

Oh I see.  What exactly does this do?  Based on the description here...

[https://launchpad.net/ubuntu/oneiric/+package/gnome-session-fallback](https://launchpad.net/ubuntu/oneiric/+package/gnome-session-fallback)

it sounds like it modifies gnome activity at login.  Do I really need something like this to add applets that are already included with gnome?  It sounds like a hack of some sort.

---

### Post by haqking on 2011-10-19
> **nethero said:**
> Oh I see.  What exactly does this do?  Based on the description here...

[https://launchpad.net/ubuntu/oneiric/+package/gnome-session-fallback](https://launchpad.net/ubuntu/oneiric/+package/gnome-session-fallback)

it sounds like it modifies gnome activity at login.  Do I really need something like this to add applets that are already included with gnome?  It sounds like a hack of some sort.

removing unity is a hack ;-)

Unity in 11.10 sits on top of Gnome 3.2

all you did was remove unity leaving you with Gnome 3.2 aand things have changed as you have seen.

if you want to use 11.10 and not unity then you need to provide yourself with a way of doing that which you can by installing Gnome-session-fallback and that is detailed in the link you yourself provided or use another GUI such as xfce or whatever or install gnome 3 shell or whatever

11.10 does not use Gnome 2.x.

Thing is you upgraded (i am assuming withou trying it out first) and so if you dont want Unity and dont want Gnome 3.2 then why upgrade in the first place ?

---

### Post by nethero on 2011-10-19
> **haqking said:**
> Thing is you upgraded (i am assuming withou trying it out first) and so if you dont want Unity and dont want Gnome 3.2 then why upgrade in the first place ?

Yes <bows head in shame>, I did upgrade without trying.  I assumed that Ubuntu would allow me to use the classic version of gnome like they did with 11.04.  Unfortunately, I'm finding out the hard way, that this is not the case.  Overall it's been a frustrating user experience since neither Unity or Gnome-shell are remotely usable IMO and Gnome 3.2 does not support any of my favorite themes.  I don't want to switch distros because Ubuntu has been my favorite up until now.  I'm trying as hard as I can to tweak it so I can keep it (hence my constant barrage of questions). But I'm rambling...  The short answer to your questions is...

I upgraded because upgrading provides users with the latest/greatest/most secure software and I assumed there would be an easy way to tweak 11.10 to my liking.  Next time I'll know better.

EDIT:
Found this...
[http://tombuntu.com/index.php/2011/09/11/install-the-classic-desktop-in-ubuntu-11-10/](http://tombuntu.com/index.php/2011/09/11/install-the-classic-desktop-in-ubuntu-11-10/)
Maybe gnome classic is a possibility.  Grrrr.  Can't wait to get home to try this out.

---

### Post by WorMzy on 2011-10-19
Sounds like you'd probably prefer Xubuntu. I certainly recommend that you give it a try:
```
sudo apt-get install xubuntu-desktop
```

It uses XFCE as a desktop environment, which is a lot *like* the GNOME2 desktop environment. After installing it, log out, and choose the XFCE option from the desktop environment list on the login screen.

---

### Post by haqking on 2011-10-19
> **nethero said:**
> Yes <bows head in shame>, I did upgrade without trying.  I assumed that Ubuntu would allow me to use the classic version of gnome like they did with 11.04.  Unfortunately, I'm finding out the hard way, that this is not the case.  Overall it's been a frustrating user experience since neither Unity or Gnome-shell are remotely usable IMO and Gnome 3.2 does not support any of my favorite themes.  I don't want to switch distros because Ubuntu has been my favorite up until now.  I'm trying as hard as I can to tweak it so I can keep it (hence my constant barrage of questions). But I'm rambling...  The short answer to your questions is...

I upgraded because upgrading provides users with the latest/greatest/most secure software and I assumed there would be an easy way to tweak 11.10 to my liking.  Next time I'll know better.

EDIT:
[B]Found this...
[http://tombuntu.com/index.php/2011/09/11/install-the-classic-desktop-in-ubuntu-11-10/](http://tombuntu.com/index.php/2011/09/11/install-the-classic-desktop-in-ubuntu-11-10/)
Maybe gnome classic is a possibility.  Grrrr.  Can't wait to get home to try this out.[/B]



The link you posted is still based on Gnome 3.

Enjoy

---

### Post by robert shearer on 2011-10-19
To the o/p there is a sticky here...
[http://ubuntuforums.org/showthread.php?t=1859961](http://ubuntuforums.org/showthread.php?t=1859961)

Once gnome-session-fallback is installed and running then...

Admin and customisations...
Applications>Other.
Applications>System Tools>System Settings.

For fonts install gnome-tweak-tool

```
sudo apt-get install gnome-tweak-tool
```

**To modify panels alt+right-click. ** this will allow you to add applets/launchers as you want and to move/arrange panels.

---

### Post by nethero on 2011-10-19
[QUOTE=robert shearer]To the o/p there is a sticky here...
[http://ubuntuforums.org/showthread.php?t=1859961](http://ubuntuforums.org/showthread.php?t=1859961)

Once gnome-session-fallback is installed and running then...

Admin and customisations...
Applications>Other.
Applications>System Tools>System Settings.

For fonts install gnome-tweak-tool[/QUOTE]

Okay.  Will try.  Thanks!

[QUOTE=haqking]The link you posted is still based on Gnome 3.

Enjoy[/QUOTE]

Yes, but I'd be willing to stick with Gnome 3.x if I could get the panel customized the way I want.  I'd even stick with the ambiance theme because I've seen some examples of how people can customize it to look similar to clearlooks.

[QUOTE=WorMzy]Sounds like you'd probably prefer Xubuntu. I certainly recommend that you give it a try:[/QUOTE]

Yes, I may try this since I don't want to leave Ubuntu.  It may be the best solution.  I didn't realize it would be so easy to install :)

---

### Post by nethero on 2011-10-19
Okay finally got it all setup the way I like it.  All I need now is to find a theme similar to clearlooks and everything will be right in the world.  Thanks everyone!

---

### Post by haqking on 2011-10-19
> **nethero said:**
> Okay finally got it all setup the way I like it.  All I need now is to find a theme similar to clearlooks and everything will be right in the world.  Thanks everyone!
ambiance and clearlooks are easily installable

Enjoy

---

### Post by nethero on 2011-10-20
> **haqking said:**
> ambiance and clearlooks are easily installable

Enjoy

Ah, that was my next question.  I was playing around with gnome-tweak-tool to try to get clear looks installed but I could not "fully" install it.  Gnome-tweak-tool gave me the option to use it as a windows decoration, but that was pretty much it.  The option to use clearlooks does not show up in the standard Ubuntu themes/wallpaper switcher even though I have clearlooks in my /usr/share/themes folder.  I was assuming that this is because clearlooks is a GTK 2 theme, right?  Is there a config file somewhere I have to edit to get clearlooks to appear in the standard Ubuntu themes/wallpaper switcher so I can fully use it?  Thanks.

---

### Post by haqking on 2011-10-20
> **nethero said:**
> Ah, that was my next question.  I was playing around with gnome-tweak-tool to try to get clear looks installed but I could not "fully" install it.  Gnome-tweak-tool gave me the option to use it as a windows decoration, but that was pretty much it.  The option to use clearlooks does not show up in the standard Ubuntu themes/wallpaper switcher even though I have clearlooks in my /usr/share/themes folder.  I was assuming that this is because clearlooks is a GTK 2 theme, right?  Is there a config file somewhere I have to edit to get clearlooks to appear in the standard Ubuntu themes/wallpaper switcher so I can fully use it?  Thanks.

yeah sorry i dont know why i wrote that, i was thinking of something completely different i had just done with my Debian build.

Yeah clearlooks needs to be ported to gtk 3 and not yet done as far as i know, sorry about that.

but this looks interesting [http://gnome-look.org/content/show.php/Newlooks?content=126920](http://gnome-look.org/content/show.php/Newlooks?content=126920)

---

### Post by nethero on 2011-10-20
> **haqking said:**
> yeah sorry i dont know why i wrote that, i was thinking of something completely different i had just done with my Debian build.

Yeah clearlooks needs to be ported to gtk 3 and not yet done as far as i know, sorry about that.

but this looks interesting [http://gnome-look.org/content/show.php/Newlooks?content=126920](http://gnome-look.org/content/show.php/Newlooks?content=126920)

Thanks for the link.  I think I remember seeing that when I was playing around with themes yesterday.  I also saw this...

[http://gnome-look.org/content/show.php?content=145210](http://gnome-look.org/content/show.php?content=145210)

Also close to clearlooks.  Unfortunately the only way to change the theme to newlooks or clearwaita appears to be through gnome-tweak-tool.  No matter where I extract them, either to the /usr/share/themes or ~/.themes they do not show up in the standard Ubuntu theme/wallpaper switcher.  Also the Ubuntu theme switcher used to have an option to switch the highlight color.  This option appears to be missing so I guess I have to manually edit the .css file.

---

