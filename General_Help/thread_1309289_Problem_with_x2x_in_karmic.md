---
title: "Problem with x2x in karmic"
date: 2009-11-01
forum: General Help
---

### Post by cmol on 2009-11-01
Hi

I installed karmic yesterday, and a I've always used x2x between my machines running:

ssh -X *IP-ADDRESS* x2x -west -to :0

Now I get an error:

No protocol specified
x2x - error: can not open display :0

I found this site ([http://www.stormcrow.ca/?p=106](http://www.stormcrow.ca/?p=106)), saying i have to edit my /etc/gdm/gdm.conf, but that file do not exist (in karmic?).

Any ideas?

Thanks :)

---

### Post by cmol on 2009-11-02
Nothing?

---

### Post by msch on 2009-11-09
I believe you're on the right path with suspecting GDM.  However, I can't get it to work either.

/etc/gdm/gdm.schemas has the section where it sets DisallowTCP=true by default, but changing it there as well as adding:

[security]
DisallowTCP=false

to /etc/gdm/custom.conf 

doesn't seem to resolve the issue.  It looks like there are further permissions/restrictions that I'm missing.  I can confirm that x2x works just fine if you "startx" from a TTY and disable GDM, but this breaks a number of other things I don't feel like fixing (audio) and I would prefer to just have things working properly through GDM.

---

### Post by cmol on 2009-11-09
> **msch said:**
> I believe you're on the right path with suspecting GDM.  However, I can't get it to work either.

/etc/gdm/gdm.schemas has the section where it sets DisallowTCP=true by default, but changing it there as well as adding:

[security]
DisallowTCP=false

to /etc/gdm/custom.conf 

doesn't seem to resolve the issue.  It looks like there are further permissions/restrictions that I'm missing.  I can confirm that x2x works just fine if you "startx" from a TTY and disable GDM, but this breaks a number of other things I don't feel like fixing (audio) and I would prefer to just have things working properly through GDM.

Then it's not just me.

I haven't really gone as deep into it as you, but I made a launchpad bug about it:
[https://bugs.launchpad.net/ubuntu/+bug/471726](https://bugs.launchpad.net/ubuntu/+bug/471726)

Maybe you have something to add in there :)

---

### Post by msch on 2009-11-10
It's definitely a problem with gdm as opposed to x2x.  I gave up trying to fix gdm and switched to SLiM which also supports auto-login.  This ruins audio somehow, so I ended up completely removing pulseaudio and going back to esound/alsa.

---

### Post by cmol on 2009-11-11
> **msch said:**
> It's definitely a problem with gdm as opposed to x2x.  I gave up trying to fix gdm and switched to SLiM which also supports auto-login.  This ruins audio somehow, so I ended up completely removing pulseaudio and going back to esound/alsa.

Should the launchpad bug above be changed to regarding gdm rather than x2x? (and how should that be done?)

---

