---
title: "Weird ALSA errors every time I start gedit"
date: 2006-04-08
forum: General Help
---

### Post by OfficeLinebacker on 2006-04-08
I get these errors whenever I invoke gedit at the command line:

ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2099:(snd_pcm_open_noupdate) Unknown PCM default


Functionality it not affected AFAICT

---

### Post by OfficeLinebacker on 2006-04-09
This wouldn't affect firestarter would it?

---

### Post by nanotube on 2006-04-09
i dont think it would have anything to do with firestarter...

---

### Post by OfficeLinebacker on 2006-04-09
Just wondering, I am not having much luck with firestarter either.

---

### Post by OfficeLinebacker on 2006-04-25
hey guys, I am still having this problem every time I invoke gedit.  doesn't seem to affect functionality, but annoying nonetheless.

Anyone. Bueller?

TIA,

T.

---

