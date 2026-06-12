---
title: "Video playback crashes after update"
date: 2011-12-13
forum: General Help
---

### Post by Los Frijoles on 2011-12-13
I am running Ubuntu 11.10 (64-bit) on a Core i5-2500K with an ASRock Z68 Pro3-M motherboard using the integrated graphics. While playing flash video (such as hulu) seems to work in my browser, using Banshee or Totem to play video files causes some strange behavior: Audio will work, but I will see no video. The GUI for Totem seems to stick as though it had only loaded the name of the video into the side bar (no play position slider shown, just the line; the time elapsed/time total display stays at 0:00/0:00). After a few seconds, my display will act as though it was changing resolutions, popping off for a second or two and then popping back on. This happens a couple times, all the while the audio is still running. I am unable to interact with the GUI or the top task bar at all even though the mouse still moves. Alt-F4 does close the program, but unity seems to shut down, the top bar is no longer visible, and keyboard shortcuts such as Ctrl-Alt-Backspace and Ctrl-Alt-T don't work. Ctrl-Alt-F2 does bring me to a CLI, but I don't know where to go from there to figure out what went wrong. Looking at the syslog doesn't seem to show anything strange (but of course I could be looking in the wrong place for the wrong thing). So far the only way I have gotten the computer to recover after this is to restart it.

Video playback was working fine a few days ago and so the only thing I can think of is the recent slew of updates. Any thoughts or solution ideas?

Edit: I found this in the log file after trying to run a DVD and then letting the screen flicker for a while:
> Dec 13 17:26:36 kcuzner-desktop kernel: [ 1850.000829] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Dec 13 17:26:36 kcuzner-desktop kernel: [ 1850.000841] [drm] capturing error event; look for more information in /debug/dri/0/i915_error_state
Dec 13 17:26:36 kcuzner-desktop kernel: [ 1850.004795] [drm:i915_wait_request] *ERROR* i915_wait_request returns -11 (awaiting 293980 at 293979, next 293982)
Dec 13 17:26:43 kcuzner-desktop kernel: [ 1856.362656] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Dec 13 17:26:43 kcuzner-desktop kernel: [ 1856.362717] [drm:i915_wait_request] *ERROR* i915_wait_request returns -11 (awaiting 293984 at 293979, next 293985)
Dec 13 17:26:49 kcuzner-desktop kernel: [ 1862.716478] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Dec 13 17:26:49 kcuzner-desktop kernel: [ 1862.716505] [drm:i915_wait_request] *ERROR* i915_wait_request returns -11 (awaiting 294216 at 294212, next 294217)
Dec 13 17:26:56 kcuzner-desktop kernel: [ 1869.481916] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Dec 13 17:26:56 kcuzner-desktop kernel: [ 1869.481974] [drm:i915_wait_request] *ERROR* i915_wait_request returns -11 (awaiting 294337 at 294335, next 294339)
Dec 13 17:27:03 kcuzner-desktop kernel: [ 1877.150469] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Dec 13 17:27:03 kcuzner-desktop kernel: [ 1877.150526] [drm:i915_wait_request] *ERROR* i915_wait_request returns -11 (awaiting 294489 at 294473, next 294491)
Dec 13 17:27:10 kcuzner-desktop kernel: [ 1883.504295] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Dec 13 17:27:10 kcuzner-desktop kernel: [ 1883.504323] [drm:i915_wait_request] *ERROR* i915_wait_request returns -11 (awaiting 294658 at 294656, next 294659)
Dec 13 17:27:16 kcuzner-desktop kernel: [ 1889.878110] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Dec 13 17:27:16 kcuzner-desktop kernel: [ 1889.878170] [drm:i915_wait_request] *ERROR* i915_wait_request returns -11 (awaiting 294661 at 294656, next 294662)
Dec 13 17:27:24 kcuzner-desktop kernel: [ 1897.167027] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Dec 13 17:27:24 kcuzner-desktop kernel: [ 1897.167057] [drm:i915_wait_request] *ERROR* i915_wait_request returns -11 (awaiting 294974 at 294968, next 294976)
Dec 13 17:27:31 kcuzner-desktop kernel: [ 1904.419992] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Dec 13 17:27:31 kcuzner-desktop kernel: [ 1904.420058] [drm:i915_wait_request] *ERROR* i915_wait_request returns -11 (awaiting 295219 at 295214, next 295221)
Now how to fix that...

---

### Post by Sayed Ali on 2011-12-14
I have the same problem.

---

### Post by Los Frijoles on 2011-12-14
So, I looked at the last upgraded package and discovered that my updates on Monday the 12th updated xserver-xorg-video-intel. I am using the xorg edgers packages and I assume it was them who updated that one. Since opengl still works (I just played nexuiz to check...60fps) I assume it is just video acceleration that is broken. Anybody have any solutions? Is there a way to downgrade the package?

---

### Post by sulo22 on 2011-12-17
I've got the same problem. Whenever the hw-acceleraton is used to render video (not flash flv) or using 3d (not opengl) xserver crashes into recovery mode. dmesg then:
```

[drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
[drm] capturing error event; look for more information in /debug/dri/0/i915_error_state
[drm:i915_wait_request] *ERROR* i915_wait_request returns -11 (awaiting 311167 at 311163, next 311168)

```

it seems like to be this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/507504]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/507504")

please let me know, if u have found a workaround! thanks! :)

---

