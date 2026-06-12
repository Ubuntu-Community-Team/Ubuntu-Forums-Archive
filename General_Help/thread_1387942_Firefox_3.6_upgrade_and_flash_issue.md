---
title: "Firefox 3.6 upgrade and flash issue"
date: 2010-01-22
forum: General Help
---

### Post by kbarron on 2010-01-22
I upgraded to 3.6 and now I can't get flash to work. I am running on 64 bit. I have tried multiple attempts to install the plugin however it is still not being detected. Can someone please help me completely remove firefox and all adobe related files via terminal etc so that I can try a clean install. As is the case Flash was never working that well even with the 64 bit alpha but it was better than nothing. I was hoping that the upgrade might improve performance. I just want to start from scratch and think that I have attempted so many different installs for flash that I prob screwed something up. Any help would be great

---

### Post by lovinglinux on 2010-01-22
For 64bit, you need to update Firefox using the *ubuntu-mozilla-daily* ppa, otherwise the plugin will not be detected or will be disabled by the new plugin checking feature.

If you have done that, than remove any flashplugin installed and follow [this tutorial](http://ubuntuforums.org/showthread.php?t=1358591).

---

### Post by lovinglinux on 2010-01-22
I forgot to explain how to completely remove flash.

First run this:

```

sudo apt-get purge flashplugin-nonfree
sudo apt-get purge flashplugin-installer
```

Then go to your **~/.mozilla**, find any plugins folder there (including under firefox folder if there is any) and delete *libflashplayer.so.*

Then go to **/usr/lib/mozilla/plugins**, **/usr/lib/firefox-addons/plugins** and **/usr/lib/xulrunner-addons/plugins** and delete *libflashplayer.so*, **BUT ONLY IF THEY ARE NOT** symlinks. The real file, not a symlink, should be the one in the **/usr/lib/mozilla/plugins**, but who knows what you have done already.

---

### Post by kbarron on 2010-01-22
Thanks lovinglinux, i purged what I could and root deleted the other stuff, still can't get it to work with the 64 bit flash alpha

I am thinking I need to wipe mozilla completely and do a fresh install from the ppa again perhaps. Not sure what else to do. As I said I think I might have conflicting files with having the 3.5 pre and then 3.6 beta at one point as there are multiple firefox folders in my /usr/lib directories 

any ides on how to completely purge all mozilla related files to ensure a clean slate

---

### Post by lovinglinux on 2010-01-22
> **kbarron said:**
> Thanks lovinglinux, i purged what I could and root deleted the other stuff, still can't get it to work with the 64 bit flash alpha

I am thinking I need to wipe mozilla completely and do a fresh install from the ppa again perhaps. Not sure what else to do. As I said I think I might have conflicting files with having the 3.5 pre and then 3.6 beta at one point as there are multiple firefox folders in my /usr/lib directories 

any ides on how to completely purge all mozilla related files to ensure a clean slate

Just uninstall any Firefox and xulrunner from Synaptic, then install again.

---

### Post by bodhi.zazen on 2010-01-26
> **lovinglinux said:**
> For 64bit, you need to update Firefox using the *ubuntu-mozilla-daily* ppa, otherwise the plugin will not be detected or will be disabled by the new plugin checking feature.

If you have done that, than remove any flashplugin installed and follow [this tutorial]("http://ubuntuforums.org/showthread.php?t=1358591").

As this thread comes up on a google search, I installed firefox directly form mozilla, into /usr/local/firefox

To use flash is not *that* hard, and you do not need a complex tutorial.

Download flash from adobe

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Select the linux version, get the .tar.gz

Extract the tar, you can do this with file roller or from the command line

install_flash_player_10_linux.tar.gz

The archive contains a single file, libflashplayer.so

```
sudo mv libflashplayer.so /usr/local/firefox/plugins
```

Restart firefox.

---

### Post by sylaan on 2010-01-29
That problem is that from Mozilla and Adobe you can only download the 32bit versions. We are talking here about the 64bit versions.

I have the same problem, I have upgraded to 3.6 from the mozilla-stable ppa and now Flash is not working. I don't want to use the unstable builds, I would like to have flash working on the stable 64bit version. 

Any ideas ?

---

### Post by sylaan on 2010-01-29
This post provides a solution: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1388978](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1388978)

I simply removed my ~/.mozilla/plugins folder and then I did a: 

```
~/.mozilla$ ln -s /usr/lib/mozilla/plugins/ ./
```

That fixed it for me.

---

### Post by MrSkrimps on 2010-03-01
Hey guys, 

I'm having a heck of a time.  Here's the low down.

Ubuntu 9.10 amd64
Firefox 3.6.2pre  (little confused on that one..)

attempting to use the Flash64 bit.  and no matter where I put it:
/home/user/.mozilla/plugins/
/usr/lib/firefox/plugins/
/usr/lib/mozilla/plugins/

various other methods involving symlinks to the newly created firefox 3.6 directory under 
/usr/lib/~

here is what i have done prior:
i have completely removed and purged all references to libflashplayer.so, flash-plugin installer, and everything else I ahve found to do in the forums...still the only way I can get flash to work in Firefox 3.6 is to use the npwrapper...not utilizing 64 bit...I do have a ubuntu 9.10 64 bit installed, am using amd64 bit architecture...

I'm just completely confused and frustrated at this point.  any suggestion???

after 5 hours of wrestling with this, this is what I got in about:plugins:

File:  npwrapper.libflashplayer.soVersion:   Shockwave Flash 10.0 r45
any help would be awesome...

---

### Post by lovinglinux on 2010-03-01
> **MrSkrimps said:**
> Hey guys, 

I'm having a heck of a time.  Here's the low down.

Ubuntu 9.10 amd64
Firefox 3.6.2pre  (little confused on that one..)

attempting to use the Flash64 bit.  and no matter where I put it:
/home/user/.mozilla/plugins/
/usr/lib/firefox/plugins/
/usr/lib/mozilla/plugins/

various other methods involving symlinks to the newly created firefox 3.6 directory under 
/usr/lib/~

here is what i have done prior:
i have completely removed and purged all references to libflashplayer.so, flash-plugin installer, and everything else I ahve found to do in the forums...still the only way I can get flash to work in Firefox 3.6 is to use the npwrapper...not utilizing 64 bit...I do have a ubuntu 9.10 64 bit installed, am using amd64 bit architecture...

I'm just completely confused and frustrated at this point.  any suggestion???

after 5 hours of wrestling with this, this is what I got in about:plugins:

File:  npwrapper.libflashplayer.soVersion:   Shockwave Flash 10.0 r45
any help would be awesome...

Try the [automated installer created by carlee](http://ubuntuforums.org/showthread.php?t=1414595).

---

