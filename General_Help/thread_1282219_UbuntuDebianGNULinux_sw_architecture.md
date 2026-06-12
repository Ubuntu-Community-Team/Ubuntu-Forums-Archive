---
title: "Ubuntu/Debian/GNU/Linux sw architecture"
date: 2009-10-04
forum: General Help
---

### Post by saphxx on 2009-10-04
Hello, I'm new to Ubuntu (and Linux in general). I'm trying to familiarize myself with OS and I tried to find some overall design documents with no luck.

I'd be interested in documents which tell how different SW modules relate to each other (some architecture pictures maybe) and what are the roles of those, and also who provides them.

I found some brief explanations which tells that Ubuntu consists of Linux kernel, Debian, etc... But as a programmer I'd be interested to go more in detail.

Here are two pictures of Maemo architecture, these are kinda what I'm looking for:

[http://maemo.org/maemo_training_material/maemo4.x/html/maemo_Technology_Overview_Chinook/images/intro_sw_stack.png](http://maemo.org/maemo_training_material/maemo4.x/html/maemo_Technology_Overview_Chinook/images/intro_sw_stack.png)
and
[http://static.maemo.org/static/0/07f3bd0a449211dd858543096c880b980b98_maemoarchitecture.png](http://static.maemo.org/static/0/07f3bd0a449211dd858543096c880b980b98_maemoarchitecture.png)

Thx for the replies beforehand!

---

### Post by saphxx on 2009-10-04
.. Should I ask this from some other area? Programming maybe?

---

### Post by saphxx on 2009-10-04
Yet one try...

---

### Post by Xzenome on 2009-10-04
I get what you're looking for, I just don't know of anything that exists.

I'll explain the best I can.

Ubuntu consists of a load of things. Coming from a Windows background, this can be a bit of a strange approach. With Windows, for most users even the more technical ones, you just have Windows and that handles everything that the end user doesn't even want to think about and then you have applications which are what the end user uses. In Ubuntu, because the open source world is so diverse, the "system" is made up of loads of different parts. I'll make a non-exhaustive list:
[LIST]
[*]The Linux Kernel - this handles all of really basic functions and most of the drivers
[*]The X Server - this handles the graphics (like the windows and such), it works with the video drivers in the kernel to provide this. It also handles keyboard and mouse input. It is actually quite basic though in some ways, for example, things like putting the borders around windows is actually done by other applications (like Compiz or Metacity).
[*]PulseAudio - this handles the sound. Applications feed PulseAudio the audio that they want played and Pulse adjusts the volume, mixes the streams of audio etc. and then delivers it to the sound drivers to play it to the user. It also deals with incoming audio (from microphones etc.)
[*]CUPS - this does all of the printing. It accepts jobs from programmes and then either prints them, queues them or sends them to a network printer.
[*]DBUS - this provides a way for applications to communicate with each other. This may be similar to COM on Windows, I'm not sure, not being a Windows programmer.
[*]V4L - Video for Linux deals with things like webcam input. I think this may be part of the kernel.
[*]DeviceKit - this deals with things like power management, this job used to be done by something called HAL.
[*]NetworkManager - this manages the networking (things like wireless and wired connections)
[*]aptitude/apt-get/dpkg - these tools form the packaging system of Ubuntu, they manage the installation, updates and removal of all of your programmes.
[/LIST]

Then you have things that provide the desktop experience. These are projects like Gnome and KDE. They provide the panels (like the taskbar I suppose), menus, a desktop and suchlike. You have a lot of choice when it comes to these - there are a lot of them. Also, unlike on Windows, they do a lot. For example, the default installation of Gnome (this is what Ubuntu comes with) provides panels, menus, a weather applet, a mail programme, a load of games, a good text editor, a good graphics editor (more like Photoshop than Paint), an instant messaging programme (for MSN, Yahoo, AIM, XMPP and a load more protocols), a music player (more like iTunes than WMP), a media player, a CD burner, a sound recorder and a load of applications to administer your system. Ubuntu then adds applications like Firefox and OpenOffice, giving you an operating system install than can actually be used straight after an install (without installing a load more packages). 

Then there are all of the libraries, I won't go into detail about them.

The relationship between Ubuntu and Debian is this:
Upsteam &#8594; Debian &#8594; Ubuntu

Basically, Ubuntu is made up of thousands of different open source projects. These are referred to as "upstream". The developers of these individual projects release the source of their projects. Someone then has to collect all of these different sources and make sure they can all work in harmony (not necessarily with each other, just not killing each other). That's what the Debian project does. You can just stop there, get a copy of Debian and use that. However, some people, of which I'm one, think that Ubuntu is more user friendly and more regularly updated (Debian doesn't publish new versions as often as Ubuntu). So Ubuntu takes all of Debian's brilliant work and builds on it.

Some people may point out errors in this, I wouldn't be surprised... It's a lot to explain. I hope this gives you a rough guide though.

---

### Post by saphxx on 2009-10-05
Thanks for your answer! There were some points that were new to me.

I continued searching for few hours yesterday but couldn't find what I was looking for (maybe there isn't that kind of document/picture, as you also thought). So I quess I'll just have to crawl through more documents and try to get the overall picture of Ubuntu to my head :)

---

### Post by bab1 on 2009-10-05
> **saphxx said:**
> Thanks for your answer! There were some points that were new to me.

I continued searching for few hours yesterday but couldn't find what I was looking for (maybe there isn't that kind of document/picture, as you also thought). So I quess I'll just have to crawl through more documents and try to get the overall picture of Ubuntu to my head :)

A quick Google of Maemo shows that it is a SDK that uses Gnome and Debian Linux libraries.  Ubuntu is for the most part a packager of various projects as *Xzenome* has pointed out.

If you are looking to develop a project within Gnome then [**_this_**]("http://library.gnome.org/devel/guides") is a good starting place.

In the little that I have read Maemo was started by a Gnome developer Miguel de Icaza.  His blog is [_http://tirania.org/blog/_]("http://tirania.org/blog/") or you might try contacting him at miguel[COLOR="green"]**(at)**[/COLOR]gnome.org.

---

