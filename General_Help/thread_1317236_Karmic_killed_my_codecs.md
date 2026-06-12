---
title: "Karmic killed my codecs"
date: 2009-11-06
forum: General Help
---

### Post by scathmandra on 2009-11-06
I've upgraded to Karmic and suddenly I can't play .avi files anymore, or stream .asx files from websites. VLC suggests that it's something I can't fix, but I beg to differ. Are there any other people with this problem? Any solutions out there?

---

### Post by coffeecat on 2009-11-06
Do you mean you upgraded from a Jaunty installation, or did you do a fresh Karmic installation to replace a Jaunty one? If you upgraded a Jaunty installation, this is probably because a dist-upgrade disables all your third-party repositories.

Your problem sounds like a Medibuntu one. Re-enable Medibuntu and update. I'd put my money on w32codecs/w64codecs for some of your problems.

---

### Post by scathmandra on 2009-11-06
> **coffeecat said:**
> Do you mean you upgraded from a Jaunty installation, or did you do a fresh Karmic installation to replace a Jaunty one? If you upgraded a Jaunty installation, this is probably because a dist-upgrade disables all your third-party repositories.

Your problem sounds like a Medibuntu one. Re-enable Medibuntu and update. I'd put my money on w32codecs/w64codecs for some of your problems.

Upgraded from existing Jaunty. Also, I am not sure how to re-enable Medibuntu... is there an easy way to do it?

Thanks.

---

### Post by codedmin on 2009-11-06
> **scathmandra said:**
> Upgraded from existing Jaunty. Also, I am not sure how to re-enable Medibuntu... is there an easy way to do it?

Thanks.

I have done that but no juice...

---

### Post by Joe Ker1086 on 2009-11-06
> **scathmandra said:**
> Upgraded from existing Jaunty. Also, I am not sure how to re-enable Medibuntu... is there an easy way to do it?

Thanks.

Might be a little presumptuous of me but have you tried uninstalling and reinstalling VLC? I have had a couple other codec problems with VLC and a fresh install of it seems to have fixed most of them. Just a thought.

---

### Post by coffeecat on 2009-11-06
> **scathmandra said:**
> Upgraded from existing Jaunty. Also, I am not sure how to re-enable Medibuntu... is there an easy way to do it?

Thanks.

No problem. Go to [http://www.medibuntu.org/](http://www.medibuntu.org/) . There's a link there - "Repository Howto". That'll get you set up. The terminal commands include a 'sudo apt-get update'. Once you've done that, hopefully the medibuntu updates will come through. Post back if that doesn't fix everything.

---

### Post by scathmandra on 2009-11-06
No dice. I reinstalled both VLC and Medibuntu, and no particular result happened.

---

### Post by andrew.46 on 2009-11-07
Hi scathmandra,

> **scathmandra said:**
> No dice. I reinstalled both VLC and Medibuntu, and no particular result happened.

Unless things have changed in the last little while the repository vlc has not been built with a vital compile-time option that enables it to use the external windows codecs packaged by Medibuntu as the w32codecs and w64codecs. The option is *--enable-loader* and I am not entirely clear why it is not used, perhaps mc4man who first pointed this out to me might have more of an idea?

Can I ask for some specifics for the files and streams that will not play? It would be interesting to see these to find out exactly why they are causing you some grief...

Andrew

---

### Post by wilee-nilee on 2009-11-07
AVI files can be a mix of several types of formats, so this can be a problem. So is it that AVI stuff that worked on jaunty you know the same files now don't work?

---

### Post by scathmandra on 2009-11-07
The files played in Jaunty--they're a bunch of Doctor Who .avi s.  

I tried to use --enable-loader, but didn't get any kind of result... not to mention that Totem doesn't work either,  so I think it's system-wide rather than player-related.

---

### Post by igorgomes on 2009-11-07
Its some incompatibility with personal PPAs. Here, I got one offering a bugged libavutil49, not found by VLC.

Try to start VLC in debug mode vlc -vv and see if there's a similar error. If so, disable the bugged PPAs (here was one with new Nvidia drivers), remove the files and install again.

Best,

Igor Gomes

---

### Post by scathmandra on 2009-11-07
There is indeed a similar error in debug mode. But how do I disable those PPAs? I don't know which ones they are...

Again, excuse my inexperience.

---

### Post by andrew.46 on 2009-11-07
Hi scathmandra,

> **scathmandra said:**
> I tried to use --enable-loader, but didn't get any kind of result... 

Sorry, I was less than clear. That option is a *compile time *option not a *run time* option. That is to say it will not work as *vlc --enable-loader myfile.avi*.

Andrew

---

### Post by scathmandra on 2009-11-07
I get the following:

```
bernard@Nicodemus:~/Videos/Films/Doctor Who 2005 - Season 1$ vlc -vv  --enable-loader bob.avi
VLC media player 1.0.2 Goldeneye
[0x1b61888] main libvlc debug: VLC media player - version 1.0.2 Goldeneye - (c) 1996-2009 the VideoLAN team
[0x1b61888] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--disable-maintainer-mode' '--enable-release' '--prefix=/usr' '--config-cache' '--enable-fast-install' '--with-binary-version=1ubuntu2' '--disable-update-check' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=xulrunner-plugin' '--enable-dvb' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--enable-flac' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-mod' '--enable-theora' '--enable-dvdnav' '--enable-gnutls' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-x264' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-dca' '--enable-realrtsp' '--disable-dv' '--disable-fluidsynth' '--disable-kate' '--disable-mtp' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[0x1b61888] main libvlc debug: translation test: code is "C"
[0x1b61888] main libvlc debug: checking plugin modules
[0x1b61888] main libvlc debug: loading plugins cache file /home/bernard/.cache/vlc/plugins-04081e.dat
[0x1b61888] main libvlc debug: recursively browsing `/usr/lib/vlc'
[0x1b61888] main libvlc warning: cannot load module `/usr/lib/vlc/codec/libx264_plugin.so' (libx264.so.67: cannot open shared object file: No such file or directory)
[0x1b61888] main libvlc warning: cannot load module `/usr/lib/vlc/codec/libavcodec_plugin.so' (libx264.so.67: cannot open shared object file: No such file or directory)
[0x1b61888] main libvlc warning: cannot load module `/usr/lib/vlc/demux/libavformat_plugin.so' (libx264.so.67: cannot open shared object file: No such file or directory)
[0x1b61888] main libvlc debug: module bank initialized (376 modules)
[0x1b61888] main libvlc debug: opening config file (/home/bernard/.config/vlc/vlcrc)
vlc: unknown option or missing mandatory argument `--enable-loader'
Try `vlc --help' for more information.
[0x1b61888] main libvlc debug: opening config file (/home/bernard/.config/vlc/vlcrc)
[0x1b61888] main libvlc debug: writing plugins cache /home/bernard/.cache/vlc/plugins-04081e.dat
VLC initialization failed

```

Not too sure what that means...

---

### Post by dannyboy79 on 2009-11-07
it's looking for the codec modules libx264_plugin.so, libavcodec_plugin.so, and libavformat_plugin.so but they aren't where they are suppose to be. Have you installed the ubuntu-restricted package or whatever it's called for playing commercial dvd's and what not? or follow here: [http://shibuvarkala.blogspot.com/2009/10/how-to-make-ubnutu-910-karmic-koala.html](http://shibuvarkala.blogspot.com/2009/10/how-to-make-ubnutu-910-karmic-koala.html)

---

### Post by scathmandra on 2009-11-07
I went to that page and followed all instructions, updated, and rebooted; still no dice. Any other ideas?

(Thanks a lot for this, guys; your support is heartening.)

---

### Post by DiogoFC on 2009-11-08
Same problem here.

---

### Post by scathmandra on 2009-11-08
I had a thought--could it be a libs problem? Or a blacklist? I remember not changing my blacklist during the upgrade(now <i>that</i> might have been the problem...). Would that give anyone any leads?

---

### Post by crysys on 2009-11-09
I'm in the same boat here, a dist-upgrade killed VLC, Movie player and Miro's ability to play nearly all videos I have.  I have tried the VLC release in the regular repos and in a couple of PPAs, I have Mediabuntu and w32codecs.

At least getting 5.1 surround to work was a little easier this time. :mad:

EDIT  I got it working!

sudo apt-get install libavcodec52

[Well, this guy solved it, I just followed directions.]("http://ubuntuforums.org/showpost.php?p=8212552&postcount=8")

This fixed VLC and Movie Player and Miro playback.  I am a happy camper.

---

### Post by JBAlaska on 2009-11-09
```
sudo aptitude install ubuntu-restricted-extras
```

---

### Post by scathmandra on 2009-11-09
Glorious! Thanks, guys.

---

### Post by n.hinton on 2009-11-09
Not on My system libavcodec52 will not co-exist with installed apps.
See attached.

---

### Post by coffeecat on 2009-11-09
If you look at what Synaptic wants to remove, it includes libavcodec-extra-52. That and libavcodec52 do the same job - have a look in Synaptic for what is different. libavcodec-extra-52 was probably installed as a dependency of ubuntu-restricted-extras. If you've got libavcodec-extra-52, you don't need libavcodec52, so you don't need to do anything.

---

### Post by n.hinton on 2009-11-10
I had exactly the same problem as post 1 in thread, this issue was further complicated my my adding a ppa best not added unless you know what you are doing, and running update manager.

Had some fantastic help from mc4man, that finally resolved the issue for me. probably best to see the whole thread.

[http://ubuntuforums.org/showthread.php?t=1313234](http://ubuntuforums.org/showthread.php?t=1313234)

---

