---
title: "downgrading firefox from 5 to 4?"
date: 2011-06-28
forum: General Help
---

### Post by bcrowell on 2011-06-28
I did an apt-get upgrade half an hour ago, resulting in an upgrade from firefox 4 to 5, and in that time I've already run into multiple serious problems with the new version. Is there any way to downgrade?

---

### Post by ianc1 on 2011-06-28
If the last version was in the repository you could do:

```
apt-get purge firefox
apt-getinstall firefox=4.0.1
```Assuming the last version number was 4.0.1

I just did a quick search

```
apt-cache search firefox
``` and I can't see version 4 but I may have missed it.  Failing that I'm sure some one will tell you how to get it from the repo.

---

### Post by ajgreeny on 2011-06-28
What problems are you getting?  My only difficulty was googlebar-lite not being run when I restarted FF and I was told it was not available for FF5.  However a quick search on the FF Add-ons site found a patch which allows it to run very well.

I suspect there are patches for other add-ons as well as that one, so if this is your problem, try that way around it.

---

### Post by bcrowell on 2011-06-28
> **ianc1 said:**
> I can't see version 4 but I may have missed it.  Failing that I'm sure some one will tell you how to get it from the repo.

Thanks for the suggestions! What worked for me was this:
```

apt-get purge firefox
apt-get install firefox=4.*

```

> **ajgreeny said:**
> What problems are you getting?  My only difficulty was googlebar-lite not being run when I restarted FF and I was told it was not available for FF5.  However a quick search on the FF Add-ons site found a patch which allows it to run very well.

I suspect there are patches for other add-ons as well as that one, so if this is your problem, try that way around it.

My problems weren't related to add-ons. I've had serious rendering glitches when I switch desktops (I use fluxbox) and widgets in web pages that don't work properly.

---

### Post by lovinglinux on 2011-06-28
Keep in mind Firefox 4 will no longer be patched with security and stability updates, since version 5 is that patch in the new development model of Firefox. So, it would be better if you could find and fix the culprit, instead of downgrading.

Perhaps you could try Firefox 6 or 7. See [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247").

---

### Post by ianc1 on 2011-06-29
That's a good point about the security updates and I apologize for not thinking of that at the time of my earlier post.

Sorry.

---

### Post by bcrowell on 2011-06-30
Having a browser with security patches would be nice, but a secure browser that's too broken to use isn't going to do it for me :-) Firefox seems to be heading down the toilet right now. Too bad there don't seem to be other viable choices.

---

### Post by d3v1150m471c on 2011-06-30
Google has been offering large sums of money to anyone who can exploit their chrome browser for some time. Last I checked, no one has been successful. I've used it, it's fast. The only reason I don't make the switch is because my firefox 5 has all my hawt addons. Thus, you might want to give it a try. I'm on Ubuntu 10.04 LTS btw, and my browser runs perfectly.

---

### Post by lovinglinux on 2011-06-30
> **bcrowell said:**
> Having a browser with security patches would be nice, but a secure browser that's too broken to use isn't going to do it for me :-) Firefox seems to be heading down the toilet right now. Too bad there don't seem to be other viable choices.

If you could point out what is broken we could try to fix it.

For me, Firefox is not going down the toilet. Quite the opposite. It is improving on every new release.

---

### Post by mars29200 on 2011-07-18
Solution was given hier : 
[http://ubuntuforums.org/showthread.php?t=1799778&highlight=downgrade+firefox](http://ubuntuforums.org/showthread.php?t=1799778&highlight=downgrade+firefox)

---

