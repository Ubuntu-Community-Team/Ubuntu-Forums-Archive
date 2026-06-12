---
title: "adobe flash issues"
date: 2010-01-30
forum: General Help
---

### Post by hunterkasy on 2010-01-30
I am running xubuntu 9.10 I have installed the xubuntu restricted I have been able to play flash based games like the one's on facebook, then a couple of weeks ago their was some Firefox and some flash updates, and now I am unable to play any flash games  I have tried removing adobe flash and re-installing through add/remove, didn't work, I have tried removing Firefox through the package remover didn't work, tried removing/re-install both at the same time didn't work.  the only way I was able to get the flash games to some what work was to remove adobe flash from the add/remove and going to adobe's website and downloading the flash from their, after installing it I was able to get the games to load but they were way to choppy to even play,  

This last week I spent at my sister's, they have a laptop that I put Ubuntu 9.10 on and that works with all of the updates installed for flash

---

### Post by lovinglinux on 2010-01-31
[For 32bit](http://lovinglinux.megabyet.net/?page_id=220#Can%27t-play-streaming-flash-videos-2)

[For 64bit](http://ubuntuforums.org/showthread.php?t=1358591)

---

### Post by hunterkasy on 2010-01-31
I tried what the link said to do but I still cannot use any flash pages like facebook games and youtube, they keep saying that I need to update flash

[http://lovinglinux.megabyet.net/?page_id=220#Can%27t-play-streaming-flash-videos-2](http://lovinglinux.megabyet.net/?page_id=220#Can%27t-play-streaming-flash-videos-2)

Some video issues are caused by conflicting plug-ins. It&#8217;s not a good idea to have multiple plug-ins for the same type of content.

To remove conflicting flash plug-ins and install only the one from Adobe open &#8220;Applications >> Accessories >> Terminal&#8221;, then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

Code:

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

Restart Firefox.

---

### Post by tom.swartz07 on 2010-01-31
> **hunterkasy said:**
> I tried what the link said to do but I still cannot use any flash pages like facebook games and youtube, they keep saying that I need to update flash

[http://lovinglinux.megabyet.net/?page_id=220#Can%27t-play-streaming-flash-videos-2](http://lovinglinux.megabyet.net/?page_id=220#Can%27t-play-streaming-flash-videos-2)

Some video issues are caused by conflicting plug-ins. It’s not a good idea to have multiple plug-ins for the same type of content.

To remove conflicting flash plug-ins and install only the one from Adobe open “Applications >> Accessories >> Terminal”, then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

Code:

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

Restart Firefox.

+1
Its important that you remove the old plugins like swfdec and gnash. 

Theres a link in my sig for x64 flash if you use 64 bit Ubuntu, also

---

### Post by lovinglinux on 2010-02-01
> **hunterkasy said:**
> I tried what the link said to do but I still cannot use any flash pages like facebook games and youtube, they keep saying that I need to update flash.

Have you closed Firefox and started it again after running those commands?

Are you using 32bit or 64bit?

Go to the Firefox Add-ons manager and check the version of the installed flash player.

---

### Post by hunterkasy on 2010-02-02
> **tom.swartz07 said:**
> +1
Its important that you remove the old plugins like swfdec and gnash. 

Theres a link in my sig for x64 flash if you use 64 bit Ubuntu, also

I do not have swfdec and gnash installed and I am using 32 bit Xubuntu 9.10 fully updated

---

### Post by hunterkasy on 2010-02-02
> **lovinglinux said:**
> Have you closed Firefox and started it again after running those commands?

Are you using 32bit or 64bit?

Go to the Firefox Add-ons manager and check the version of the installed flash player.



I have restarted firefox after running those commands I also rebooted th machine just for the hell of it, still didn't work, I am using 32 bit Xubuntu 9.10  I went to the add-on manager in firefox and I did not see any flash player installed, but I do have adobe player installed under the add/remove

---

### Post by lovinglinux on 2010-02-02
> **hunterkasy said:**
> I have restarted firefox after running those commands I also rebooted th machine just for the hell of it, still didn't work, I am using 32 bit Xubuntu 9.10  I went to the add-on manager in firefox and I did not see any flash player installed, but I do have adobe player installed under the add/remove

Close Firefox, open your home folder with the file manager, then hit CTRL+H to see the hidden files, then open the folder .mozilla/firefox and look for your profile folder there. Inside your profile folder, delete the file *pluginreg.dat*. Start Firefox and see if it recognizes the flash player.

---

### Post by Leppie on 2010-02-02
what is the output of the following command:
```
locate locate libflashplayer.so
```

it sometimes gets copied to other folders as well (like the general mozilla plugins folder).

---

### Post by hunterkasy on 2010-02-03
> **Leppie said:**
> what is the output of the following command:
```
locate locate libflashplayer.so
```

it sometimes gets copied to other folders as well (like the general mozilla plugins folder).

lisa@lisa-desktop:~$ locate locate libflashplayer.so
/etc/alternatives/locate
/etc/alternatives/locate.1.gz
/etc/cron.daily/mlocate
/usr/bin/locate
/usr/bin/mlocate
/usr/bin/updatedb.mlocate
/usr/lib/gnome-settings-daemon/gsd-locate-pointer
/usr/share/doc/mlocate
/usr/share/doc/mlocate/AUTHORS
/usr/share/doc/mlocate/NEWS.gz
/usr/share/doc/mlocate/README
/usr/share/doc/mlocate/TODO.Debian
/usr/share/doc/mlocate/changelog.Debian.gz
/usr/share/doc/mlocate/changelog.gz
/usr/share/doc/mlocate/copyright
/usr/share/locale-langpack/en_GB/LC_MESSAGES/mlocate.mo
/usr/share/man/man1/locate.1.gz
/usr/share/man/man1/mlocate.1.gz
/usr/share/man/man5/mlocate.db.5.gz
/usr/share/snmp/mib2c-data/generic-data-allocate.m2i
/var/lib/mlocate
/var/lib/dpkg/alternatives/locate
/var/lib/dpkg/info/mlocate.conffiles
/var/lib/dpkg/info/mlocate.list
/var/lib/dpkg/info/mlocate.md5sums
/var/lib/dpkg/info/mlocate.postinst
/var/lib/dpkg/info/mlocate.postrm
/var/lib/dpkg/info/mlocate.prerm
/var/lib/mlocate/daily.lock
/var/lib/mlocate/mlocate.db
/var/lib/mlocate/mlocate.db.Z12W8Z
lisa@lisa-desktop:~$

---

### Post by hunterkasy on 2010-02-03
> **lovinglinux said:**
> Close Firefox, open your home folder with the file manager, then hit CTRL+H to see the hidden files, then open the folder .mozilla/firefox and look for your profile folder there. Inside your profile folder, delete the file *pluginreg.dat*. Start Firefox and see if it recognizes the flash player.

I did what you said, delete pluginreg.dat  still the same unable to play any flash games youtube, and I did not see flash in addon's

---

### Post by lovinglinux on 2010-02-03
> **hunterkasy said:**
> lisa@lisa-desktop:~$ locate locate libflashplayer.so
/etc/alternatives/locate
/etc/alternatives/locate.1.gz
/etc/cron.daily/mlocate
/usr/bin/locate
/usr/bin/mlocate
/usr/bin/updatedb.mlocate
/usr/lib/gnome-settings-daemon/gsd-locate-pointer
/usr/share/doc/mlocate
/usr/share/doc/mlocate/AUTHORS
/usr/share/doc/mlocate/NEWS.gz
/usr/share/doc/mlocate/README
/usr/share/doc/mlocate/TODO.Debian
/usr/share/doc/mlocate/changelog.Debian.gz
/usr/share/doc/mlocate/changelog.gz
/usr/share/doc/mlocate/copyright
/usr/share/locale-langpack/en_GB/LC_MESSAGES/mlocate.mo
/usr/share/man/man1/locate.1.gz
/usr/share/man/man1/mlocate.1.gz
/usr/share/man/man5/mlocate.db.5.gz
/usr/share/snmp/mib2c-data/generic-data-allocate.m2i
/var/lib/mlocate
/var/lib/dpkg/alternatives/locate
/var/lib/dpkg/info/mlocate.conffiles
/var/lib/dpkg/info/mlocate.list
/var/lib/dpkg/info/mlocate.md5sums
/var/lib/dpkg/info/mlocate.postinst
/var/lib/dpkg/info/mlocate.postrm
/var/lib/dpkg/info/mlocate.prerm
/var/lib/mlocate/daily.lock
/var/lib/mlocate/mlocate.db
/var/lib/mlocate/mlocate.db.Z12W8Z
lisa@lisa-desktop:~$

You typed locate twice, so it located the locate program, not the  libflashplayer.so

Do it again and post the result.

---

### Post by hunterkasy on 2010-02-04
> **lovinglinux said:**
> You typed locate twice, so it located the locate program, not the  libflashplayer.so

Do it again and post the result.

I did what you said, it does not locate it

lisa@lisa-desktop:~$ locate libflashplayer.so
lisa@lisa-desktop:~$

---

### Post by lovinglinux on 2010-02-04
> **hunterkasy said:**
> I did what you said, it does not locate it

lisa@lisa-desktop:~$ locate libflashplayer.so
lisa@lisa-desktop:~$

So, close Firefox and run these:

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

After that, run the locate command again:

```
locate libflashplayer.so
```

Post the result:

Then open Firefox and check if Flash is recognized and working.

---

### Post by selectstar on 2010-02-04
ok
I am having the exact same problem
Ubuntu 9.10 amd64. Firefox updated to 3.6 and flash stopped to work
Tryed many procedures suggested in this forum but none of them worked.


my result for locate libflashplayer.so is
[PHP]
/home/martin/libflashplayer.so
/home/martin/.local/share/Trash/info/npwrapper.libflashplayer.so.trashinfo
/root/.local/share/Trash/files/npwrapper.libflashplayer.so
/root/.local/share/Trash/info/npwrapper.libflashplayer.so.trashinfo
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
[/PHP]

---

### Post by Leppie on 2010-02-04
> **selectstar said:**
> ok
I am having the exact same problem
Ubuntu 9.10 amd64. Firefox updated to 3.6 and flash stopped to work
Tryed many procedures suggested in this forum but none of them worked.
did you use the script in this thread? [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)
i'm on x64 and flash working fine for ff 3.6

---

### Post by selectstar on 2010-02-04
> **Leppie said:**
> did you use the script in this thread? [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

Yes that's exactly the one.
But I also tried the suggested pluging by firefox.
I also tried installing flash-nonfree directly from teminal

---

### Post by Leppie on 2010-02-04
> **selectstar said:**
> Yes that's exactly the one.
But I also tried the suggested pluging by firefox.
I also tried installing flash-nonfree directly from teminal
is flash enabled in ff?
go to Tools>Add-ons>Plugins>Shockwave Flash. if the button says enable, then click it (as it is disabled like this).

---

### Post by selectstar on 2010-02-04
> **Leppie said:**
> is flash enabled in ff?
go to Tools>Add-ons>Plugins>Shockwave Flash. if the button says enable, then click it (as it is disabled like this).

if I go to Tools>Add-ons>Plugins> there isn't any Shockwave Flash plugin

---

### Post by Leppie on 2010-02-04
> **selectstar said:**
> if I go to Tools>Add-ons>Plugins> there isn't any Shockwave Flash plugin
then i would suggest to close ff completely and rerun the script.

---

### Post by selectstar on 2010-02-04
> **Leppie said:**
> then i would suggest to close ff completely and rerun the script.

Already tried ](*,)

---

### Post by hunterkasy on 2010-02-06
> **lovinglinux said:**
> So, close Firefox and run these:

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

After that, run the locate command again:

```
locate libflashplayer.so
```

Post the result:

Then open Firefox and check if Flash is recognized and working.


I did what you said, flash still does not work


lisa@lisa-desktop:~$ sudo apt-get remove swfdec-mozilla
[sudo] password for lisa: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-17 libevent-1.4-2 xulrunner-1.9.1-gnome-support
  linux-headers-2.6.28-11 language-support-translations-en
  thunderbird-locale-en-gb openoffice.org-l10n-common libsmbios2
  libdirectfb-1.0-0 acl evolution-documentation-en
  linux-headers-2.6.28-11-generic tcl openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za openoffice.org-help-en-gb gnome-mount
  openoffice.org-help-en-us linux-headers-2.6.31-17-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lisa@lisa-desktop:~$ sudo apt-get remove mozilla-plugin-gnash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-plugin-gnash is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-17 libevent-1.4-2 xulrunner-1.9.1-gnome-support
  linux-headers-2.6.28-11 language-support-translations-en
  thunderbird-locale-en-gb openoffice.org-l10n-common libsmbios2
  libdirectfb-1.0-0 acl evolution-documentation-en
  linux-headers-2.6.28-11-generic tcl openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za openoffice.org-help-en-gb gnome-mount
  openoffice.org-help-en-us linux-headers-2.6.31-17-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lisa@lisa-desktop:~$ sudo apt-get remove adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-17 libevent-1.4-2 xulrunner-1.9.1-gnome-support
  linux-headers-2.6.28-11 language-support-translations-en
  thunderbird-locale-en-gb openoffice.org-l10n-common libsmbios2
  libdirectfb-1.0-0 acl evolution-documentation-en
  linux-headers-2.6.28-11-generic tcl openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za openoffice.org-help-en-gb gnome-mount
  openoffice.org-help-en-us linux-headers-2.6.31-17-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lisa@lisa-desktop:~$ sudo apt-get remove flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-17 libevent-1.4-2 xulrunner-1.9.1-gnome-support
  linux-headers-2.6.28-11 language-support-translations-en
  thunderbird-locale-en-gb openoffice.org-l10n-common libsmbios2
  libdirectfb-1.0-0 acl evolution-documentation-en
  linux-headers-2.6.28-11-generic tcl openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za openoffice.org-help-en-gb gnome-mount
  openoffice.org-help-en-us linux-headers-2.6.31-17-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-nonfree
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 41.0kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 164271 files and directories currently installed.)
Removing flashplugin-nonfree ...
lisa@lisa-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-17 libevent-1.4-2 xulrunner-1.9.1-gnome-support
  linux-headers-2.6.28-11 language-support-translations-en
  thunderbird-locale-en-gb openoffice.org-l10n-common libsmbios2
  libdirectfb-1.0-0 acl evolution-documentation-en
  linux-headers-2.6.28-11-generic tcl openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za openoffice.org-help-en-gb gnome-mount
  openoffice.org-help-en-us linux-headers-2.6.31-17-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1,772B of archives.
After this operation, 41.0kB of additional disk space will be used.
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 164269 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.42.34ubuntu0.9.10.1_i386.deb) ...
Setting up flashplugin-nonfree (10.0.42.34ubuntu0.9.10.1) ...
lisa@lisa-desktop:~$ locate libflashplayer.so
lisa@lisa-desktop:~$

---

### Post by Leppie on 2010-02-06
@lisa
could you post the output of the following command:
```
sudo find / -iname libflashplayer.so
```

---

### Post by hunterkasy on 2010-02-06
> **Leppie said:**
> @lisa
could you post the output of the following command:
```
sudo find / -iname libflashplayer.so
```

lisa@lisa-desktop:~$ sudo find / -iname libflashplayer.so
[sudo] password for lisa: 
lisa@lisa-desktop:~$

---

### Post by Leppie on 2010-02-06
try the following:
```
cp /var/cache/apt/archives/flashplugin-nonfree_10.0.42.34ubuntu0.9.10.1_i386.deb ~/Desktop/
```this will copy the package to your desktop, then just double click that package and have gdebi install it.
if gdebi doesn't come up with errors, try the locate command again.

alternatively, download the player from the Adobe website and install with gdebi: [http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb](http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb))

---

### Post by hunterkasy on 2010-02-07
> **Leppie said:**
> try the following:
```
cp /var/cache/apt/archives/flashplugin-nonfree_10.0.42.34ubuntu0.9.10.1_i386.deb ~/Desktop/
```this will copy the package to your desktop, then just double click that package and have gdebi install it.
if gdebi doesn't come up with errors, try the locate command again.

alternatively, download the player from the Adobe website and install with gdebi: [http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb](http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb))

I did what you said, after it was copied to the desktop and doubled clicked on it, I clicked on re-install, everything went without isues

I tried the locate commands again, and they found nothing, next I am going to follow the link to download from adobes site and see what happens

lisa@lisa-desktop:~$ locate libflashplayer.so
lisa@lisa-desktop:~$ sudo find / -iname libflashplayer.so
[sudo] password for lisa: 
lisa@lisa-desktop:~$

---

### Post by hunterkasy on 2010-02-07
> **hunterkasy said:**
> I did what you said, after it was copied to the desktop and doubled clicked on it, I clicked on re-install, everything went without isues

I tried the locate commands again, and they found nothing, next I am going to follow the link to download from adobes site and see what happens

lisa@lisa-desktop:~$ locate libflashplayer.so
lisa@lisa-desktop:~$ sudo find / -iname libflashplayer.so
[sudo] password for lisa: 
lisa@lisa-desktop:~$


I had to remove adobe flash from add/remove, then I was able to install the new adobe flash from adobe's web site, I am able to play flash games, and I am able to use youtube

lisa@lisa-desktop:~$ locate libflashplayer.so
lisa@lisa-desktop:~$ 
lisa@lisa-desktop:~$ sudo find / -iname libflashplayer.so
[sudo] password for lisa: 
/usr/lib/adobe-flashplugin/libflashplayer.so
lisa@lisa-desktop:~$

---

### Post by Leppie on 2010-02-07
glad you've got it going now. flash can be a bit of a pain to install properly.
good thing you didn't give in so easily ;)

---

### Post by cmcginty on 2010-02-19
Just had this same issue. All the above tricks did not work ... the one that did it was:


[B]Before exiting FireFox ... make sure to clear the complete browser history/cookies/settings.

<Ctrl-Shif-Del>, Time range = "Everything", "Clear Now"[/B]

---

### Post by selectstar on 2010-02-23
@cmcginty I am glad to hear you managed to fix your issue just by emptying your cache. This is not the kind of problem I have. My issue seems to be much more serious and it's not a matter of any configuration I can change. 
Firefox is refusing to use the installed flash player which is correctly working with Chrome and Opera.
It is only a matter of either Mozilla or Adobe to fix the bug.
I am not sure who's fault is it so I am unable to log a bug report

---

