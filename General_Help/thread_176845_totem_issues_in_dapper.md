---
title: "totem issues in dapper"
date: 2006-05-15
forum: General Help
---

### Post by jsmidt on 2006-05-15
I installed Dapper.  I put in a DVD and totem gives me these error messages:  Totem could not play 'dvd:///media/cdrom0'. No URI handler implemented for "dvd".

If I then close totem and reopen it and say "Play Disc" It says: Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it. Please install the necessary plugins and restart Totem to be able to play this media.

Does anybody know what I can do about this.  If I need to install more plugins which ones?  Synaptic does not suggest or recommend any.  Also, if the correct plugins are not installed automatically should I file a bug report?

---

### Post by linuxcity on 2006-05-15
You can follow the instruction on this page to install the plug-ins:

[http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper)

---

### Post by jsmidt on 2006-05-15
I appriciate the help.  The only problem is the link says:

 How to install DVD playback capability

Stubby: gstreamer dvd plugin not ported to dapper yet. following instructions will not work properly

    * Read #General Notes
    * Read #How to add extra repositories 

sudo apt-get install libdvdcss2

So the instuctions don't work yet.  However it looks like I just need to get my hands on libdvdcss2.  Does anybody know where I can find this.  It isn't in universe or multiverse.

---

### Post by linuxcity on 2006-05-15
You need to add the "Extra repositories"
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories)
after you added the extra repositories
sudo apt-get update
sudo apt-get upgrade
then install the packages you need for multimedia player.

Or you can use Easy Ubuntu, which designed for Breezy, but it works okay for Dapper

[http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html)
-------------------------------------------------------------
This release support Ubuntu/Kubuntu/Xubuntu, Breezy/Dapper, x86/powerpc/amd64!

wget [http://robotgeek.org/eu/easyubuntu-3.0-beta.tar.gz](http://robotgeek.org/eu/easyubuntu-3.0-beta.tar.gz)
tar -zxf easyubuntu-3.0-beta.tar.gz
cd easyubuntu
sudo python easyubuntu.py
-----------------------------------------------------------------

---

### Post by jivebiscuit on 2006-10-13
Try this link: [http://www.ehomeupgrade.com/entry/2663/how-to_get_full](http://www.ehomeupgrade.com/entry/2663/how-to_get_full)

Everything works when you follow this links instructions to the tee...

---

