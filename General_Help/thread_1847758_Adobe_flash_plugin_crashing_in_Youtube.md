---
title: "Adobe flash plugin crashing in Youtube"
date: 2011-09-21
forum: General Help
---

### Post by t0p on 2011-09-21
Over the past couple of weeks, I have had Youtube videos play okay for a while, then suddenly I get a sad little lego block telling me that the Adobe flash plugin has crashed.  This doesn't happen all the time or anything - but it seems to occur sometimes when I'm watching a longer than usual video (though it has happened with shorter files too).  And until recently, I don't think I'd *ever* seen this.

I seem to recall Update Manager downloading an update to the Adobe flash installer or plugin a few weeks ago.  Is that the reason for this behaviour?  The sad little lego block gives me the option to  report the crash, which I have done every time this has happened, but no fix has appeared.  Anyone know what's going on, and if there's a way to solve this?  I'm running Firefox on Ubuntu 10.04, and I try to keep up-to-date with updates.

Cheers.

---

### Post by Frogs Hair on 2011-09-21
You could try Flash Aid if using Firefox . I makes installing flash easy and you can also test the beta versions to see if they preform better.

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by pqwoerituytrueiwoq on 2011-09-21
are you using the correct version for your system (64bit flash for 64bit ubuntu)? (google flash aid)
you can play it in html5 [http://www.youtube.com/html5](http://www.youtube.com/html5)

pause the flash video and run this command it will open the video in the movie player
```
d="`date`";ln -s `f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"` /tmp/"movie-$d";totem /tmp/"movie-$d"
```

---

### Post by t0p on 2011-09-22
Thanks for feedback, respondents.  I haven't tried any of the offered solutions, though I undoubtedly shall if/when the bad behaviour reappears.

This morning, Update Manager downloaded a new flashplugin-installer (and installed an updated flashplugin) so maybe the problem has been solved... I'll see later, when I try and watch something on Youtube (I've been watching/listening to the Mark Steel lectures - very funny *and* interesting.  I strongly recommend them to you all - just search on Youtube for "Mark Steel").

---

### Post by galacticaboy on 2011-09-22
From what I understand, this is a flash problem. I have the same problem to on Ubuntu 11.04 and so does my fiance, on Windows 7. We are both getting tired of it!

---

### Post by brntoki on 2011-11-02
Me too. Any developments on this??? Very annoying. I use FlashAid which usually solves any problems, but it just isn't working this time.

---

### Post by Frogs Hair on 2011-11-02
What version of Firefox ? While using Firefox Nightly Alpha 10 and Opera 11.52 as my only browsers and have not experienced this . I'm surprised I don't see any problems with the nightly build . I also use flash aid but have install the add-on compatibility reporter first .

---

### Post by lovinglinux on 2011-11-11
Disable HWVideo Decode in Flash-Aid tweaking preferences and install flash again.

---

### Post by subehsharma on 2011-11-11
I gave up "correcting" flash problems and installed MiniTube which is a kind of youtube front end NOT using flash but HTML5 so its smooth.

---

