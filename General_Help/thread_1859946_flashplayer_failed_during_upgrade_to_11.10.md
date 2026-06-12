---
title: "flashplayer failed during upgrade to 11.10"
date: 2011-10-14
forum: General Help
---

### Post by gamblor01 on 2011-10-14
Last night I upgraded from 11.04 to 11.10.  I'm having a few issues with it but most of them I think I can fix by just tweaking the .desktop files and dragging them back into the launch bar.

However, the biggest issue I ran into is a failure to properly install flash.  The upgrade process ran for a few hours (servers must have been slow due to a large amount of traffic) and then eventually right before it told me to reboot it gave me an error saying that the upgrade failed.  I should have copied and pasted the message but I didn't.  :(  It was something about how flashplugin-downloader:i386 failed to install because of flashplugin-installer.  Then I believe it said it would run dpkg --configure -a?

I rebooted and flash doesn't work.  I ran apt-get remove flashplugin-installer and uninstalled.  It said there were some other unused packages so I then ran apt-get autoremove and removed all of those as well.  But flash still doesn't work.  I did an apt-get install flashplayer-installer and it's still not working.

Any idea how to fix this?  If it helps at all, I know that prior to the upgrade (when running 11.04) I had installed both the restricted-extras package as well as ia32-libs.  I don't know if that is causing any conflicts or not.

---

### Post by TheCat on 2011-10-14
I had the same problem.  The error is:

> Could not install 'flashplugin-downloader'

The upgrade will continue but the 'flashplugin-downloader' package may not be in a working state. Please consider submitting a bug report about it.

subprocess installed post-installation script returned error exit status 1

---

### Post by kungfoofool on 2011-10-14
I was upgrading from the alternative CD-ROM and got the same error.

Appears to be running 11.10 now but I'm not sure if the upgrade was done or not. :/

---

### Post by Frogs Hair on 2011-10-14
If you are using Firefox install Flash Aid and try to install with that .

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by hunterm4573r on 2011-10-14
I had this same problem.  Somewhere in the upgrade process Network-Manager disconnected the network and I suppose there is a bug in the Flash installer that bails if the additional flash-download can't connect to the the Internet.  

I wonder if manually re-connecting would prevent this error.  In any case, after I read with much trepidation the message 'your system may be left in an unusable state', I rebooted and everything seems fine, the strange video lag on almost every window/icon interaction not withstanding.

---

### Post by gamblor01 on 2011-10-14
> **hunterm4573r said:**
> I had this same problem.  Somewhere in the upgrade process Network-Manager disconnected the network and I suppose there is a bug in the Flash installer that bails if the additional flash-download can't connect to the the Internet.  

I wonder if manually re-connecting would prevent this error.  In any case, after I read with much trepidation the message 'your system may be left in an unusable state', I rebooted and everything seems fine, the strange video lag on almost every window/icon interaction not withstanding.

Hey you're absolutely correct!  I went to [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) and it finally displays my flash version.  I don't know when this happened -- I suppose at some point while I was at work today?  When I tested this page early this morning (shortly after reboot) it said that I was missing the plugin.  The about:plugins page in both Firefox and Chrome failed to list the plugin as well.  For some reason it shows up now.

Not sure how it got fixed but I'll take it!  Now to fix a few other little issues...

---

### Post by tonus on 2011-10-15
This is this bug: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/859373](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/859373)

---

