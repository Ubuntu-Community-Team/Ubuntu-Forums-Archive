---
title: "sound only works with live cd"
date: 2006-03-06
forum: General Help
---

### Post by morguns on 2006-03-06
why is it sound works fine when i boot to the live cd, but it doesn't work when booting normally? would it be possible to somehow copy the cd drivers and apply them to the normal install? if so, how would i accomplish that? any help appreciated.

---

### Post by WelterPelter on 2006-03-06
Which sound card are you using?

---

### Post by nominal on 2006-03-06
> when booting normally

Normally means?

---

### Post by taurus on 2006-03-06
Did you check with alsamixer to make sure you have turned on the volumes?

```

sudo alsamixer
sudo alsactl store (to save the settings...)

```

---

### Post by morguns on 2006-03-06
[quote=taurus]Did you check with alsamixer to make sure you have turned on the volumes?[/quote]yes, errrr, i _thought_ i had. i did it again just to be sure and now the sound is working. i'm an id10t, must have missed one of the settings previously. thanks for the quick replies everyone! sound is working, woot!

---

