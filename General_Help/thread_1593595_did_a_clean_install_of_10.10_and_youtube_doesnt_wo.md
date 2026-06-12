---
title: "did a clean install of 10.10 and youtube doesnt work on Mozila Firefox"
date: 2010-10-11
forum: General Help
---

### Post by linuxguy86 on 2010-10-11
I did a clean install of Ubuntu 10.10 and it seems to work fine, maybe just a little slow, and I have recently found out that youtube doesnt work on Firefox, so I dowonloaded google chrome and it works on their.  I did install the Flash plugin but still no it just shows a black screen.

---

### Post by gheorghe_pop on 2010-10-11
Hello,

I have a similar problem with firefox. When I'm going to youtoube and try to play a movie I stay 30-40s till the movie starts to play. And in google chrome it starts imediatly to play. Also I've observed that websites are loading much faster in chrome than in firefox.

I've tryed the same youtube movie in windows with firefox and IE and no problem.

I don't know what is wrong because I've tryed all the possible reasons including DNS;proxy and so on.

To mention that also evolution is extreamly slow on loding html mails.

Thanks for any help.

---

### Post by linuxguy86 on 2010-10-11
It seem to work find when I had 10.04 installed but for some reason I dont know if it is a bug or what, I cant play youtube videos on firefox with the new verision.

---

### Post by carlomagn0 on 2010-10-12
Hi, I am in the same situation.. I don't know Why I can not see videos ON YOUTUBE.

Please any help with this??

Thanks.

---

### Post by AAllInFlynn on 2010-10-12
try the following:

1.  Ensure you have the following package repositories selected in Synaptic.  Goto the Settings > Repositories.  Then select the Other Software tab.  Ensure that Canonical Partners is select by checking the box next to that option.

2.  Exit Synaptic and run the following commands:

sudo apt-get update
sudo apt-get install flashplugin-installer

3.  Enjoy youtube!

Note:  Adobe flash is pre-packaged with both Google Chrome and the open source Chromium alternative.  You have to install the flashplugin-installer in order for Adobe Flash to work with Firefox.  There are also open soure flash alternative packages, however, I find that they do not work as reliably as the Adobe Flash variant.

---

### Post by carlomagn0 on 2010-10-12
Thank you!

---

### Post by garvinrick4 on 2010-10-12
Now in 10.10 you can check the box at install to download updates and 3rd party and it will give you your flash at install. Still run 
```
sudo apt-get install ubuntu-restricted-extras
```You will get all your codecs and gstreamer. Make sure you have your
internet connection before you hit install. I am writing this for all the new ones not  just the Starter of this Thread.

---

### Post by garvinrick4 on 2010-10-12
```
rick@rick-HP-G71-Notebook-PC:~$ aptitude show ubuntu-restricted-extras
Package: ubuntu-restricted-extras 
State: installed
Automatically installed: no
Version: 42
Priority: optional
Section: multiverse/metapackages
Maintainer: Michael Vogt <michael.vogt@ubuntu.com>
Uncompressed Size: 36.9k
Depends: ubuntu-restricted-addons
Recommends: gstreamer0.10-plugins-ugly-multiverse, ttf-mscorefonts-installer,
            unrar, gstreamer0.10-plugins-bad-multiverse, libavcodec-extra-52,
            libmp4v2-0
Description: Commonly used restricted packages for Ubuntu
 This package depends on some commonly used packages in the Ubuntu multiverse
 repository. 
 
 Installing this package will pull in support for MP3 playback and decoding,
 support for various other audio formats (GStreamer plugins), Microsoft fonts,
 Java runtime environment, Flash plugin, LAME (to create compressed audio
 files), and DVD playback. 
 
 Please note that this does not install libdvdcss2, and will not let you play
 encrypted DVDs. For more information, see
 https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs 
 
 Please also note that packages from multiverse are restricted by copyright or
 legal issues in some countries. See http://www.ubuntu.com/ubuntu/licensing for
 more information.


```This is after checking to install updates and restricted at beginning of installation process.

---

