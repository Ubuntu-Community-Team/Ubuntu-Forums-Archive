---
title: "Iron browser 5.0.381 in Lucid 10.04"
date: 2010-09-06
forum: General Help
---

### Post by Dragynn on 2010-09-06
Hello all, just adding a short note to detail this install, some of the other threads are getting a little dated, I added to one but again it's a little lost in the shuffle, i'm new here, so forgive me if I break any protocols and feel free to correct if needed;)

I downloaded the new build of Iron 5.0.381 from here:

[[COLOR="blue"]http://www.srware.net/forum/viewtopic.php?f=18&t=1638[/COLOR]]("http://www.srware.net/forum/viewtopic.php?f=18&t=1638")

and here is the URL for the actual file (32 bit version):

[[COLOR="blue"]http://www.srware.net/downloads/iron-linux.tar.gz[/COLOR]]("http://www.srware.net/downloads/iron-linux.tar.gz")

The install was incredibly straightforward thankfully (i'm a noob to Linux), I simply moved the package from my download file to my home file, opened a terminal and used this code:
```
tar xvfz iron-linux.tar.gz
```

Then closed the terminal, navigated back to my home file where there is now an "iron-linux" file. I opened that and clicked on the Iron executable and it immediately opened and asked if I wanted to import settings, so I imported bookmarks etc. from Firefox and started browsing immediately. That was it, very painless and quick.

I right-clicked after that on my desktop and made a launcher, also added the icon that came in the Iron files as the icon used for the desktop shortcut (product_logo_48.png).

I decided to add the Adblock feature that's now enabled, and here was the first glitch; according to the documentation, the download should have come with an empty "adblock.ini" file that you fill yourself and move to the correct location, well it didn't. So the solution for me was found in the SR Ware forum where I got the download from, I opened a terminal again, started Nano with the simple command:
```
nano
```

And then navigated to the SR Ware recommended adblock.ini file:

[[COLOR="Blue"]http://www.srware.net/downloads/adblock.ini[/COLOR]]("http://www.srware.net/downloads/adblock.ini")

I copied that file, and then pasted it into the new Nano file I had opened. Being new to this, I was unsure how to save it where I wanted with the proper name, I wound up saving it in my home file with the wrong name(nano.save). So I renamed it with a quick right-click, and opened up the terminal again to move it :
```
sudo mv adblock.ini /opt
```

"/opt" being the location it requires to work.

I started it back up, and I can report that it is fast and functional, ads are being blocked (though not quite as smoothly or thoroughly as Adblock for Firefox), flash sites work well and fast (Youtube, Hulu) and I haven't had any glitches so far.

On an old machine with a single core AMD64 2.0 ghz, Nvidia 6200 tc video card, and 1 gig of DDR400, the Peacekeeper scores were:

Firefox = 1138
Iron    = **3272**

Pretty significant difference, and it really shows when browsing.

Hope this info is useful for someone, thanks to all for all the help provided in these forums and Happy Labor Day! ):P)

---

### Post by elliotn on 2010-09-06
Oh.... K I will try it when I get my net back

---

### Post by Chiapo on 2010-10-11
Thanks for the guide! :KS

There's a new version of iron-linux out:

New Iron-Version: 6.0.475.1 Stable for Linux

Link to download:

[http://www.srware.net/forum/viewtopic.php?f=18&t=1824](http://www.srware.net/forum/viewtopic.php?f=18&t=1824)

I'm off to test the differences between Chromium from the Ubuntu repos & SR Ware Iron for linx.

Aloha!

---

