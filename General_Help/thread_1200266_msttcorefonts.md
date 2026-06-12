---
title: "msttcorefonts"
date: 2009-06-29
forum: General Help
---

### Post by chopwet on 2009-06-29
I am reaching at point of frustration now, thanks to having to install wine, just so that I can use Safari (still haven't got it to work yet) or even god-forbid, IE, thanks to needing to do work related tasks on a site that only accepts those two browsers.

I cannot get Safari to open and I keep getting the seemingly dreaded  E: msttcorefonts: subprocess post-installation script returned error exit status 1 error message.

Someone please help! I have searched and tired many of the different solution but none have worked thus far, I'm running 8.04 Hardy Heron

---

### Post by [adult swim] on 2009-06-30
what happens when you run the following command from a terminal?
```
sudo apt-get install msttcorefonts
```

alternatively there is a plugin for firefox called user agent switcher.  when a website queries your browser to see what type it is, instead of firefox, it will return safari, ie or almost any other browser you want it to appear as.  this would probably get around the problem you seem to be having.  you can get it here [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

---

### Post by chopwet on 2009-07-03
Sorry about the very delayed response!, Trying:  sudo apt-get install msttcorefonts

Gives me:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
msttcorefonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

I cannot solve this, I've tried searching the web, and various solutions do not work for me! Also every time I install something new or use the update manager I get errors!

Help!

---

### Post by Soul-Sing on 2009-07-03
> Invalid host name.

system: synaptic packagemanager: preferences: network
Are you behind a proxy? Otherwise try it without using a proxy.

---

### Post by moster on 2009-07-03
That sudo apt-get install... puts fonts in ubuntu here 
```
/usr/share/fonts/truetype/msttcorefonts
```
and that safari is looking for it here, because I understand that you run it in wine.
```
/home/moster/.wine/dosdevices/c:/windows/Fonts
```

That other path you just need to change accordingly to your username. My username, as visible in path is moster. I would just copy that fonts to that other directory.

You also have to go to view > show hidden files in nautilus so you can view .directories.

wish luck to that is only problem :)

---

### Post by chopwet on 2009-07-03
> **leoquant said:**
> system: synaptic packagemanager: preferences: network
 Are you behind a proxy? Otherwise try it without using a proxy.
 

 Despite studying computer science for a while, I'm not great with technical terms, I am connected to the net via a wireless network and I cannot connect directly, since the the connection is in another part of the house.

---

### Post by chopwet on 2009-07-03
> **moster said:**
> That sudo apt-get install... puts fonts in ubuntu here 
```
/usr/share/fonts/truetype/msttcorefonts
```and that safari is looking for it here, because I understand that you run it in wine.
```
/home/moster/.wine/dosdevices/c:/windows/Fonts
```That other path you just need to change accordingly to your username. My username, as visible in path is moster. I would just copy that fonts to that other directory.

You also have to go to view > show hidden files in nautilus so you can view .directories.

wish luck to that is only problem :)

oooh my wine fonts folder was empty, I've copied everything across, hopefully this works now!

---

### Post by chopwet on 2009-07-04
Now I seem to get this problem when trying to run the update manager:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy Release: The following signatures were invalid: NODATA 1 NODATA 2

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: Failed to fetch [http://th.archive.ubuntu.com/ubuntu/dists/hardy/Release](http://th.archive.ubuntu.com/ubuntu/dists/hardy/Release)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.


I'm really starting to regret ever having put **wine** on my machine, and I still can't get either Safari nor IE to work

---

### Post by chopwet on 2009-07-06
Anyone have any other suggestions?

When I run the update manager the latest message I get is this:

[B]E: msttcorefonts: subprocess post-installation script returned error exit status 1


[/B]

---

### Post by Ra-Hoor-Khuit on 2009-07-06
Try using ```
sudo apt-get install ubuntu-restricted-extras
```That metapackage contains the msttcorefonts package you need.

If you still get errors try using a different server via the Software Sources "Download From" button.

---

### Post by DeMus on 2009-07-06
> **chopwet said:**
> I am reaching at point of frustration now, thanks to having to install wine, just so that I can use Safari (still haven't got it to work yet) or even god-forbid, IE, thanks to needing to do work related tasks on a site that only accepts those two browsers.

I cannot get Safari to open and I keep getting the seemingly dreaded  E: msttcorefonts: subprocess post-installation script returned error exit status 1 error message.

Someone please help! I have searched and tired many of the different solution but none have worked thus far, I'm running 8.04 Hardy Heron

I found the msttcorefonts, version 2.6, in Synaptic. They are in the multiverse repository.

---

### Post by chopwet on 2009-07-06
> **Ra-Hoor-Khuit said:**
> Try using ```
sudo apt-get install ubuntu-restricted-extras
```That metapackage contains the msttcorefonts package you need.

If you still get errors try using a different server via the Software Sources "Download From" button.

back to square one:

Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Setting up gstreamer0.10-pitfdll (0.9.1.1+cvs20080215-1) ...
Setting up ubuntu-restricted-extras (15.2) ...
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by chopwet on 2009-07-06
> **DeMus said:**
> I found the msttcorefonts, version 2.6, in Synaptic. They are in the multiverse repository.

when I try synaptic it shows me that I have already installed msttcorefonts, I cannot get rid of them either (do I have to uninstall all my Windows apps first?)

---

### Post by DeMus on 2009-07-06
> **chopwet said:**
> when I try synaptic it shows me that I have already installed msttcorefonts, I cannot get rid of them either (do I have to uninstall all my Windows apps first?)

No, no need to get rid of your Windows apps. It should be possible to uninstall the fonts using Synaptic.
When this does not work you are having other problems, more serious problems. Sorry, but I can't help you with those.

---

### Post by koshari on 2009-07-07
it may have been better to use a symlink from the wine font location to the linux font location

---

### Post by chopwet on 2009-07-08
> **Ra-Hoor-Khuit said:**
> Try using ```
sudo apt-get install ubuntu-restricted-extras
```That metapackage contains the msttcorefonts package you need.

If you still get errors try using a different server via the Software Sources "Download From" button.

ok I'm still getting:

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

Playing around with the software sources now! I changed the server and ticked some of the boxes that were unticked, now when I try to update I get GPG errors!

---

### Post by chopwet on 2009-07-10
> **DeMus said:**
> No, no need to get rid of your Windows apps. It should be possible to uninstall the fonts using Synaptic.
 When this does not work you are having other problems, more serious problems. Sorry, but I can't help you with those.


That's what I was afraid of! Looks like its getting closer to reinstall time!

---

### Post by jmcgovern on 2009-07-10
> **chopwet said:**
> Now I seem to get this problem when trying to run the update manager:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy Release: The following signatures were invalid: NODATA 1 NODATA 2

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: Failed to fetch [http://th.archive.ubuntu.com/ubuntu/dists/hardy/Release](http://th.archive.ubuntu.com/ubuntu/dists/hardy/Release)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.


I'm really starting to regret ever having put **wine** on my machine, and I still can't get either Safari nor IE to work

I see "edgy" in those lines a couple times, but also hardy too.  which are you using?  the Edgy repos were disabled months ago.

---

### Post by chopwet on 2009-07-10
> **jmcgovern said:**
> I see "edgy" in those lines a couple times, but also hardy too.  which are you using?  the Edgy repos were disabled months ago.

I'm using Hardy Heron 8.04, so what should I do?

---

### Post by chopwet on 2009-07-10
So now when I try to run update manager I get:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by chopwet on 2009-07-10
> **jmcgovern said:**
> I see "edgy" in those lines a couple times, but also hardy too.  which are you using?  the Edgy repos were disabled months ago.

I unchecked a few boxes in the software sources list (namely the edgy and cd rom related stuff, no more error messages!)

---

### Post by aaronLund on 2009-11-02
Just installed karmic!  Nice!

However, after doing a sudo apt-get install msttcorefonts (which was successful), it seems I still don't have them.

I've even restarted.

Am I forgetting something silly?

Thanks.

---

### Post by coffeecat on 2009-11-02
How exactly do you mean that you don't have them? Can you not find them in Appearance > Fonts? Or in OpenOffice? Or some other apps?

If you can't find them in those sorts of places, it's just possible that the installation failed to do a font cache regeneration, although I've never heard of that happening. Try:

```
sudo fc-cache -f -v
```If that doesn't work, try reinstalling, and if that doesn't work, I haven't a clue.

The other way to install MS fonts (if you have access to the .ttf files from your Windows machine) is to create a hidden folder in your home directory: ~/.fonts. Simply copy the .ttf files into there and they should be immediately available - but only to that account.

---

### Post by aaronLund on 2009-11-02
Thanks, coffeecat.

This is probably a really stupid question.....so I apologize...

But how/when will my new msttcorefonts "show up" (in my browser, etc)?

I know the install of the fonts worked (as did your fccache bit) but when will my visited web pages start looking "normal"?

Right now, they still look like the generic versions of the installed ubuntu fonts.

It's been so long since I've done this that I'm convinced I'm neglecting to do something really simple. Restarting my browser, maybe?

Thanks again.

---

### Post by coffeecat on 2009-11-03
By browser, I presume you mean Firefox. Yes, you have to set them in Firefox. It's a regular task for me to get Firefox to show Verdana as the default font - which I happen to prefer - whenever I do a new install.

In Firefox go to Edit > Preferences > Content tab, and then click on the Advanced button by Fonts and Colours. You can set your default fonts there. That's for FF 3.0.15 in Jaunty. There are some changes to the Preferences tab layout in FF3.5 in Karmic but you should be able to find the font preferences easily enough.

---

### Post by aaronLund on 2009-11-04
Hey thanks again for the reply, coffeecat.

However, in all of my linux installs (started with Hardy a few years ago), I've never had to enter anything into my Firefox preferences.

I guess that was the purpose of my submission of this question to this thread......Basically, what is the process that lets Firefox (and any other application that reads fonts) use these msttcorefonts?  Perhaps I simply need to move a file somewhere?

It wasn't this "hard" (and I use the term lightly) on any other install?

Do I have to make a .fonts folder in my home folder for Firefox, etc to find them?

As it stands they do not seem to be being used.  

If I do a "locate msttcorefonts", I get:

```
/usr/share/fonts/truetype/msttcorefonts
/usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf
/usr/share/fonts/truetype/msttcorefonts/Arial.ttf
/usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf
/usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf
/usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf
/usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf
/usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS.ttf
/usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS_Bold.ttf
/usr/share/fonts/truetype/msttcorefonts/Courier_New.ttf
/usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold.ttf
/usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold_Italic.ttf
/usr/share/fonts/truetype/msttcorefonts/Courier_New_Italic.ttf
/usr/share/fonts/truetype/msttcorefonts/Georgia.ttf
/usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf
/usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf
/usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf
/usr/share/fonts/truetype/msttcorefonts/Impact.ttf
/usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf
/usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf
/usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold_Italic.ttf
/usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Italic.ttf
/usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf
/usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf
/usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold_Italic.ttf
/usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Italic.ttf
/usr/share/fonts/truetype/msttcorefonts/Verdana.ttf
/usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf
/usr/share/fonts/truetype/msttcorefonts/Verdana_Bold_Italic.ttf
/usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf
/usr/share/fonts/truetype/msttcorefonts/Webdings.ttf
/usr/share/fonts/truetype/msttcorefonts/andalemo.ttf
/usr/share/fonts/truetype/msttcorefonts/arial.ttf
/usr/share/fonts/truetype/msttcorefonts/arialbd.ttf
/usr/share/fonts/truetype/msttcorefonts/arialbi.ttf
/usr/share/fonts/truetype/msttcorefonts/ariali.ttf
/usr/share/fonts/truetype/msttcorefonts/ariblk.ttf
/usr/share/fonts/truetype/msttcorefonts/comic.ttf
/usr/share/fonts/truetype/msttcorefonts/comicbd.ttf
/usr/share/fonts/truetype/msttcorefonts/cour.ttf
/usr/share/fonts/truetype/msttcorefonts/courbd.ttf
/usr/share/fonts/truetype/msttcorefonts/courbi.ttf
/usr/share/fonts/truetype/msttcorefonts/couri.ttf
/usr/share/fonts/truetype/msttcorefonts/georgia.ttf
/usr/share/fonts/truetype/msttcorefonts/georgiab.ttf
/usr/share/fonts/truetype/msttcorefonts/georgiai.ttf
/usr/share/fonts/truetype/msttcorefonts/georgiaz.ttf
/usr/share/fonts/truetype/msttcorefonts/impact.ttf
/usr/share/fonts/truetype/msttcorefonts/times.ttf
/usr/share/fonts/truetype/msttcorefonts/timesbd.ttf
/usr/share/fonts/truetype/msttcorefonts/timesbi.ttf
/usr/share/fonts/truetype/msttcorefonts/timesi.ttf
/usr/share/fonts/truetype/msttcorefonts/trebuc.ttf
/usr/share/fonts/truetype/msttcorefonts/trebucbd.ttf
/usr/share/fonts/truetype/msttcorefonts/trebucbi.ttf
/usr/share/fonts/truetype/msttcorefonts/trebucit.ttf
/usr/share/fonts/truetype/msttcorefonts/verdana.ttf
/usr/share/fonts/truetype/msttcorefonts/verdanab.ttf
/usr/share/fonts/truetype/msttcorefonts/verdanai.ttf
/usr/share/fonts/truetype/msttcorefonts/verdanaz.ttf
/usr/share/fonts/truetype/msttcorefonts/webdings.ttf
/var/lib/msttcorefonts
/var/lib/msttcorefonts/cabfiles.sha256sums
/var/lib/msttcorefonts/ms-fonts

```

Also, as a web developer, changing Firefox's preferences feels like tainting my web experience.  Again, I'm 100% convinced I'm just forgetting/neglecting to do something ridiculously simple.

Thanks again.

---

### Post by coffeecat on 2009-11-04
> **aaronLund said:**
> Do I have to make a .fonts folder in my home folder for Firefox, etc to find them?

Making a ~/.fonts folder is a perfectly good way of installing fonts, but only for that account holder - not system-wide. I've made up a tarball that contains the .ttf's of the MS fonts plus a few others I like to use. When I make a new install I simply put the .tgz in my home folder, double-click on it and it unwraps itself, creating ~/.fonts with all my fonts inside it. But that's just me being a smart-a***. :wink: I don't think it makes any difference to Firefox because sometimes I go with the msttcorefonts package instead.

> **aaronLund said:**
> Also, as a web developer, changing Firefox's preferences feels like tainting my web experience.

Point taken. I'm afraid I know next to nothing about web-coding but I thought that if the web-page designer had coded the font into the page, **and** the system had that font installed, then the browser would display the font. Otherwise it would go with the default font(s). In the Ubuntu version of Firefox they seem to be the Open-Source Serif and Sans. To my eyes they're OK-ish, but don't quite cut the mustard. Which is why I change the preferences. For example, on a fresh install, this forum renders with the Open Source Serif font - which I don't find pleasing. If I change the Firefox default to Verdana, then I see all the posts in Verdana - which I find easier on the eyes.

If you've seen a behaviour in Firefox in earlier version of Ubuntu, but not Karmic I'm sorry, I can't help. Have you tried looking at a web-page you know is coded for one of the MS fonts that you've installed?

---

