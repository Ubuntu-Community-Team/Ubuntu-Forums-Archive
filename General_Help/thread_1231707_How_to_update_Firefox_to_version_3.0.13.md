---
title: "How to update Firefox to version 3.0.13 ?"
date: 2009-08-04
forum: General Help
---

### Post by styxcoverbnd on 2009-08-04
I saw on CNET ([link](http://news.cnet.com/8301-1009_3-10302299-83.html)) that Mozilla released new versions of Firefox to patch critical securities holes. I'm running Firefox version 3.0.12 and wondering how to update to the latest version. I ran Update manager and there were no updates for Firefox, is there a way to auto-update or force an update to the latest version?

Sorry if this question has been asked already, I ran a search for this and got no results

---

### Post by wojox on 2009-08-04
If it's not in the updates you could try the Mozilla sight. You could also download 3.5 from Synaptic.

---

### Post by dpeters11 on 2009-08-04
3.5 hasn't been updated either. I'm only seeing 3.5.1 and the same vulnerability fixed in 3.0.13 is fixed in 3.5.2.

---

### Post by jmszr on 2009-08-04
styxcvrbnd,

Firefox updates usually show up (in the Update Manager)a day or two after Firefox releases them. The developers need time to go over them.

---

### Post by styxcoverbnd on 2009-08-04
I think Firefox 3.5 was vulnerable to this to and an update for that was also issued. I saw on Mozilla's site that I can run Firefox as root to possible try to update. Is that a good idea (don't really want to run anything as root)?

Is this something I should even be worried about if I don't go to any sketchy sites, not that I do?

Edit: Just saw the two above posts after I posted, thanks for the info guys. I'll wait a few days to see what happens

---

### Post by Katalog on 2009-08-04
> **styxcoverbnd said:**
> I think Firefox 3.5 was vulnerable to this to and an update for that was also issued. I saw on Mozilla's site that I can run Firefox as root to possible try to update. Is that a good idea (don't really want to run anything as root)?

Nope (at least not IMO), I'd just wait a day or two for the update.

> **styxcoverbnd said:**
> Is this something I should even be worried about if I don't go to any sketchy sites, not that I do?

I don't think so, but that's just me (I don't really go anywhere shady either).

---

### Post by styxcoverbnd on 2009-08-04
> **Katalog said:**
> Nope (at least not IMO), I'd just wait a day or two for the update.

I figured as much. I work support in a Windows environment so when I say that post I thought, just like 'runas' which I use daily. Then I thought that doing that might get me in trouble so I figured I'd ask and see what others thought

> **Katalog said:**
> I don't think so, but that's just me (I don't really go anywhere shady either).

Good to know, if I have anything important to do besides check email, I'll wait until the update is released.

---

### Post by egalvan on 2009-08-04
Firefox 3.0.x running on:

XP

Jaunty

Hardy

all updated to 3.0.[COLOR="Red"]13[/COLOR] in the since 2200 Central Daylight USA.

---

### Post by aysiu on 2009-08-04
If you use the Ubuntu repositories version of Firefox, you will get security updates. They just won't appear immediately. Just be patient. Update manager will let you know when the updates are ready. Sometimes they come within a day of Mozilla's updates to Firefox. Sometimes they take a couple of weeks.

Running Firefox as root if you are using the repositories version will **not** allow you to update to a newer version. You get a new version when a new version arrives in the repositories.

If you are really impatient, just use the Firefox from the Mozilla website:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Then you can launch it as root to get updates (but always use ```
gksudo firefox
``` and **never** use *sudo firefox*).

---

### Post by Katalog on 2009-08-05
> **aysiu said:**
> If you use the Ubuntu repositories version of Firefox, you will get security updates. They just won't appear immediately. Just be patient. Update manager will let you know when the updates are ready. Sometimes they come within a day of Mozilla's updates to Firefox. Sometimes they take a couple of weeks.

And what do you know, they showed up this morning. That was pretty quick.

---

