---
title: "Ubuntu firefox problems."
date: 2009-12-18
forum: General Help
---

### Post by Jotaro on 2009-12-18
Well, I have been trying to fix a flash problem, and accidentally removed a component from the Ubuntu firefox browser. So, is there a way I can reinstall the Ubuntu firefox browser to restore the defaults?

---

### Post by JBAlaska on 2009-12-18
Just use synaptic, search for your installed FF and choose mark for re-installation

---

### Post by Jotaro on 2009-12-18
> **JBAlaska said:**
> Just use synaptic, search for your installed FF and choose mark for re-installation
Well, what happened:
The browser started with Shockwave Flash 9.0 r999
and Shockwave Flash 10.0.
I somehow removed Shockwave Flash 10.0
"search for your installed FF" What does FF mean?
Also, thanks for the help.

---

### Post by Jotaro on 2009-12-18
Bump. Anybody there to able to help me with my problem?

---

### Post by snorkytheweasel on 2009-12-18
> **JBAlaska said:**
> Just use synaptic, search for your installed FF and choose mark for re-installation
Sadly, that didn't fix the problem. I'm not convinced that the procedure went correctly - it only took 2 minutes or so, and my connection isn't very fast (512 kbs).

---

### Post by Jotaro on 2009-12-18
Hmm..
Well, I need to know how to either reinstall Shockwave Flash 10.0, or how to reinstall the Ubuntu firefox browser. I am hoping to find the way to reinstall Shockwave Flash 10.0, as that will keep me from losing my bookmarks...

---

### Post by yavoh on 2009-12-18
System->Administration->Synaptic Package Manager.

Search "firefox".

Right click --> Mark for Reinstallation.

Apply.

That should do the trick!

---

### Post by Jotaro on 2009-12-18
> **yavoh said:**
> System->Administration->Synaptic Package Manager.

Search "firefox".

Right click --> Mark for Reinstallation.

Apply.

That should do the trick!
I did those exact steps, but the Shockwave Flash 10.0 did not return. In fact, nothing changed, unless it is natural for everything in the last version to carry over into the new version...

---

### Post by Chronon on 2009-12-18
Re-install flashplugin-nonfree.

---

### Post by Jotaro on 2009-12-18
> **Chronon said:**
> Re-install flashplugin-nonfree.
I did that. The Shockwave Flash 10.0 plugin still didn't come back.:(

---

### Post by Chronon on 2009-12-18
Hmph.  you can always download it directly from Adobe and install it manually.  I am just using flashplugin-nonfree on my system, though.  Sorry I couldn't help.

---

### Post by Jotaro on 2009-12-18
> **Chronon said:**
> Hmph.  you can always download it directly from Adobe and install it manually.  I am just using flashplugin-nonfree on my system, though.  Sorry I couldn't help.
I went to Adobe to do that, but in the "Select a operating system" dropdown menu, there is no Linux option...

---

### Post by snorkytheweasel on 2009-12-18
> **yavoh said:**
> System->Administration->Synaptic Package Manager.

Search "firefox".

Right click --> Mark for Reinstallation.

Apply.

That should do the trick!

It didn't work - same symptoms remain.

---

### Post by daenoid on 2009-12-18
You may have to punt on this and download the latest release of Firefox. If Flash player (non-free) has been installed properly from Synaptic, open up a terminal window and try:

```
locate libflashplayer.so
```

More than likely this will return several different results. In particular you are looking for libflashplayer.so. From my experiences once Flash has been installed from Synaptic libflashplayer.so is placed in the /usr/lib/adobe-flashplugin/ directory. Something you can try is to cp the libflashplayer.so file into /home/username/.mozilla/plugins. 

If you go the route of downloading the latest version of Firefox its directory will also house a plugins directory. Simply place libflashplayer.so into it.

---

### Post by Jotaro on 2009-12-18
> **daenoid said:**
> You may have to punt on this and download the latest release of Firefox. If Flash player (non-free) has been installed properly from Synaptic, open up a terminal window and try:

```
locate libflashplayer.so
```More than likely this will return several different results. In particular you are looking for libflashplayer.so. From my experiences once Flash has been installed from Synaptic libflashplayer.so is placed in the /usr/lib/adobe-flashplugin/ directory. Something you can try is to cp the libflashplayer.so file into /home/username/.mozilla/plugins. 

If you go the route of downloading the latest version of Firefox its directory will also house a plugins directory. Simply place libflashplayer.so into it.
Ok, I entered that command line, and I got the following:

```
jordanfaulkner@jordanfaulkner-desktop:~$ locate libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so
jordanfaulkner@jordanfaulkner-desktop:~$
```

Ok, what should I do next?

---

### Post by daenoid on 2009-12-18
Okay...

```

cd .mozilla/plugins
cp /usr/lib/flashplugin-installer/libflashplayer.so ./

```

Restart Firefox and check to see if Flash is working for you now.

---

### Post by Jotaro on 2009-12-18
> **daenoid said:**
> Okay...

```

cd .mozilla/plugins
cp /usr/lib/flashplugin-installer/libflashplayer.so ./

```Restart Firefox and check to see if Flash is working for you now.
```
jordanfaulkner@jordanfaulkner-desktop:~$ cd .mozilla/plugins
bash: cd: .mozilla/plugins: No such file or directory
jordanfaulkner@jordanfaulkner-desktop:~$ 
```
That is what it said, so I tried the second command:
```
jordanfaulkner@jordanfaulkner-desktop:~$ cp /usr/lib/flashplugin-installer/libflashplayer.so ./
jordanfaulkner@jordanfaulkner-desktop:~$ 
```
Did I do something wrong?

---

### Post by snorkytheweasel on 2009-12-18
> **yavoh said:**
> System->Administration->Synaptic Package Manager.

Search "firefox".

Right click --> Mark for Reinstallation.

Apply.

That should do the trick!

Sadly, that didn't fix the problem.

---

### Post by unmole on 2009-12-18
Do a ```
 sudo aptitude purge firefox-3.5 
```
Then try installing firefox again.

---

### Post by Jotaro on 2009-12-18
> **unmole said:**
> Do a ```
 sudo aptitude purge firefox-3.5 
```Then try installing firefox again.
Ok, I will try that, but before I do, could you give me the command to type in to reinstall it?

---

### Post by daenoid on 2009-12-18
> **Jotaro said:**
> Did I do something wrong?

No, you didn't do anything wrong. But I'm wondering now if you actually have Firefox installed at all. The .mozilla directory should be in your home directory with Firefox 3.5. Try purging it from Synaptic and reinstalling it. Then repeat the previous commands.

```
sudo apt-get purge firefox-3.5
sudo apt-get install firefox-3.5

```

Just fyi, you effectively copied libflashplayer.so to your home directory.

---

### Post by bilalakhtar on 2009-12-18
Make sure the ubufox plugin is installed.
```
sudo apt-get install ubufox
```

---

### Post by Jotaro on 2009-12-18
> **daenoid said:**
> No, you didn't do anything wrong. But I'm wondering now if you actually have Firefox installed at all. The .mozilla directory should be in your home directory with Firefox 3.5. Try purging it from Synaptic and reinstalling it. Then repeat the previous commands.

```
sudo apt-get purge firefox-3.5
sudo apt-get install firefox-3.5

```Just fyi, you effectively copied libflashplayer.so to your home directory.
Ok, I completed the commands, and my browser refreshed. The Shockwave Flash 10.0 plugin STILL didn't come back..
Any other ideas?:(

---

### Post by Jotaro on 2009-12-18
> **bilalakhtar said:**
> Make sure the ubufox plugin is installed.
```
sudo apt-get install ubufox
```
Ok, I entered that command. The Shockwave Flash 10.0 plugin still didn't return...:(

---

### Post by JBAlaska on 2009-12-18
Close your FF (Firefox) browser and enter this in a terminal:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by daenoid on 2009-12-18
Try this too...

```
sudo apt-get install adobe-flashplugin
```

---

### Post by Jotaro on 2009-12-18
> **JBAlaska said:**
> Close your FF (Firefox) browser and enter this in a terminal:
```
sudo apt-get install ubuntu-restricted-extras
```
Ok, I will copy the code, close the FF browser, enter it, and come back here now.:)

---

### Post by Jotaro on 2009-12-18
> **JBAlaska said:**
> Close your FF (Firefox) browser and enter this in a terminal:
```
sudo apt-get install ubuntu-restricted-extras
```
Ok, I'm back. This is what it did:
```
Unpacking libdirac0c2a (from .../libdirac0c2a_1.0.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libfaad0.
Unpacking libfaad0 (from .../libfaad0_2.6.1-3.1_i386.deb) ...
Selecting previously deselected package libiptcdata0.
Unpacking libiptcdata0 (from .../libiptcdata0_1.0.3-1ubuntu1_i386.deb) ...
Selecting previously deselected package libxml++2.6-2.
Unpacking libxml++2.6-2 (from .../libxml++2.6-2_2.26.0-2_i386.deb) ...
Selecting previously deselected package libffado1.
Unpacking libffado1 (from .../libffado1_2.0~rc2+svn1569-2ubuntu1_i386.deb) ...
Selecting previously deselected package libfreebob0.
Unpacking libfreebob0 (from .../libfreebob0_1.0.11-1build1_i386.deb) ...
Selecting previously deselected package libjack0.
Unpacking libjack0 (from .../libjack0_0.116.1-4ubuntu2_i386.deb) ...
Selecting previously deselected package libkate1.
Unpacking libkate1 (from .../libkate1_0.3.3-1_i386.deb) ...
Selecting previously deselected package libmimic0.
Unpacking libmimic0 (from .../libmimic0_1.0.4-2_i386.deb) ...
Selecting previously deselected package libmms0.
Unpacking libmms0 (from .../libmms0_0.4-2_i386.deb) ...
Selecting previously deselected package libmodplug0c2.
Unpacking libmodplug0c2 (from .../libmodplug0c2_1%3a0.8.7-1_i386.deb) ...
Selecting previously deselected package libmpcdec3.
Unpacking libmpcdec3 (from .../libmpcdec3_1%3a1.2.2-2.1_i386.deb) ...
Selecting previously deselected package libfftw3-3.
Unpacking libfftw3-3 (from .../libfftw3-3_3.2.1-2ubuntu2_i386.deb) ...
Selecting previously deselected package libofa0.
Unpacking libofa0 (from .../libofa0_0.9.3-3ubuntu1_i386.deb) ...
Selecting previously deselected package libopenspc0.
Unpacking libopenspc0 (from .../libopenspc0_0.3.99a-2_i386.deb) ...
Selecting previously deselected package libsoundtouch1c2.
Unpacking libsoundtouch1c2 (from .../libsoundtouch1c2_1.3.1-2_i386.deb) ...
Selecting previously deselected package libwildmidi0.
Unpacking libwildmidi0 (from .../libwildmidi0_0.2.2-2_i386.deb) ...
Selecting previously deselected package gstreamer0.10-plugins-bad.
Unpacking gstreamer0.10-plugins-bad (from .../gstreamer0.10-plugins-bad_0.10.14-4ubuntu1_i386.deb) ...
Selecting previously deselected package libfaac0.
Unpacking libfaac0 (from .../libfaac0_1.26-0.1ubuntu2_i386.deb) ...
Selecting previously deselected package libquicktime1.
Unpacking libquicktime1 (from .../libquicktime1_2%3a1.1.1+debian-1build1_i386.deb) ...
Selecting previously deselected package libmjpegtools-1.9.
Unpacking libmjpegtools-1.9 (from .../libmjpegtools-1.9_1%3a1.9.0-0.5ubuntu1_i386.deb) ...
Selecting previously deselected package libxvidcore4.
Unpacking libxvidcore4 (from .../libxvidcore4_2%3a1.1.2-0.1ubuntu4_i386.deb) ...
Selecting previously deselected package gstreamer0.10-plugins-bad-multiverse.
Unpacking gstreamer0.10-plugins-bad-multiverse (from .../gstreamer0.10-plugins-bad-multiverse_0.10.13-0ubuntu1_i386.deb) ...
Selecting previously deselected package libmp3lame0.
Unpacking libmp3lame0 (from .../libmp3lame0_3.98.2+debian-0ubuntu2_i386.deb) ...
Selecting previously deselected package libx264-67.
Unpacking libx264-67 (from .../libx264-67_1%3a0.svn20090621+git364d7d-0ubuntu2_i386.deb) ...
Selecting previously deselected package gstreamer0.10-plugins-ugly-multiverse.
Unpacking gstreamer0.10-plugins-ugly-multiverse (from .../gstreamer0.10-plugins-ugly-multiverse_0.10.12-0ubuntu1_i386.deb) ...
Selecting previously deselected package libmp4v2-0.
Unpacking libmp4v2-0 (from .../libmp4v2-0_1%3a1.6dfsg-0.2ubuntu5_i386.deb) ...
Selecting previously deselected package ttf-liberation.
Unpacking ttf-liberation (from .../ttf-liberation_1.05.1.20090721-0ubuntu1_all.deb) ...
Selecting previously deselected package ttf-mscorefonts-installer.
Unpacking ttf-mscorefonts-installer (from .../ttf-mscorefonts-installer_3.0_all.deb) ...
Selecting previously deselected package ubuntu-restricted-extras.
Unpacking ubuntu-restricted-extras (from .../ubuntu-restricted-extras_36_i386.deb) ...
Selecting previously deselected package w32codecs.
Unpacking w32codecs (from .../w32codecs_20071007-0medibuntu5_i386.deb) ...
Processing triggers for man-db ...
Setting up cabextract (1.2-3) ...
Setting up freepats (20060219-1) ...
Setting up gstreamer0.10-pitfdll (0.9.1.1+cvs20080215-1ubuntu1) ...
Setting up libenca0 (1.9-7) ...

Setting up libass3 (0.9.6-1) ...

Setting up libcdaudio1 (0.99.12p2-7) ...

Setting up libcelt0 (0.6.1-1) ...

Setting up libdc1394-22 (2.1.2-1) ...

Setting up libdca0 (0.0.5-3) ...

Setting up libdirac0c2a (1.0.2-0ubuntu1) ...

Setting up libfaad0 (2.6.1-3.1) ...

Setting up libiptcdata0 (1.0.3-1ubuntu1) ...

Setting up libxml++2.6-2 (2.26.0-2) ...

Setting up libffado1 (2.0~rc2+svn1569-2ubuntu1) ...

Setting up libfreebob0 (1.0.11-1build1) ...

Setting up libjack0 (0.116.1-4ubuntu2) ...

Setting up libkate1 (0.3.3-1) ...

Setting up libmimic0 (1.0.4-2) ...

Setting up libmms0 (0.4-2) ...

Setting up libmodplug0c2 (1:0.8.7-1) ...

Setting up libmpcdec3 (1:1.2.2-2.1) ...

Setting up libfftw3-3 (3.2.1-2ubuntu2) ...

Setting up libofa0 (0.9.3-3ubuntu1) ...

Setting up libopenspc0 (0.3.99a-2) ...

Setting up libsoundtouch1c2 (1.3.1-2) ...

Setting up libwildmidi0 (0.2.2-2) ...

Setting up gstreamer0.10-plugins-bad (0.10.14-4ubuntu1) ...

Setting up libfaac0 (1.26-0.1ubuntu2) ...

Setting up libquicktime1 (2:1.1.1+debian-1build1) ...

Setting up libmjpegtools-1.9 (1:1.9.0-0.5ubuntu1) ...

Setting up libxvidcore4 (2:1.1.2-0.1ubuntu4) ...

Setting up gstreamer0.10-plugins-bad-multiverse (0.10.13-0ubuntu1) ...
Setting up libmp3lame0 (3.98.2+debian-0ubuntu2) ...

Setting up libx264-67 (1:0.svn20090621+git364d7d-0ubuntu2) ...

Setting up gstreamer0.10-plugins-ugly-multiverse (0.10.12-0ubuntu1) ...
Setting up libmp4v2-0 (1:1.6dfsg-0.2ubuntu5) ...

Setting up ttf-liberation (1.05.1.20090721-0ubuntu1) ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-liberation
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.

Setting up ttf-mscorefonts-installer (3.0) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-12-18 02:22:09--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://hivelocity.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2009-12-18 02:22:11--  http://hivelocity.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving hivelocity.dl.sourceforge.net... 74.50.111.26
Connecting to hivelocity.dl.sourceforge.net|74.50.111.26|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://downloads.sourceforge.net/project/corefonts/the%2520fonts/final/andale32.exe?download&failedmirror=hivelocity.dl.sourceforge.net [following]
--2009-12-18 02:22:12--  http://downloads.sourceforge.net/project/corefonts/the%2520fonts/final/andale32.exe?download&failedmirror=hivelocity.dl.sourceforge.net
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2009-12-18 02:22:12--  http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving iweb.dl.sourceforge.net... 70.38.0.134
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198384 (194K) [application/x-msdos-program]
Saving to: `./andale32.exe'

100%[======================================>] 198,384      358K/s   in 0.5s    

2009-12-18 02:22:13 (358 KB/s) - `./andale32.exe' saved [198384/198384]

--2009-12-18 02:22:13--  http://downloads.sourceforge.net/corefonts/arialb32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe [following]
--2009-12-18 02:22:14--  http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe
Resolving iweb.dl.sourceforge.net... 70.38.0.134
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168176 (164K) [application/x-msdos-program]
Saving to: `./arialb32.exe'

100%[======================================>] 168,176      351K/s   in 0.5s    

2009-12-18 02:22:14 (351 KB/s) - `./arialb32.exe' saved [168176/168176]

--2009-12-18 02:22:14--  http://downloads.sourceforge.net/corefonts/arial32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following]
--2009-12-18 02:22:15--  http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Resolving cdnetworks-us-2.dl.sourceforge.net... 65.49.46.188
Connecting to cdnetworks-us-2.dl.sourceforge.net|65.49.46.188|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554208 (541K) [application/octet-stream]
Saving to: `./arial32.exe'

100%[======================================>] 554,208      431K/s   in 1.3s    

2009-12-18 02:22:16 (431 KB/s) - `./arial32.exe' saved [554208/554208]

--2009-12-18 02:22:16--  http://downloads.sourceforge.net/corefonts/comic32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://hivelocity.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe [following]
--2009-12-18 02:22:17--  http://hivelocity.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe
Resolving hivelocity.dl.sourceforge.net... 74.50.111.26
Connecting to hivelocity.dl.sourceforge.net|74.50.111.26|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://downloads.sourceforge.net/project/corefonts/the%2520fonts/final/comic32.exe?download&failedmirror=hivelocity.dl.sourceforge.net [following]
--2009-12-18 02:22:17--  http://downloads.sourceforge.net/project/corefonts/the%2520fonts/final/comic32.exe?download&failedmirror=hivelocity.dl.sourceforge.net
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe [following]
--2009-12-18 02:22:17--  http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe
Resolving iweb.dl.sourceforge.net... 70.38.0.134
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246008 (240K) [application/x-msdos-program]
Saving to: `./comic32.exe'

100%[======================================>] 246,008      467K/s   in 0.5s    

2009-12-18 02:22:18 (467 KB/s) - `./comic32.exe' saved [246008/246008]

--2009-12-18 02:22:18--  http://downloads.sourceforge.net/corefonts/courie32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe [following]
--2009-12-18 02:22:18--  http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe
Resolving iweb.dl.sourceforge.net... 70.38.0.134
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646368 (631K) [application/x-msdos-program]
Saving to: `./courie32.exe'

100%[======================================>] 646,368      646K/s   in 1.0s    

2009-12-18 02:22:19 (646 KB/s) - `./courie32.exe' saved [646368/646368]

--2009-12-18 02:22:19--  http://downloads.sourceforge.net/corefonts/georgi32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://hivelocity.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe [following]
--2009-12-18 02:22:19--  http://hivelocity.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe
Resolving hivelocity.dl.sourceforge.net... 74.50.111.26
Connecting to hivelocity.dl.sourceforge.net|74.50.111.26|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://downloads.sourceforge.net/project/corefonts/the%2520fonts/final/georgi32.exe?download&failedmirror=hivelocity.dl.sourceforge.net [following]
--2009-12-18 02:22:20--  http://downloads.sourceforge.net/project/corefonts/the%2520fonts/final/georgi32.exe?download&failedmirror=hivelocity.dl.sourceforge.net
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe [following]
--2009-12-18 02:22:20--  http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 392440 (383K) [application/octet-stream]
Saving to: `./georgi32.exe'

100%[======================================>] 392,440     1.10M/s   in 0.3s    

2009-12-18 02:22:20 (1.10 MB/s) - `./georgi32.exe' saved [392440/392440]

--2009-12-18 02:22:20--  http://downloads.sourceforge.net/corefonts/impact32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe [following]
--2009-12-18 02:22:21--  http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe
Resolving voxel.dl.sourceforge.net... 208.122.28.20, 208.122.28.21, 208.122.28.26, ...
Connecting to voxel.dl.sourceforge.net|208.122.28.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 173288 (169K) [application/octet-stream]
Saving to: `./impact32.exe'

100%[======================================>] 173,288      389K/s   in 0.4s    

2009-12-18 02:22:21 (389 KB/s) - `./impact32.exe' saved [173288/173288]

--2009-12-18 02:22:21--  http://downloads.sourceforge.net/corefonts/times32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe [following]
--2009-12-18 02:22:22--  http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe
Resolving voxel.dl.sourceforge.net... 208.122.28.20, 208.122.28.21, 208.122.28.26, ...
Connecting to voxel.dl.sourceforge.net|208.122.28.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 661728 (646K) [application/octet-stream]
Saving to: `./times32.exe'

100%[======================================>] 661,728      693K/s   in 0.9s    

2009-12-18 02:22:23 (693 KB/s) - `./times32.exe' saved [661728/661728]

--2009-12-18 02:22:23--  http://downloads.sourceforge.net/corefonts/trebuc32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe [following]
--2009-12-18 02:22:23--  http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe
Resolving voxel.dl.sourceforge.net... 208.122.28.11, 208.122.28.12, 208.122.28.18, ...
Connecting to voxel.dl.sourceforge.net|208.122.28.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357200 (349K) [application/octet-stream]
Saving to: `./trebuc32.exe'

100%[======================================>] 357,200      566K/s   in 0.6s    

2009-12-18 02:22:24 (566 KB/s) - `./trebuc32.exe' saved [357200/357200]

--2009-12-18 02:22:24--  http://downloads.sourceforge.net/corefonts/verdan32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe [following]
--2009-12-18 02:22:24--  http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe
Resolving iweb.dl.sourceforge.net... 70.38.0.134
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 351992 (344K) [application/x-msdos-program]
Saving to: `./verdan32.exe'

100%[======================================>] 351,992      518K/s   in 0.7s    

2009-12-18 02:22:25 (518 KB/s) - `./verdan32.exe' saved [351992/351992]

--2009-12-18 02:22:25--  http://downloads.sourceforge.net/corefonts/webdin32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe [following]
--2009-12-18 02:22:25--  http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe
Resolving cdnetworks-us-2.dl.sourceforge.net... 65.49.46.188
Connecting to cdnetworks-us-2.dl.sourceforge.net|65.49.46.188|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 185072 (181K) [application/octet-stream]
Saving to: `./webdin32.exe'

100%[======================================>] 185,072      347K/s   in 0.5s    

2009-12-18 02:22:26 (347 KB/s) - `./webdin32.exe' saved [185072/185072]

andale32.exe: OK
Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
arialb32.exe: OK
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
arial32.exe: OK
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
comic32.exe: OK
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
courie32.exe: OK
Extracting cabinet: courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
georgi32.exe: OK
Extracting cabinet: georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
impact32.exe: OK
Extracting cabinet: impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
times32.exe: OK
Extracting cabinet: times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
trebuc32.exe: OK
Extracting cabinet: trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
verdan32.exe: OK
Extracting cabinet: verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
webdin32.exe: OK
Extracting cabinet: webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.
Updating fontconfig cache for /usr/share/fonts/truetype/msttcorefonts
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.

Setting up ubuntu-restricted-extras (36) ...
Setting up w32codecs (20071007-0medibuntu5) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```
After this, I went to Tools->Add Ons-> Plugins. The Shockwave Flash 10.0 didn't appear....

---

### Post by daenoid on 2009-12-18
There's some confusion here and it is partially my fault. It's late and this lapse my mind. 

The package flashplayer-plugin = Adobe Flash Player 9.

Package adobe-flashplugin = Adobe Flash Player 10.

Make sure you install adobe-flashplugin.

```
sudo apt-get install adobe-flashplugin
```

---

### Post by Jotaro on 2009-12-18
> **daenoid said:**
> There's some confusion here and it is partially my fault. It's late and this lapse my mind. 

The package flashplayer-plugin = Adobe Flash Player 9.

Package adobe-flashplugin = Adobe Flash Player 10.

Make sure you install adobe-flashplugin.

```
sudo apt-get install adobe-flashplugin
```
Yeah, I understand. I am pretty tired myself.
Well, I entered it and got this:
```
jordanfaulkner@jordanfaulkner-desktop:~$ sudo apt-get install adobe-flashplugin
[sudo] password for jordanfaulkner: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  firefox konqueror-nsplugins ttf-bitstream-vera ttf-dejavu
  ttf-xfree86-nonfree xfs
The following packages will be REMOVED:
  flashplugin-installer flashplugin-nonfree
The following NEW packages will be installed:
  adobe-flashplugin
0 upgraded, 1 newly installed, 2 to remove and 8 not upgraded.
Need to get 4,022kB of archives.
After this operation, 10.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.canonical.com karmic/partner adobe-flashplugin 10.0.42.34-2karmic1 [4,022kB]
Fetched 4,022kB in 4s (978kB/s)              
(Reading database ... 160235 files and directories currently installed.)
Removing flashplugin-nonfree ...
Removing flashplugin-installer ...
Selecting previously deselected package adobe-flashplugin.
(Reading database ... 160225 files and directories currently installed.)
Unpacking adobe-flashplugin (from .../adobe-flashplugin_10.0.42.34-2karmic1_i386.deb) ...
Setting up adobe-flashplugin (10.0.42.34-2karmic1) ...
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/iceape/plugins/flashplugin-alternative.so (iceape-flashplugin) in auto mode.
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/iceweasel/plugins/flashplugin-alternative.so (iceweasel-flashplugin) in auto mode.
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/mozilla/plugins/flashplugin-alternative.so (mozilla-flashplugin) in auto mode.
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/firefox/plugins/flashplugin-alternative.so (firefox-flashplugin) in auto mode.
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/xulrunner/plugins/flashplugin-alternative.so (xulrunner-flashplugin) in auto mode.
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/midbrowser/plugins/flashplugin-alternative.so (midbrowser-flashplugin) in auto mode.
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so (xulrunner-addons-flashplugin) in auto mode.

```I checked, and....the plugin is back! Thank you so much!!!=D>
So, I will be heading to bed. The other problem is optional, while that one was absolutely needed.

---

### Post by lovinglinux on 2009-12-18
Close Firefox, then delete the **libflashplayer.so** file from ~/.mozilla/plugins then run this:

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

Then go to your FF profile folder (in some folder under ~/.mozilla/firefox) and delete the file **pluginreg.dat**. Start firefox.

---

### Post by JBAlaska on 2009-12-18
Dang... I do this all the time>> If your terminal buffer was set higher, you would seee it installed Sun Java as well as flash:

[B]ubuntu-restricted-extras is a package for Ubuntu, that allows the user to install essential software which is not already included due to legal or copyright reasons.
It is a meta-package that installs:

    * Support for MP3 and unencrypted DVD playback
    * Microsoft TrueType core fonts
    * [COLOR="Red"]Flash plugin[/COLOR]
    * codecs for common audio and video files[/B]
[[IMG]http://img31.imageshack.us/img31/8249/flashc.th.png[/IMG]](http://img31.imageshack.us/i/flashc.png/)

**Go to youtube and view a video...does it play??**

---

