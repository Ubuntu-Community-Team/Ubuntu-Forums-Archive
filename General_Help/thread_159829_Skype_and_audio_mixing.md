---
title: "Skype and audio mixing"
date: 2006-04-13
forum: General Help
---

### Post by pdobrev on 2006-04-13
Hello people!
During the past few days I've been reading various articles on this particular topic, alas, I didn't find a solution that satisfies me. I tried aoss, esd and arts but none of them worked normally.
With aoss skype runs ok, I can talk and people can hear me, but then suddenly the sound would stop and some weird "read error"-s are displayed in the console.
With esddsp just when the skype window is about to pop up, I get a "bus error".
With artsdsp skype loads OK, but when I try to call anyone (or just any sound has to be produced), it crashes and I get 
```
*** glibc detected *** free(): invalid pointer: 0x08cccbd8 ***
Aborted 
```

The only was I can use skype is just running it directly (i.e. with OSS) but then it blocks the soundcard and that isn't something I want.

Any ideas?

Thanks.

---

### Post by wvelez on 2006-04-13
Hi,

Check out this link:  

[http://www.ubuntuforums.org/showthread.php?t=121756&highlight=skype+work](http://www.ubuntuforums.org/showthread.php?t=121756&highlight=skype+work)

It fixed the Skype issue for me and for a number of my friends.

Best regards and good luck,
-will

---

### Post by pdobrev on 2006-04-13
Hi!
Thanks for your reply, but I kinda already tried that. It basically says that I should use skype_dsp_hijacker but it still uses OSS and hence blocks my soundcard.
I believe skype should be piped through a sound daemon that uses alsa as output in order audio mixing to be available.

---

### Post by shuttleworthwannabe on 2006-04-13
[QUOTE=wvelez]Hi,

Check out this link:  

[http://www.ubuntuforums.org/showthread.php?t=121756&highlight=skype+work](http://www.ubuntuforums.org/showthread.php?t=121756&highlight=skype+work)

It fixed the Skype issue for me and for a number of my friends.

Best regards and good luck,
-will[/QUOTE]

hey, this was what I was looking for. It worked here for me. Thanks

---

### Post by pdobrev on 2006-04-13
It worked with sound mixing? You can talk on skype and hear sound from other applications?

---

