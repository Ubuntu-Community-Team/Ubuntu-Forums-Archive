---
title: "no headphone sound xubuntu 11.04"
date: 2011-06-14
forum: General Help
---

### Post by goneskiing on 2011-06-14
sound works thru speakers but when headphone is plugged in, speakers go silent (like they should)  but there is no sound in the headphones (headphones work fine on my cell phone)

I added options snd-hda-intel  in the /etc/modprobe.d/alsa-base.conf file but no luck

any ideas

---

### Post by goneskiing on 2011-06-14
> **goneskiing said:**
> sound works thru speakers but when headphone is plugged in, speakers go silent (like they should)  but there is no sound in the headphones (headphones work fine on my cell phone)

I added options snd-hda-intel  in the /etc/modprobe.d/alsa-base.conf file but no luck

any ideas

[SOLVED]
I installed gnome-alsamixer  then checked to enable mic and checked 2nd speaker 

not really sure if this was the right way to solve it but headphones now get sound

---

### Post by djbacon on 2011-08-15
> I installed gnome-alsamixer then checked to enable mic and checked 2nd speaker 

not really sure if this was the right way to solve it but headphones now get soundUnfortunately it did't work for me.
I did update and then restarted and then there is this problem. When i plug in headphones, speakers go silent but headphones are also silent. I checked with other devices, headphones are ok. Anyone has any ideas how to fix it?

---

