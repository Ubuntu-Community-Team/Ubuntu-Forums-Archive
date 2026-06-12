---
title: "What Am I Missing?"
date: 2009-12-08
forum: General Help
---

### Post by SoulMazer on 2009-12-08
Okay, this is really starting to get frustrating. Let's say I go to [this page (link)]("http://www.engadget.com/2009/12/08/dell-vostro-v13-hands-on-impressions-yes/") and I want to watch the video on it. I will click on the "Play" button yet nothing happens. I BELIEVE this has to do with flash, but correct me if I am wrong. I currently have both the Flash and Java plugins installed on my 64 bit 9.10 system, and still no avail.

Also, the browser is not part of the problem. This problem recurs on both Chrome and Firefox.

What can I do?

Thanks in advance.

---

### Post by Leppie on 2009-12-08
Try removing flash and installing the the x64 version:
```
sudo apt-get remove --purge flashplugin-nonfree
sudo apt-get remove flashplugin-installer
sudo apt-get remove --purge swfdec-mozilla
```

Download the 64 bit version from the [adobe labs page]("http://labs.adobe.com/downloads/flashplayer10.html") and extract the file.

For firefox copy the plugin to one of these locations (you may have to try them one by one):
```
/usr/lib/adobe-flashplugin
/usr/lib/firefox-addons/plugins
/usr/lib/mozilla/plugins
```

For chrome, copy the file to this location:
```
/opt/google/chrome/plugin
```

If the location of your chrome isn't in /opt, you can find the location like this:
```
$which chrome
```

Once done, you it should work with the flash plugin for x64 machines.

---

### Post by SoulMazer on 2009-12-08
Okay, well I downloaded the file and copied the .so to /opt/google/chrome/plugin and now when I visit the site, the area which should contain the video appears as a blank box.

A "ls" of /opt/google/chrome/ reveals that "plugin" is not a directory, but an executable file.

So..what next?

Thanks again.

---

### Post by Leppie on 2009-12-08
Are you sure /opt/google is your chrome location?
Also, how did you copy the file?
There is a difference between:
```
$sudo cp /src/file.so /dest
```
and:
```
$sudo cp /src/file.so /dest/
```

The trailing slash indicates you're copying to a directory, if omitted the file will be renamed to the name of the directory you were copying to. But this usually would generate an error unless the destination directory doesn't exist.
Have you tried to locate chrome first?
```
$which chrome
```

---

### Post by SoulMazer on 2009-12-08
My mistake, I forgot the tailing slash. Anyways...I just did a complete removal of Chrome then reinstalled it...it did not create a "plugin" directory. So: I made one myself. I copied the .so file to this new directory. No luck; still the white box of nothing. And yes, I know I copied it correctly this time. ```
$ ls /opt/google/chrome/plugin
libflashplayer.so
```

Also, a "which chrome" returns nothing. However, I know it is installed to /opt/google/chrome, since that's where it has seemed to place all of its files.

Thanks again.

---

### Post by Leppie on 2009-12-08
Have you tried the other locations as well?
Is it only chrome not playing flash, or can you not view flash in ff either?

---

### Post by SoulMazer on 2009-12-08
I just tried all three locations you supplied for ff with no avail either.

Thanks again.

---

### Post by Leppie on 2009-12-08
Chrome may need a command line option to be passed when launched to activate the flash plugin.
Right click on the application menu bar and select "Edit Menus", under applications find the "Internet" section, select "Google Chrome" and click the "Properties" button. In the command field add " --enable-plugins %U" so it looks like this:
```
/opt/google/chrome/google-chrome --enable-plugins %U
```

As you can see, this will actually also show you the exact location of chrome. So you can copy the flash plugin to the correct folder if needed.

Not sure why ff doesn't play flash, have you tried to restart your system? I know this sounds more like a windoze thing, but sometimes it frees your system from temporary "errors".

---

### Post by SoulMazer on 2009-12-08
Okay, well it was copied to the right folder. And the restart didn't seem to have an effect. Is there something my system does not like about the plugin itself? Or is it just a coincidence that it doesn't work on either Chrome or FF?

EDIT: Well, I've come to a certain conclusion. If I just install the "flashplugin-installer" package (32 bit?), Flash barely works. If I click on say the "Play" button of a video, it might take about twenty clicks, but it usually works. However, I would like a different solution if I could find one.

---

### Post by Leppie on 2009-12-09
I have recently installed 64bit flash on a system and it works like a charm. I've never tried it with chrome though (ff and opera).

in ff, have you tried recreating your profile?

Edit:
try copying the plugin to this /usr/lib/flashplugin-installer/libflashplayer.so as well.

Edit:
My apologies, but I only just now noticed a typo I made. Change /opt/google/chrome/plugin to /opt/google/chrome/plugins (if you cd into /opt/google/chrome and do sudo mv plugin plugins).

---

### Post by SoulMazer on 2009-12-09
Well the changing the folder name to "plugins" did it for me. So now pretty much every site I visit works flawlessly except for one I use pretty frequently. Since I am in school, I have the ability to visit a website and view my textbooks online. Every part of this website (I believe it is Flash driven?) works flawlessly except for the virtual scrollbar for the page (not the browser scrollbar, they have a Flash(?) one). Is this a problem on their side or my side?

However, now Flash works flawlessly on every site except for this one. Thank you so much for the continued support.

---

