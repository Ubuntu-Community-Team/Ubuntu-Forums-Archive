---
title: "Copying DVD's?"
date: 2010-06-01
forum: General Help
---

### Post by Lyerae on 2010-06-01
[FONT=Arial]Well, I just got a brand-new 500GB portable drive the other day, and I figured it might be a good idea to back a backup of all my movies, in case the discs ever got damaged, but I can't figure out how.

I've tried Googling it, but everything I got was for old resources that didn't help much (I found some going back to 2006).

Thanks for any help.[/FONT]

---

### Post by dino99 on 2010-06-01
better than google, search "backup" into synaptic and make your choice :P

---

### Post by Lyerae on 2010-06-01
Alright, cool. Thanks.

Now I just seem to have a problem actually getting the movie to play...

---

### Post by sidzen on 2010-06-01
KDE has the best means (simple, straightforward) of accomplishing what you ask.  You may need to enable repositories first (check [https://help.ubuntu.com](https://help.ubuntu.com)), but I accomplished what was necessary in*** lubuntu*** by first going to* Synaptic* and checking the "Remove" box for Brasero and applying this in the said GUI.

Exit Synaptic

Then, in Terminal, I entered the following commands:
[PHP]sudo apt-get update[/PHP]Let it do its thing, then
[PHP]sudo apt-get build-dep k3b && sudo apt-get build-dep k9[/PHP]Let all downloads be accomplished, then (of course) enter
[PHP]sudo apt-get -f install k3b && sudo apt-get -f install k9[/PHP]K9 is what you're after, but my experience has been it is better to use it in conjunction with k3b.  It is more desirable to get rid of Brasero before loading k3b -- hence, the first order is to remove Brasero.

After successfully installing k3b and k9, it may be a good idea to get rid of unneeded files downloaded to satisfy dependencies.  Do this with the command
[PHP]sudo apt-get autoremove[/PHP]This worked for me.  I hope it does for you.
Best wishes!

---

### Post by Smart Viking on 2010-06-01
> **Lyerae said:**
> Alright, cool. Thanks.

Now I just seem to have a problem actually getting the movie to play...

Hey, you need to do this to play/copy DVDs: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Hope that helps. :)

---

