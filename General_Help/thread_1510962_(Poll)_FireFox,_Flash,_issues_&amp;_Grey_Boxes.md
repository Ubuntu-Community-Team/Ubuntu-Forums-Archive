---
title: "(Poll) FireFox, Flash, issues &amp; Grey Boxes?"
date: 2010-06-16
forum: General Help
---

### Post by PinchedNerve on 2010-06-16
Hello.

     I've been having some issues with FireFox & Flash. I am wondering if many people are having the same issues that I am. Below you'll see a couple pictures of my issues. The issue I have is that when Flash is present in FireFox I get grey boxes. Usually it tends to cover up text on forums or other websites & it starts as soon as I start scrolling the page. Tried multiple flash installs & multiple ways to remove installs, so far all are unsuccessful. Please vote if this issue happens to you & if you have another issue, please feel free to post it.

[IMG]http://img.photobucket.com/albums/v141/Devourer/IMG_0590.jpg[/IMG]

[IMG]http://img.photobucket.com/albums/v141/Devourer/IMG_0589.jpg[/IMG]

Sorry about having to take pictures, I would have taken screen shots but every time I did the grey boxes would disappear.

Edit:  Please leave info about your Ubuntu OS version & computer hardware, & what you've tried if you have any issues.

I have 4 Computers, 3 are desktops running 10.04 x64, 2 with Core 2 Duo's & 1 AMD 3500+. The AMD 3500+ has an nVidia 8600GT. THe 2 Core 2 Duo's, 1 has an ATI 4870 & the other has a nVidia 200 (something or other). Last computer is a Netbook running Netbook Remix & [it can't run FF at all]("http://ubuntuforums.org/showthread.php?t=1479514").



[COLOR="Red"]Edit: Doing a search I found some threads with this same issue.[/COLOR]

[Grey flickering boxes]("http://ubuntuforums.org/showthread.php?t=1488520&highlight=grey+boxes")

[Hebrew shown LtR in Ubuntu netbook remix 10.4]("http://ubuntuforums.org/showthread.php?t=1462185&highlight=grey+boxes") (post #4 specifically)

[64-bit Flash for Karmic]("http://ubuntuforums.org/showthread.php?t=1332870&highlight=grey+boxes") (This one goes back to 2009)

---

### Post by philinux on 2010-06-16
To sort out flash use this.
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

However the grey boxes look more like a graphics card driver issue. There is no flash on the forums and it looks like left over tooltips.

---

### Post by AnoPoli on 2010-06-16
Are you using firefox and flash from the official repositories?
If yes try to use Firefox and Flash from the original sites,
then post back again.
I would recomment you to unzip firefox in /opt and run it from there.
In case it works better, you would only have to update your links.

---

### Post by PinchedNerve on 2010-06-16
> **philinux said:**
> To sort out flash use this.
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

However the grey boxes look more like a graphics card driver issue. There is no flash on the forums and it looks like left over tooltips.
I was using that, but I still have the Grey Box issue.

I've tried this, the repositories, terminal code & I still get this problem.

1 thing I would like to ask. I keep seeing people say not to use the repositories. This is puzzling to me, why would the repositories be such an issue for Flash? Just how often would Adobe be releasing Flash updates for everyone to say not to use the repositories?

Lastly, I am starting to think the issue isn't Flash at all & the problem is with FF because I do not have any issues in Chrome.

---

### Post by philinux on 2010-06-16
I don't think it's flash either. The one in the repo is the latest version from adobe anyway. 10.1 r53

It could be an addon. Try running firefox in safe mode.

```
firefox -safe-mode
```

What graphics card is it. Check the driver in sys>admin>hardware drivers.

You could try turning off tooltips in FF.

```
about:config
```
Filter = browser.chrome.toolbar_tips and set it to false. You can easily change it back to true.

---

### Post by PinchedNerve on 2010-06-16
Just a shot in the dark here, but another thread I looked at "[Adobe Flash Plugin Problem: menu buttons]("http://ubuntuforums.org/showthread.php?t=1510263&highlight=flash+problem")" mentions about Ubuntu extra's being 32bit only. I do install these through terminal. I'll test this out if someone would be kind enough to tell me how to reverse the Ubuntu Extra's install?

BTW: I've tried disabling all addons as well a creating another user & trying FF. Still got the grey boxes.

---

### Post by warfacegod on 2010-06-16
I don't think this is a Flash issue either. I very rarely get this also but *only* in the Forum. I'm fairly sure it only happens when I have Compiz enabled and I'm running several apps, using at least 600 MB of my 2 GB RAM and with a torrent running, it really means that my RAM is full.

Basically, what I think is happening is that I'm taxing the hell out of my puny nVidia Go5200 64 MB video card.

Although, this might be (and I stress *might*) a Forum specific problem.

I'll go with philinux on this and suggest disabling "Tooltips".

---

### Post by John Bean on 2010-06-16
> **philinux said:**
> However the grey boxes look more like a graphics card driver issue. There is no flash on the forums and it looks like left over tooltips.

I agree. I used to get something similar occasionally with ATI restricted drivers in Jaunty, but in Lucid the drivers work perfectly. It didn't affect all apps equally but it did affect Firefox, Google Earth (worst) and to some others.

I have no issues at all with Firefox in Lucid.

---

### Post by ajgreeny on 2010-06-16
Flash is good here. Sempron 2400+, 2GB ram, ATI 9200SE card with open source driver.

Gnome on 10.04.

---

### Post by PinchedNerve on 2010-06-16
> **warfacegod said:**
> I don't think this is a Flash issue either. I very rarely get this also but *only* in the Forum. I'm fairly sure it only happens when I have Compiz enabled and I'm running several apps, using at least 600 MB of my 2 GB RAM and with a torrent running, it really means that my RAM is full.

Basically, what I think is happening is that I'm taxing the hell out of my puny nVidia Go5200 64 MB video card.

Although, this might be (and I stress *might*) a Forum specific problem.

I'll go with philinux on this and suggest disabling "Tooltips".

I get this on 3 desktops. My main has 4 gigs of memory, E8400 Core 2 Duo, & an ATI 4870. As I mentioned up top, the 2 other Desktops have nVidia cards.  Its not a V-card driver issue.




> **John Bean said:**
> I agree. I used to get something similar occasionally with ATI restricted drivers in Jaunty, but in Lucid the drivers work perfectly. It didn't affect all apps equally but it did affect Firefox, Google Earth (worst) and to some others.

I have no issues at all with Firefox in Lucid.

Please see my reply directly above.

---

### Post by warfacegod on 2010-06-16
Okay. Did you disable Tooltips like philinux suggested?

---

### Post by PinchedNerve on 2010-06-16
I'll try this as well if someone could tell me where Compiz, is?

> WORKAROUND 1: Disable compiz
WORKAROUND 2: Remove flashplugin-nonfree / flashplugin-installer and install from adobe
WORKAROUND 3: Open a terminal and enter:

gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Then add: export GDK_NATIVE_WINDOWS=1 before the last line of text

---

### Post by warfacegod on 2010-06-16
Disable Compiz = right click desktop> select Change Desktop Background> Visual Effects tab> set to None.

Convenient way, download Compiz Switch. Google it.

---

### Post by PinchedNerve on 2010-06-16
> **warfacegod said:**
> Disable Compiz = right click desktop> select Change Desktop Background> Visual Effects tab> set to None.

Convenient way, download Compiz Switch. Google it.

[Ah!!!  Ya, I figured that out a while ago.]("http://ubuntuforums.org/showthread.php?t=1491482")

Also did this: 

gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Then add: export GDK_NATIVE_WINDOWS=1 before the last line of text 			 		

Still got the grey boxes.....

---

