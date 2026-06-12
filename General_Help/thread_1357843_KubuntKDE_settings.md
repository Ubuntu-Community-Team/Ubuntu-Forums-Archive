---
title: "Kubunt/KDE settings"
date: 2009-12-17
forum: General Help
---

### Post by Knowle on 2009-12-17
I've been using Kubuntu for about 3 days now it's pretty nice few weird issues though.

->When I first boot up my laptop and login I have to put in my password for KwalletManager so it will connect to my wireless, is there a way to bypass it or always give it access for that specific task?

I also tried unchecking the enable kwallet option but then it wants me to put in my WPA key each time.

->When right clicking a webpage and saving an image  the whole screen dims with only a single menu box highlighted for the action your taking, is there a way to turn that off?

->Is there a “light weight” text editor similar to gedit in gnome?

->There doesn't seem to be any kind of “right click &#8594; set as desktop background” as I found in Ubuntu when either using the action from a webpage or on an image already saved to the hdd.

->Title bar text in Firefox messes up at times and gets “scrambled” is this  a bug in Kubuntu or is it just happening to me?

->Are there no touchpad settings? Mainly to turn off edge scrolling and/or tap to click

Is it just me, or does anyone else have trouble going to tvguide.com, then select whats on tv/tv listings and try hitting the arrow button just above the grid to go forward in the guide. It doesn't work in Firefox on my Kubuntu install, in my previous Ubuntu install, or on my desktop running Windows XP. It works in Konqueror and Chrome.

---

### Post by SuperSonic4 on 2009-12-17
> ->When I first boot up my laptop and login I have to put in my password for KwalletManager so it will connect to my wireless, is there a way to bypass it or always give it access for that specific task?

Not too sure but you might be able to in System Settings --> KDE Wallet

> ->When right clicking a webpage and saving an image  the whole screen dims with only a single menu box highlighted for the action your taking, is there a way to turn that off?

I think that's a firefox thing more than a KDE thing

> 
->Is there a “light weight” text editor similar to gedit in gnome?

Kate or KWrite.

> ->There doesn't seem to be any kind of “right click &#8594; set as desktop background” as I found in Ubuntu when either using the action from a webpage or on an image already saved to the hdd.

->Title bar text in Firefox messes up at times and gets “scrambled” is this  a bug in Kubuntu or is it just happening to me?

As far as I know that's you, firefox works fine for me.

> ->Are there no touchpad settings? Mainly to turn off edge scrolling and/or tap to click

Have you installed *input-synaptics* or similar? I don't have my laptop on so I cannot verify

> Is it just me, or does anyone else have trouble going to tvguide.com, then select whats on tv/tv listings and try hitting the arrow button just above the grid to go forward in the guide. It doesn't work in Firefox on my Kubuntu install, in my previous Ubuntu install, or on my desktop running Windows XP. It works in Konqueror and Chrome.

No trouble here

---

### Post by _sAm_ on 2009-12-17
> ->There doesn't seem to be any kind of “right click &#8594; set as desktop background” as I found in Ubuntu when either using the action from a webpage or on an image already saved to the hdd.
In upcoming KDE 4.4 you can drag a picture to the desktop to add it as wallpaper(and have different wallpapers on the virtual desktops).

---

### Post by Zorael on 2009-12-18
> **Knowle said:**
> ->When I first boot up my laptop and login I have to put in my password for KwalletManager so it will connect to my wireless, is there a way to bypass it or always give it access for that specific task?
Use the wallet, but set the password blank. Then set it to always allow wallet access to the networking manager.

> **Knowle said:**
> ->When right clicking a webpage and saving an image  the whole screen dims with only a single menu box highlighted for the action your taking, is there a way to turn that off?
This is a KWin effect. System Settings -> Desktop -> Desktop Effects -> Effects, uncheck "Dialog Parent".

> **Knowle said:**
> ->Is there a “light weight” text editor similar to gedit in gnome?
KWrite. Kate is a bit more powerful with the ability to have several files open at once in a tabbed-esque manner, but also heavier. They both use the same text rendering [kpart](http://en.wikipedia.org/wiki/Kpart) (katepart), but other features differ.

> **Knowle said:**
> ->Are there no touchpad settings? Mainly to turn off edge scrolling and/or tap to click
Not officially, no, and I'm not sure why. However, there is [a third-party touchpad System Settings module](http://www.kde-apps.org/content/show.php?content=113335) that's not part of the official software compilation. There's [a launchpad bug](https://bugs.launchpad.net/ubuntu/+bug/448762) about it not being packaged for Ubuntu, and while "declined", [there are supposedly plans](https://wiki.kubuntu.org/Kubuntu/Specs/LucidTouchpadConfig) for it to be included per default in Lucid (and not packaged separately).

The author links to [his own ppa](https://launchpad.net/~mishaaq/+archive/ppa/) which includes testing packages of it, but they're compiled for Jaunty. If you're running Karmic, you could probably still just add it as a Jaunty repo and install the package (**kcmtouchpad**). Alternatively, use [Dominik Stadler's PPA](https://launchpad.net/~dominik-stadler/+archive/ppa/) (which I found by doing [a ppa search](https://launchpad.net/ubuntu/+ppas?name_filter=kcmtouchpad)). He seems to have copied the author's package and had it recompiled for Karmic.

---

### Post by Knowle on 2009-12-19
Mmm..Zorael my man, you've saved me some major annoyances. <3

I had to look up how to change the password in kwallet, a quick google saved me there. I'm a KDE/Linux newb, just when I finally got to understand the Gnome menus using Ubuntu but I had the urge to switch. ;P

Thanks to everyone else who replied as well.

---

### Post by Knowle on 2009-12-24
Well seems I'm having trouble again now. When I start my laptop up after the desktop loads I get a pop-up asking if I want KDE to forget my sound device. I've never gotten it before I don't know why it's showing up now. I found this thread here [http://ubuntuforums.org/showthread.php?t=1192613](http://ubuntuforums.org/showthread.php?t=1192613) so I assume it would ok if I just checked "Don't ask again" and hit No, right?

[[IMG]http://img189.imageshack.us/img189/3661/sounddev.th.png[/IMG]](http://img189.imageshack.us/i/sounddev.png/)

My second problem is that my wireless isn't connecting automatically again. At start up the default icon showing is for ethernet showing its disconnected and wireless shows that its enabled but not connected to my network. The only way I can connect is if I go into networkmanager and delete my wireless network, then reconnect to it and of course retyping my WPA key.

That happens everytime I start my laptop up and apparently as it just happened, after I log back in from the session being locked. Kubuntu is beautiful, but it really does hate me. I never had any problems with Ubuntu. :(

---

### Post by cloggie on 2010-01-16
Hi,

Since awhile I got these same problems, I mean, the one with the soundcard in Kubuntu 9.10.
For some reason this seams to give problems with KNetworkmanager because whenever I startup my laptop and I see that KNetworkmanager is not conecting then within a few seconds the popup appears saying that there is a problem with my sounddevice and that it should be removed from the list. When I click on the Yes button, KNetworkmanager is able to connect to my router.
This just happened in the last few weeks or so. 
Could this be because of some upgrade to my system maybe? Some "lib" that is replaced and interfering the sounddevice with the wifi?

Thanks, Cloggie.

---

### Post by x19mark on 2010-02-16
Hi,

No--it isn't just you, Knowle! TV GUIDE's Listings Grid arrows didn't work for me, either, when I used ubuntu 9.10 and Firefox. The little "favorite channels" hearts didn't work either: Clicking on them didn't make them redder. It was so frustrating!  ](*,)Those little "back" and "forth" arrows had worked perfectly with Safari (Mac OS X v10.5.6 Leopard up to v10.6.2 Snow Leopard) and with Firefox in openSUSE 11.2. I thought that it was ubuntu's fault (it does have its faults). In this case, the problem was not with ubuntu.

To make a long story short(er), I uninstalled "NoScript!". Then I set Firefox up to not only accept Web sites' cookies, but to also accept third-party cookies (and keep them only until I closed Firefox). Finally, I completely cleared the history of my browsing by putting a check mark into the check box next to "Clear histo_r_y when Firefox closes", clicking on the nearby "Se_t_tings..." button, putting check marks into every empty check box, clicking the "OK" button, clicking the "Firefox Preferences" dialog box "OK" button, closing or quitting Firefox, and, finally, opening Firefox. (I didn't forget to remove the check mark from the check box next to "Clear histo_r_y when Firefox closes"! :wink:)

In other words, I just let TV GUIDE's Web site "rip". It worked!! \\:D/

I'm very selective about the Web sites that I "enter". Among other things, I now use the Firefox add-on, LinkExtend.

Have a lot of fun!

Mark

Update: As I don't know how your Web browser is set up--what your preferences are, which add-ons you're using, etc.--I can't be sure why your little back/forth arrows in tvguide.com's Listings Grid don't work. I can, however, figure out why my arrows don't work. I no longer think that NoScript! was the cause of the problem (though I haven't yet fully examined it). I now suspect that my having disabled third-party cookies (preventing Firefox from accepting third-party cookies) caused my arrows to not work. Check this mozilla Web page out (it's very interesting): [http://support.mozilla.com/en-US/kb/Disabling+third+party+cookies?style_mode=inproduct](http://support.mozilla.com/en-US/kb/Disabling+third+party+cookies?style_mode=inproduct)

I just discovered that YAHOO! TV has a very nice TV Guide ("TV LISTINGS")! :grin:

---

