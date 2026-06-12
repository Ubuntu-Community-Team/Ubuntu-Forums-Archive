---
title: "Rhythmbox EQ suddenly not working"
date: 2012-07-22
forum: General Help
---

### Post by BoogeyOfTheMan on 2012-07-22
Yesterday I was listening to some songs, I skipped to the next song and it sounded like a really bad cassette recording off of AM radio. After checking some other songs and going back to the ones I was listening to before the problem started, all of them sounded like this.

Basically there is no low end. If I turn the higher frequencies all the way down, theres almost no sound whatsoever. There is sound, but its like having the volume set on 1.

Disabling the EQ makes the problem go away, but then I have no Rhythmbox specific EQ.

I have installed the pulseaudio system wide EQ, but its not an ideal solution as now videos in totem and audio books in clementine have too much bass.

I really like rhythmbox and would like to continue to use it for my music needs, but this issue is making that decision difficult. Any ideas?

EDIT* I used the ppa and instructions from this thread to get the Rhythmbox plugins working again, and they worked fine for a few days.
[http://ubuntuforums.org/showthread.php?t=1951237](http://ubuntuforums.org/showthread.php?t=1951237)

---

### Post by Frogs Hair on 2012-07-22
I am not familiar with that plug-in but have been using this system wide EQ since 9.10 . [http://www.ubuntuupdates.org/package/webupd8/precise/main/base/pulseaudio-equalizer](http://www.ubuntuupdates.org/package/webupd8/precise/main/base/pulseaudio-equalizer)

---

### Post by BoogeyOfTheMan on 2012-07-22
> **Frogs Hair said:**
> I am not familiar with that plug-in but have been using this system wide EQ since 9.10 . [http://www.ubuntuupdates.org/package/webupd8/precise/main/base/pulseaudio-equalizer](http://www.ubuntuupdates.org/package/webupd8/precise/main/base/pulseaudio-equalizer)

Yes, that is what I am using right now, but I prefer app specific EQ's,since, as I stated, I use different apps for different files and with a system wide EQ, my audio books and videos have entirely too much bass.

I started using a different audio player for audio books just so I didnt have to change EQ settings every time I switched from music to book.

---

### Post by Frogs Hair on 2012-07-22
It's a 3rd party plugin so you may want to post the problem at the PPA source . I found these plugins at Launchpad pad but I don't if they are the same as you are using.   [https://launchpad.net/~fossfreedom/+archive/rhythmbox-plugins](https://launchpad.net/~fossfreedom/+archive/rhythmbox-plugins)

---

### Post by BoogeyOfTheMan on 2012-07-23
> **Frogs Hair said:**
> It's a 3rd party plugin so you may want to post the problem at the PPA source . I found these plugins at Launchpad pad but I don't if they are the same as you are using.   [https://launchpad.net/~fossfreedom/+archive/rhythmbox-plugins](https://launchpad.net/~fossfreedom/+archive/rhythmbox-plugins)

Yes, those are the ones I'm using.

---

### Post by davidmohammed on 2012-07-25
Yep - that's my PPA - it contains the github code from the original author.

I'm trying to diagnose the issue and possibly fix it - it looks like strange characters in the track genre are being written to the gconf database.

Please can you reset the database via the plugin preferences and clicking the Reset All button -

you can also run this:

```
 gconftool-2 --recursive-unset /apps/rhythmbox/plugins/equalizer

```
I do my fixes in github - if anyone has the will to test - 

please can you test out my fix before I push it upstream:

[URL="https://github.com/fossfreedom/rhythmbox-plugins"]https://github.com/fossfreedom/rhythmbox-plugins
[/URL]

click the zip button on the link above.

Extract

copy the equalizer folder and its contents to ~/.local/share/rhythmbox/plugins

uninstall the existing PPA package

```
sudo apt-get purge rhythmbox-plugin-equalizer
```

---

### Post by BoogeyOfTheMan on 2012-07-25
Sorry I havent responded sooner. I have tried your fix and I'm not sure if it worked or my stuff just magically fixed itself. For some reason, anything more than +8dB in an EQ (including the pulseaudio system wide one) causes distortion on an ear splitting unmanageable level.

I'm also having other odd issues with the volume maxing out if I manually change tracks, or in Totem if I manually switch to the next video. So apparently something I did while trying to fix the original issue messed something up.

I'm basically having things randomly break in 12.04 that I never had happen before and am trying to figure out if its due to something I did or if Precise is just buggy as all hell. /rant

I really appreciate your quick response and diligent manner in trying to resolve the EQ issue.

---

