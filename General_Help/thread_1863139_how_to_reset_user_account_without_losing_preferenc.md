---
title: "how to reset user account without losing preferences"
date: 2011-10-17
forum: General Help
---

### Post by roberto.tomas on 2011-10-17
I'm noticing a lot of different bugs and I think I should reset my user account. This is after upgrading to 11.10 but, at first, it was working just fine after the upgrade. Today however, I notice all of these issues:

[edit] resolved issues:

[COLOR=SeaGreen]function keys[/COLOR] do not work for: default keyboard shortcuts, changing consoles, alsamixer

[COLOR=SeaGreen]compiz opacify[/COLOR]: seems to toggle on and off or only rarely work

[COLOR=SeaGreen]compiz desktop cube[/COLOR]: stopped triggering first on left side, and after the last reboot, on right side.

unresolved issues:

[COLOR=Red] sound not working[/COLOR]. so after deleting /tmp files and rebooting, sound was working but microphone  compressed the audio (ie, I record it or chat with someone and the sound plays back as high pitched like an old tape player with the play and fast forward buttons both pressed at once). toggling on and off the microphone from the sound preferences hardware page seems to resolve the issue, but I have to do it after each boot. There is an order to this process: (on) no sound, (off), (on) sound but fast, (off), (on) sound correct from mic. -- obviously no sound when the mic is off

[COLOR=Red]epiphany[/COLOR]: google docs file uploads stopped working .. I'm not 100% positive this ever worked, but I thought that it did.

.. an amazing list of things really. I dont want to lose my preferences, .. how can I delete all caches and stuff, but not the preferences?

---

### Post by roberto.tomas on 2011-10-17
I followed advice for a different problem, to delete compiz cache and got compiz to work again. :)

solution:
>  rm -rf .cache/compizconfig-1/* .compiz-1/* .config/compiz-1/*this also seems to have fixed the function keys :)

---

### Post by roberto.tomas on 2011-10-17
here's a sample of the microphone problem, .. my audio output sounds like this when I record it in audacity .. and my chat friends tell me the effect is basically the same there.

[http://kiwi6.com/file/b989eoklw8](http://kiwi6.com/file/b989eoklw8)

---

