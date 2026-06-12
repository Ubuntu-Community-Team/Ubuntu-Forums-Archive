---
title: "set volume from terminal"
date: 2011-06-05
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-06-05
i want to set the volume to 8% on login
i have tried a few thing like
[FONT=Courier New]amixer -c 0 set PCM  8%
amixer set PCM 8% unmute[/FONT]
but it goes to 1%

---

### Post by stinkeye on 2011-06-05
On Natty, for me, this command sets the volume to full.(ie above 100% as in screenshot)
```
pacmd set-sink-volume 1 [COLOR="Magenta"]100000[/COLOR]
```

[COLOR="#ff00ff"]66666[/COLOR] sets at the 100% mark.

No idea why it's labelled 100% when you can increase the volume above that.


Try
```
pacmd set-sink-volume 1 15000
```
I can barely hear it below that.Depends on your speakers I suppose.

---

### Post by pqwoerituytrueiwoq on 2011-06-05
that was loud *pacmd set-sink-volume 0 5000* is what i want ty

---

### Post by BlueDon on 2011-06-05
> **pqwoerituytrueiwoq said:**
> that was loud *pacmd set-sink-volume 0 5000* is what i want ty

off topic (sorry) but your avatar is ace. I'd love that on a t shirt

---

### Post by pqwoerituytrueiwoq on 2011-06-05
> **BlueDon said:**
> off topic (sorry) but your avatar is ace. I'd love that on a t shirt
i would post the full size but i cant seem to find it
here are the 2 images i used to make it if you would like to remake it not so blurred and get a custom t shirt made

---

