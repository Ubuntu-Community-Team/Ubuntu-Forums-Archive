---
title: "Have to reinstall 64 bit flash on every boot"
date: 2009-11-02
forum: General Help
---

### Post by Cuddles McKitten on 2009-11-02
I'm using Firefox in Koala 64 bit, and, for some reason, I have to re-copy libflashplayer.so every boot.  I wondered if the file was getting corrupted somehow, so I md5 summed it before and after booting.  The results were the file doesn't change at all.  After re-copying it to the plugins directory, again, the file's md5 didn't change but Firefox was willing to run flash all of a sudden.

Right now I just have a little script that runs when GNOME starts to fix it, but that's relatively inelegant and doesn't solve the underlying problem.  Anyone have any ideas?

---

### Post by mattlach on 2009-11-22
> **Cuddles McKitten said:**
> I'm using Firefox in Koala 64 bit, and, for some reason, I have to re-copy libflashplayer.so every boot.  I wondered if the file was getting corrupted somehow, so I md5 summed it before and after booting.  The results were the file doesn't change at all.  After re-copying it to the plugins directory, again, the file's md5 didn't change but Firefox was willing to run flash all of a sudden.

Right now I just have a little script that runs when GNOME starts to fix it, but that's relatively inelegant and doesn't solve the underlying problem.  Anyone have any ideas?


I have this same problem.   Have you reported it as a bug, or found a good solution?


As I understand the 64bit plugin is still in beta, so some issues are expected.   This is an odd one though.

---

### Post by NoaHall on 2009-11-22
Hm.. it sounds like Firefox is no longer linking to flash. Where are you copying it to?

---

### Post by mattlach on 2009-11-23
> **NoaHall said:**
> Hm.. it sounds like Firefox is no longer linking to flash. Where are you copying it to?

Hmm..


Im using the version of flash in the Karmic repository.  Is it still advisable to remove the repository versions and install manually, or was that only for Jaunty?

---

### Post by NoaHall on 2009-11-23
> **mattlach said:**
> Hmm..


Im using the version of flash in the Karmic repository.  Is it still advisable to remove the repository versions and install manually, or was that only for Jaunty?

Yes, indeed. The one in Karmic repos is still the 32 bit version, not the great and powerful 64 bit version :)

---

### Post by mattlach on 2009-11-25
> **NoaHall said:**
> Yes, indeed. The one in Karmic repos is still the 32 bit version, not the great and powerful 64 bit version :)

That is odd...


Home come it is working for me then?  (or at least working until I reboot?)

The 32 bit flash plugin shouldn't work with a 64 bit broswer...

---

### Post by mattlach on 2009-11-28
Hmm.

I went to the link in your sig to try to install it manually.   There was only one Linux plugin on the Flash 10.1 webpage linked, and it didnt specify 32bit or 64bit.

I tried installing it, but it didn't work.

I then went back to using the package in the karmic repository which usies ndiswrapper, and again, I am back to ahving to reinstall the damned plugin every time I reboot.

I can't understand why more people aren't having this problem?

---

### Post by dcstar on 2009-11-28
> **Cuddles McKitten said:**
> I'm using Firefox in Koala 64 bit, and, for some reason, I have to re-copy libflashplayer.so every boot.  I wondered if the file was getting corrupted somehow, so I md5 summed it before and after booting.  The results were the file doesn't change at all.  After re-copying it to the plugins directory, again, the file's md5 didn't change but Firefox was willing to run flash all of a sudden.

Right now I just have a little script that runs when GNOME starts to fix it, but that's relatively inelegant and doesn't solve the underlying problem.  Anyone have any ideas?

Firefox plugins can either exist in the system wide folders or in the user specific folders.

If the is a bad plugin in a user folder, I would say it will be used instead of the system wide alternative - so check/uninstal/delete any user plugins.

---

