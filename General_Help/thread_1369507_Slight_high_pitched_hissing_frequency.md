---
title: "Slight high pitched hissing frequency"
date: 2010-01-01
forum: General Help
---

### Post by Scott O'Nanski on 2010-01-01
I have the slight, high-pitched hissing frequency when ever I play back audio.

I know other people have experienced this as well, but the threads were in a development section of the forum and are no longer open.

Has anyone has the same issue yet found a solution?

Thanks.

---

### Post by smerral on 2010-01-01
This could be the same problem I had. If so it's caused by feedback due to the power save option. You need to edit it out.

sudo gedit /etc/modprobe.d/alsa-base.conf

Scroll down to the bottom and comment out power save so it looks like this:

# options snd-hda-intel power_save=10 power_save_controller=N

Reboot.

Hope this helps.

Happy New Year!

---

### Post by Scott O'Nanski on 2010-01-01
Yep. Did that, which fixed the popping sound but not the strange frequency hissing sound.

In Jaunty, my audio worked flawlessly so I'm assuming it has something to do with whatever changes they made with Pulse Audio.

---

### Post by Scott O'Nanski on 2010-01-04
It's a bug in Pulse Audio (or whatever I'm using - I have no idea there enough listed / installed to be too confusing)

When I select 5.1 + Analogue out from the hardware subsection of the Sound Preferences the hissing starts.

It worked fine in Jaunty why did they break it?

---

### Post by Scott O'Nanski on 2010-01-04
Well, it's obviously the POS audio software they have installed as default.

I just realized sound is only coming out of two speakers. The center and rear left channel.

Any ideas how to fix this?

---

### Post by twent4 on 2010-01-08
Got the exact same issue as Scott (didn't bother tracking it down to the specific speakers though). Hiss goes away when switching to stereo mode.

Odd thing: hiss persists even when using headphones out of the front Audigy 2 panel and having 5.1 selected... i could've sworn that plug should always be stereo regardless of main config. Can i blame pulse?

---

