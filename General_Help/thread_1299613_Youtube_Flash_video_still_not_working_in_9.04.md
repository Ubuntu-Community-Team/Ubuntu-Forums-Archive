---
title: "Youtube Flash video still not working in 9.04"
date: 2009-10-24
forum: General Help
---

### Post by bingung99 on 2009-10-24
Hi

I have been trying to get Youtube and other video sharing sites to work on 9.04...me have tried suggestions on the Ubuntu community help website...installing flash-plugin-nofree, the restricted-extras, gnash....Problem is only some videos played OK...but most of the links will give me a black screen on the video page....

Is there anything else I need to do?

Take a look at the screenshots, maybe you guys had the same problem:


[http://bit.ly/6do6n]("http://bit.ly/6do6n")


:(:(

---

### Post by MelDJ on 2009-10-24
that happens sometimes to me, but i refresh the page and it works.
i know you are bingung/confused with your problem though

---

### Post by bingung99 on 2009-10-24
Thanx for replying...yeah I've tried refreshing couple of times....restarting the computer...searching again through the forum page...sigh.....

Could i have missed something??

:confused::confused:

---

### Post by lovinglinux on 2009-10-24
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by bingung99 on 2009-10-24
> **lovinglinux said:**
> See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

Thanx alot guys...finally managed to solve the problem!!!:)

:guitar::guitar:

---

### Post by RedRat on 2009-10-24
This may or may not help you, but using your file manager, e.g., nautilus or Thunar, turn on hidden files. Look under /home/YourLoginName/.mozilla and see if you have a folder called 'plugins'. See if it contains the file "libflashplayer.so". If it does not, create the folder there and then you will have to download the flashplayer file, e.g., from Adobe. Open the FlashPlayer file "install_flash_player_10_linux.deb" and look for the file "libflashplayer.so" and drag it to the 'plugins' folder you created under /.mozilla. 

This may help. For reasons known only to Ubuntu, when I tried using either synaptic or the deb file from Adobe, it would not create that foler under .mozilla. When I created it and dragged the *.so file in, flash playe worked in firefox. Beats me in wha tis going on heree, but I am running 8.04 and maybe it is just getting tired.

---

### Post by mscitex on 2009-10-25
[SIZE=2][COLOR=#cc0000][COLOR=black]I had the same problem but the guy suggested to read[/COLOR]
[/COLOR][/SIZE][SIZE=2]Troubleshooting section of the[**[COLOR=DarkRed] Firefox optimization and troubleshooting [/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004")[/SIZE][SIZE=2]then go to the section[/SIZE][SIZE=2][COLOR=#cc0000] Removing Conflicting Plugins

[/COLOR][/SIZE] 				 				[SIZE=2][B]it seams to me to that would solve a lots of users problems.
i did it a little deferent
[/B][/SIZE] 			
 			 			 		   		 		 		[SIZE=2]I also had no video or flash and could not see pages with black background
I fixed the problem by removing 2 packages and installing 2

by using "synaptic package manager"

**I removed this package**.
"swfdec-gnome"
Tools to play SWF files (Macromedia Flash) on GNOME
This package contains programs to integrate Flash functionality into the
GNOME desktop. It's main application is swfdec-player, a stand-alone viewer
for Flash files. It also contains swfdec-thumbnailer, a program that
provides screenshots for files to display in the Nautilu

**I removed this package**.
swfdec-Mozilla
Mozilla plugin for SWF files (Macromedia Flash)

A GTK+ and swfdec based Mozilla plugin for SWF files,
commonly known as Macromedia Flash animations

**I installed this package**.
adobe-flashplugin

Adobe Flash Player plugin version 10
This package will download the Flash Player from Adobe. It is a
Netscape/Mozilla type plugin. Any browser based on Netscape or Mozilla can use
the Flash plugin. This package officially supports the following browsers:

**I installed this package**.
flashplug-ininstaller

then i just went to Adobe and downloaded  (Adobe Flash Player)
Adobe Flash Player version 10.0.32.18 Linux

heres the link

[http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP)

then i selected (.deb for ubuntu)

the i restarted Firefox then everything was working as far as i can tell

   -=Mike Scitex=-
[EMAIL="flapipe@yahoo.com"]flapipe@yahoo.com[/EMAIL][/SIZE]

---

### Post by lovinglinux on 2009-10-25
> **mscitex said:**
> 

**I installed this package**.
adobe-flashplugin

**I installed this package**.
flashplug-ininstaller


Please read this:

> **sasha1024 said:**
> The flashplugin-nonfree package is located in the ubuntu repository (ubuntu.com/multiverse), while the adobe-flashplugin is located in the external repository (archive.canonical.com/partner).

The flashplugin-nonfree is somewhat "unusual" package: when you start installing it, it initiates a download from [www.adobe.com;](www.adobe.com;) but no files are contained directly inside the package.
On the other hand, the adobe-flashplugin is a "regular" package of size ~3.7 MB, which actually contains the flash plugin inside.

Thus, "unusual|downloader" flashplugin-nonfree is located in the primary repository, and the "regular" adobe-flashplugin is contained in external repository.
I don't know why they did like that. Just some my stupid assumption:
a) Long-ago they were not sure whether adobe license allows to include the plugin directly into package, so they created "unusual" flashplugin-nonfree.
b) Relatively-recently they created the "regular" adobe-flashplugin; but it's yet experimental and without 64bit support, so the older one is still in repository.

Which one to use -- your choice :). See also [http://ubuntulinuxtipstricks.blogspot.com/2008/12/adobe-flash-avoiding-md5-errors.html](http://ubuntulinuxtipstricks.blogspot.com/2008/12/adobe-flash-avoiding-md5-errors.html)

So, installing both won't help. Besides, adobe-flashplugin is not even present on Karmic anymore. So the recommended package is flashplugin-nonfree.


> **mscitex said:**
> I fixed the problem by removing 2 packages and installing 2

by using "synaptic package manager"

**I removed this package**.
"swfdec-gnome"

**I removed this package**.
swfdec-Mozilla

There is no need to remove swfdec-gnome. It doesn't interfere with Firefox, since it just provides a standalone player and a thumbnailer for Nautilus. The package that needs to be removed is swfdec-mozilla, which is the swfdec plugin for Firefox.

Additionally, lots of users have issues when gnash plugin is installed. So I recommend the procedure described in the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by penguinv on 2009-10-26
In the process of all this I did install gnash.

How can I remove it? If I go to add/remove programs I dont see gnash.

How could I have figured out how to remove it on my own?

And TIA

---

### Post by lovinglinux on 2009-10-26
> **penguinv said:**
> In the process of all this I did install gnash.

How can I remove it? If I go to add/remove programs I dont see gnash.

How could I have figured out how to remove it on my own?

And TIA

Open "Applications >> Accessories >> Terminal" then paste the following command and hit "enter":

```
sudo apt-get remove mozilla-plugin-gnash
```

---

