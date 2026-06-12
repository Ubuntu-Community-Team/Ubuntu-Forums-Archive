---
title: "Getting your Ubuntu 6.06 installation ready for you - Multimedia guide"
date: 2006-06-01
forum: General Help
---

### Post by Kevin on 2006-06-01
I thought I'd start a thread, that would clear up some of the things about Automatix, BUMPS, and EasyUbuntu.  If anyone has any suggestions or corrections just tell me and I'll try and keep it updated.
___________

So you've finally got your new Ubuntu 6.06 installation working, and now you need to get it ready for daily use.  Depending on how you use your computer, there might still be some things for you to do.

One of the most often asked questions, is how to get Ubuntu multimedia ready.  This includes things like audio and video codecs, DVD playback, as well as internet content such as Flash.  There are a couple ways to accomplish this.  There are several programs and scripts that will get everything set up for you, and of course you can do it all yourself with the right information.

[SIZE="4"]**Method #1 - BUMPS - Basic Ubuntu Multimedia Preparation Script**[/SIZE]

BUMPS is what it's name implies: basic.  It is, however, basic by design.  BUMPS is designed to get your Ubuntu installation multimedia ready, whilst changing your installation as little as possible.  It installs few programs, and is mostly unnoticeable once installed, with the obvious exception being that your multimedia works!  BUMPS was written from the ground up for Ubuntu 6.06, and has been extensively tested by its users.  Since it modifies the least things, it is arguably the safest of the three programs, and least likely to mess up your installation.  This is recommended for most users.

Step 1:  More information about BUMPS including the packages it installs is available [here.]("http://www.ubuntuforums.org/showthread.php?t=181248")

Step 2:  BUMPS can be downloaded from [this thread.]("http://www.ubuntuforums.org/showthread.php?t=181251")

Step 3:  Simply double click the script and select run, or run it from the command line, and follow the instructions!

[SIZE="4"]**Method #2 - EasyUbuntu**[/SIZE]

EasyUbuntu installs a few more things than BUMPS, including 3d Acceleration for nVidia and ATI users, and will also get your multimedia set up.  It also includes tweaks such as restoring your Firefox icons, and installing Skype.  EasyUbuntu supports 6.06 and 5.10, but has not been as extensively tested for 6.06 as BUMPS.

Step 1:  More information about EasyUbuntu can be found [here.]("http://easyubuntu.freecontrib.org/")

Step 2:  EasyUbuntu can now be downloaded from [this page.]("http://easyubuntu.freecontrib.org/get.html")  Instructions on how to download and run it are all there.

[SIZE="4"]**Method #3 - Automatix**[/SIZE]

Some users may want to install lots of additional software, and have many additional things set up for them.  For this there is Automatix, which does everything that the previous two methods do, as well as much more.  Automatix is still in the process of being ported to 6.06, and as a result may still not work as advertised.  Of the three methods, it modifies your installation the most, and can be the most dangerous.  Have a look at the packages in installs, available in the more information link below, and see if it is right for you.  Automatix has a lot of support behind it, and is a constantly moving project, so feel free to follow its development and try it out!

Step 1:  More information on Automatix, as well as a download link, can be found in [this thread.]("http://www.ubuntuforums.org/showthread.php?t=177646")

Step 2:  Double click the file downloaded, and install the package.

Step 3:  There should now be a menu link for Automatix under Applications -> System Tools, and you can use it to install the additional software.

**General Note!**

If you'd like to learn about what these programs are doing, or how to do it yourself, a great page to start is the wiki entry on RestrictedFormats.  This page also includes a legal disclaimer as well as information on why proprietary codecs require such intervention.  It is a highly suggested read!

This page can be found [here.]("https://wiki.ubuntu.com/RestrictedFormats")

That's all for now, I'll try and keep this thread updated as things change.

---

### Post by abhaysahai on 2006-06-01
Thanks for the info buddy. 
Of these Automatix is by far the best and the easiet to install commonly used software.

---

### Post by atezun on 2006-06-01
Automatix is alright, but I use EasyUbuntu, because I don't like all the bloat comes with Automatix. (ie: I don't use much outside the codes, nvidia driver and microsoft fonts.)

On a related nore: Is anyone else having problems getting the Nvidia driver through EasyUbuntu right now?

---

### Post by turbojugend_gr on 2006-06-01
yeah, me.I done it through synaptic fine. Though it doesn't let me to install nvidia settings GUI also. Weird.

---

### Post by nix4me on 2006-06-01
Those scripts are mostly pointless now with the added functionality of the add/remove programs applet.  Most unsupported and commercial apps are in the list now.

nix4me

---

### Post by Rackerz on 2006-06-01
[QUOTE=nix4me]Those scripts are mostly pointless now with the added functionality of the add/remove programs applet.  Most unsupported and commercial apps are in the list now.

nix4me[/QUOTE]

True that.

---

### Post by russianbandit on 2006-06-01
Does anyone know whats the difference between gstreamer-0.8 stuff and gstreamer-0.10 stuff. Because BUMPS gets the 0.10 and Automatix gets 0.80.

---

### Post by Kevin on 2006-06-01
All the programs in Dapper use gstreamer0.10, so the gstreamer0.8 plugins aren't of much use anymore, except for legacy apps that still use 0.8.

---

### Post by Rackerz on 2006-06-01
[QUOTE=Kevin]All the programs in Dapper use gstreamer0.10, so the gstreamer0.8 plugins aren't of much use anymore, except for legacy apps that still use 0.8.[/QUOTE]

Correct. Also in the above it needs to mentioned that Automatix edits important system settings and can cause problems for some users.

---

### Post by ericesque on 2006-06-01
Additionally Automatix has not worked out all the bugs for 6.06.   I used BUMPS and it worked wonderfully.  Then again, BUMPS was designed for Dapper.  Automatix was designed for breezy and is being adapted/updated for dapper.

---

### Post by aysiu on 2006-06-01
Kevin, can you give a slightly more detailed overview of each--what are the differences between them? A link to "read more about..." is nice, but it'd also be nice for a new user to just know straightaway which one suits her needs best.

---

### Post by ronlybonly on 2006-06-01
Good info. ... GREAT sig. quote!

---

### Post by Kevin on 2006-06-01
[QUOTE=aysiu]Kevin, can you give a slightly more detailed overview of each--what are the differences between them? A link to "read more about..." is nice, but it'd also be nice for a new user to just know straightaway which one suits her needs best.[/QUOTE]
Sure thing, I'll do a little more research first so I don't mess anything up, but I'll try and add more detail.

Edit: Ok I tried to elaborate on a few things.  If anyone has anything specific for me to add just let me know!

---

### Post by aysiu on 2006-06-02
[QUOTE=Kevin]Sure thing, I'll do a little more research first so I don't mess anything up, but I'll try and add more detail.

Edit: Ok I tried to elaborate on a few things.  If anyone has anything specific for me to add just let me know![/QUOTE] It looks awesome now. Thanks for the revision.

---

### Post by mk1970 on 2006-06-08
May I proposed Method #4:

[http://ubuntuforums.org/showthread.php?t=186533](http://ubuntuforums.org/showthread.php?t=186533)

---

### Post by Iandefor on 2006-07-01
Might I suggest updating this? It's a good comparison, but is outdated.

---

