---
title: "No sound in my new notebook!"
date: 2009-07-25
forum: General Help
---

### Post by Fixman on 2009-07-25
I recently bought the Compaq 610 laptop, and installed Ubuntu on it. Everything, including WiFi, ran smoothly, except for sound, that does not work.

The strange thing is that the system responds as if it worked, but no sound comes out. This also happened on the Live USB. I already tried looking for alsamixer (and all values were already on max volume) and nothing that I know is muted.

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

**EDIT:** Okay, heres the new situation. Due to some problem, I had to format the notebook. However, I can't make the sound to work this time, not even with the ALSA upgrade script. Does anyone have any new ideas?

**ANOTHER EDIT:** For some reason, after I completely removed ALSA drivers (using the awesone script), rebooted, installed them with the script and rebooted again it worked. Weird.

---

### Post by Fixman on 2009-07-25
No help yet? Please, I need it!

---

### Post by Vinger on 2009-07-26
Hello,

I have the same laptop, and the same problem...
Has anyone an idea how to solve it?

tx.

---

### Post by Fixman on 2009-07-26
I solved it!

All I had to do was to update ALSA to a new version. Since the new version isn't still on the Repos, I had to download it from the ALSA page, or use [this]("http://ubuntuforums.org/showthread.php?p=6589810") awesome script by soundcheck.

After that, I reboot my computer, put my speakers on maximum (since for some reason after the update they made it to minimum) and enjoy my music.

---

### Post by Vinger on 2009-07-27
ok, tx for the explanation!

I'll try it tonight...

Since you have the same laptop, can you please give a look at my other problem: 
[http://ubuntuforums.org/showthread.php?t=1214109](http://ubuntuforums.org/showthread.php?t=1214109)

allready thanks.

grz

---

### Post by langyaw on 2009-07-27
> **Fixman said:**
> I solved it!

All I had to do was to update ALSA to a new version. Since the new version isn't still on the Repos, I had to download it from the ALSA page, or use [this]("http://ubuntuforums.org/showthread.php?p=6589810") awesome script by soundcheck.

After that, I reboot my computer, put my speakers on maximum (since for some reason after the update they made it to minimum) and enjoy my music.

congratulations!
the ALSA page has many files for downloading. which did you download and install?:confused:

---

### Post by Fixman on 2009-07-27
> **langyaw said:**
> congratulations!
the ALSA page has many files for downloading. which did you download and install?:confused:

I didn't manually download any file from the ALSA page, I just used [the awesome ALSA-upgrade script]("http://ubuntuforums.org/attachment.php?attachmentid=113163&r td=1241945700") (that file, or the first attachment in the thread).

---

### Post by Vinger on 2009-07-28
ok, tx!

that did the trick! indeed...

grz.

---

### Post by langyaw on 2009-07-28
> **Fixman said:**
> I didn't manually download any file from the ALSA page, I just used [the awesome ALSA-upgrade script]("http://ubuntuforums.org/attachment.php?attachmentid=113163&r td=1241945700") (that file, or the first attachment in the thread).

Fixman, what script? the link above opens a page that takes forever to show anything.:confused:

---

### Post by Vinger on 2009-07-29
> **Fixman said:**
> I solved it!

All I had to do was to update ALSA to a new version. Since the new version isn't still on the Repos, I had to download it from the ALSA page, or use [this]("http://ubuntuforums.org/showthread.php?p=6589810") awesome script by soundcheck.

After that, I reboot my computer, put my speakers on maximum (since for some reason after the update they made it to minimum) and enjoy my music.

You have to go to the page with the ALSA script. There is a little manual and the download link of the script you mension.

grz.

---

### Post by tau88 on 2009-07-30
fixman, vinger, can you tell me if your microphone is working correctly?
also, when you plug a headphone set, does the sound go to the headphones?

---

### Post by Vinger on 2009-07-30
Hello,

When i plug in a headphone, the sound is there correctly. I don't have a microphone with me for the moment to test...

grz.

---

### Post by tau88 on 2009-07-30
the laptop has an internal microphone, just open the sound recorder and you should be able to test it

---

### Post by Vinger on 2009-08-08
Sorry for the late respons, but i was on vacation for a week...

I'm now searching a sound recorder for Kubuntu. (fe. Krecorder)
When i have installed it (it is not in the repo) then i let you know...

grz

---

### Post by Illender on 2009-08-10
hey gang, here's my malfunction.
I have a compaq evu n620c running the jaunty jackalope. 
Sound was working fine for abit then all of the sudden it no longer works.
I surfed a few threads. I've uninstalled then reinstalled the alsa packages, i've checked the audio group, I've tested it under other users and most recently ran the upgrade script, all to no avail.
I'm reluctant to reinstall ubuntu yet, but will try that as a last resort.

when I enter aplay -l it tells me:
> 
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


should there be two devices there? is there maybe a conflict here?
At the end of my rope here.

---

### Post by Vinger on 2009-08-11
Hello,

I've not yet found a sound recorder for kubuntu (see another topic). 

What about the question for Illender:
Maybe you can try the alsa online upgrade from following topic:
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

grz.

---

### Post by Illender on 2009-08-11
> **Vinger said:**
> 
Maybe you can try the alsa online upgrade from following topic:
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

grz.


[QUOTE=Illender]
and most recently ran the upgrade script, all to no avail.
[/QUOTE]

As you can see, i've tried that already.
but thanks for the attempted help.

---

