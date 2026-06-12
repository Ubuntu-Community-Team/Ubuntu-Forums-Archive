---
title: "What should I do?"
date: 2006-04-26
forum: General Help
---

### Post by justin2021 on 2006-04-26
Hi, as of right now, I have PCLinuxOS installed on my computer. I've been reading the great reviews about ubuntu and have a few questions. How is the availability of applications in terms of ubuntu on deb and PCLOS on rpm? Would ubuntu be good for programming, because recently I've been trying to learn python. Also, would I be able to code and compile Java on it? How is it media wise?  Would I be able to use DOS emulators for it? Thanks for the help. Ubuntu looks really tempting and so far (using the live at the moment) it seems like a good distro.:)

---

### Post by Nequeo on 2006-04-26
[QUOTE=justin2021]Hi, as of right now, I have PCLinuxOS installed on my computer. I've been reading the great reviews about ubuntu and have a few questions. How is the availability of applications in terms of ubuntu on deb and PCLOS on rpm? Would ubuntu be good for programming, because recently I've been trying to learn python. Also, would I be able to code and compile Java on it? How is it media wise?  Would I be able to use DOS emulators for it? Thanks for the help. Ubuntu looks really tempting and so far (using the live at the moment) it seems like a good distro.:)[/QUOTE]

Hi Justin (2021?),

Ubuntu's package availability is massive. here are hundreds of applications under 'Add/Remove Applications'. And tens of thousands more that you can install via apt-get/aptitude/synaptic. Take a look at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) if you want to search through everything that is in the Ubuntu repositories.  

Ubuntu is also an excellent Python developement platform. It comes with Python 2.4 and many, many, many additional bindings pre-installed. 

Java has to be added manually, but the instructions on this page: 
[https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Java#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Java#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca)
work perfectly with the latest Sun JDK (make sure you do not download the Netbeans bundle, though). In fact, I currently use Ubuntu + Vim + a nicely customised .vimrc to write Java apps for my University courses. Eclipse IDE is available in the repositories, too. 

Media wise, you will need to install all the non-free codecs yourself. It's a little more work up-front, but it can handle everything that PCLinux can. There are plenty of guides out there. Most of them are geared towards 5.10 at the moment. But if you go with  Dapper Beta, a good way to get started quickly is to open synaptic, search for 'gstreamer-plugin' and install everything you find. In particular gstreamer-plugins-ugly and gstreamer-plugins-ugly-multiverse.

(Disclaimer: Installing those plugins is probably illegal if you live in the U.S. )

I've used Dosbox under Ubuntu with no problems at all. 

Hope that answers your questions,

---

### Post by justin2021 on 2006-04-26
Thanks Nequeo, that helped out a lot. I may start downloading the Ubuntu installation cd in a moment to install. So if I wanted to play mp3s all I would need would be a media player and these gstreamer plugins? And what is the difference between the normal ones and the -ugly and -ugly-multiverse?

---

### Post by Nequeo on 2006-04-27
[QUOTE=justin2021]Thanks Nequeo, that helped out a lot. I may start downloading the Ubuntu installation cd in a moment to install. So if I wanted to play mp3s all I would need would be a media player and these gstreamer plugins? And what is the difference between the normal ones and the -ugly and -ugly-multiverse?[/QUOTE]

No problem. Well... all you really need is the codecs. My default Ubuntu installs two media-players. This is Ubuntu specific information, btw. If you're going to install Kubuntu, there is a slightly different process.

But Ubuntu, by default, comes with Totem and Rhymbox. Totem is primarily for movies, and Rhythmbox is closer to iTunes. The catch is, both those media players are just two different GUIs that use the same backend to play media files. That is, 'Gstreamer'. 

There are three main Gstreamed plugin packages. Good, Bad and Ugly. These are meta-packages, that have no files themselves but install a lot of other packages for you. 'Good' plugins are Free, well-maintained and working Open Source plugins. That is, ogg/vorbis, ogg/theora, speex and flac. 

'Bad' plugins are open source plugins that have something wrong with them. Maybe they work perfectly, but the package doesn't have a maintainer. Or maybe they're not well-tested. 

Ugly plugins are working plugins that might be illegal to distribute or install for people in certain countries. MP3s and DVDs being the most common examples.

Which reminds me, you'll also want to install the ffmpeg Gstreamer plugin, which lets you play some additional movie formats. 

A lot of people have had problems with Gstreamer. Things like stuttering DVDs, pauses between CD tracks and MP3s, etc. The version in Dapper is much better... And personally, I've never had any problems with it. But in any case you can also install Mplayer, VLC, Xine, XMMS, BMP, etc. etc. etc. if the Gstreamer won't cut your mustard.

I'd say... if multi-media and streaming media is really important to you, and you don't like fiddle around much, stick with Ubuntu 5.10 (Breezy), and use the Automatix or Easy Ubuntu scripts to install all the codecs you desire. At least until June, when 6.06 final is released, and those scripts are updated to work with the new version. 

If it's not so important, or you're happy to do manually what the Automatix scripts do for you, then you might as well install Dapper Beta. Just be aware that it *is* still Beta, and might have a few niggling bugs.

I currently use Dapper for both Python and Java programming, and I can play all my media (a few oggs, a few MP3s, and a lot of Anime) without problems. 

Cheers,

---

### Post by eeried on 2006-04-27
Hello justin2021,

Why are you leaving PCLinuxOS? I'd be insterested to know. Because of RPM perhaps?

I have used the CD-Live and I think it's an  impressive distro -- I'm no Mandriva fan  though (I like Debian-based distros much better, no offence meant)  but I think this distro looks great. Even Xmms has a smart PCLinuxOS-modified skin (I like Xmms because it's the only small app that's willing to play my CDs on Ubuntu).

cheers

---

