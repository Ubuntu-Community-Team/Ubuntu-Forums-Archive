---
title: "Latest Kernel update killed Toshiba sound."
date: 2011-01-27
forum: General Help
---

### Post by FunkeyMonk on 2011-01-27
The latest Kernel update (2.6.35-25-generic) killed all my sound output on my Toshiba Satellite M115.

I tried reinstalling all ALSA components and plugins.   No luck there.

Rebooting into 2.6.35-24-generic fixes the problem, in that my sound works again.

Any ideas?

---

### Post by gordintoronto on 2011-01-27
Did it kill both onboard speakers and earphones?

In Preferences/Sound, under the hardware tab, there is a drop-down menu called "profile." Have you experimented with different profiles?

---

### Post by FunkeyMonk on 2011-01-28
> **gordintoronto said:**
> Did it kill both onboard speakers and earphones?
Yup.  I usually use external speakers plugged into the headphone jack.  I tried with and without them plugged in, including rebooting each way.

> In Preferences/Sound, under the hardware tab, there is a drop-down menu called "profile." Have you experimented with different profiles?
Did that, too.

---

### Post by ttreadway81 on 2011-02-03
I have the same problem here.  Got a Toshiba Satellite m115-s1061.  Neither the speakers or headphones will work.

---

### Post by FunkeyMonk on 2011-02-03
> **ttreadway81 said:**
> I have the same problem here.  Got a Toshiba Satellite m115-s1061.  Neither the speakers or headphones will work.

I still haven't found any sort of fix, other than using the previous Kernel.   I'm just hoping it's fixed in the next.

---

### Post by ttreadway81 on 2011-02-04
Would there be a large drawback if I rolled back to the previous kernel?

---

### Post by FunkeyMonk on 2011-02-04
> **ttreadway81 said:**
> Would there be a large drawback if I rolled back to the previous kernel?

No.  I haven't noiced any difference between the two. (except that my sound works on the previous version)

---

### Post by ttreadway81 on 2011-02-08
That sounds like a plan until a fix comes out for this.  Now its off to do some research on how to roll back!

---

### Post by ttreadway81 on 2011-02-23
I took my problem to the bug team and they managed to get the sound running again.
They had me add a line to /etc/modprobe.d/alsa-base.conf
The first one they had me try: options snd-hda-intel model=auto That didn't work after a reboot.
So, they had me try: snd-hda-intel model=3stack
That one worked and now the sound is back.  Speakers and headphones.

---

### Post by FunkeyMonk on 2011-03-02
> **ttreadway81 said:**
> I took my problem to the bug team and they managed to get the sound running again.
They had me add a line to /etc/modprobe.d/alsa-base.conf
So, they had me try: snd-hda-intel model=3stack
That one worked and now the sound is back.  Speakers and headphones.

Where did you add the line?  At the end of the file?  Somewhere in the middle?

FWIW, the Kernel was just updated again today, and my sound isn't working with this one either.

---

### Post by jeremyjjbrown on 2011-03-02
If you don't need any functions of the new kernel it's easier to just report the bug and boot to the one that worked. It will get fixed soon enough.

---

### Post by FunkeyMonk on 2011-03-02
> **jeremyjjbrown said:**
> If you don't need any functions of the new kernel it's easier to just report the bug and boot to the one that worked. It will get fixed soon enough.

Sorry to be a total n00b, but I've been using Ubuntu for three years now and I still can't figure out how/where to report a bug.   Help?

---

### Post by jeremyjjbrown on 2011-03-02
[http://www.ubuntu.com/community/report-problem](http://www.ubuntu.com/community/report-problem)

---

### Post by jeremyjjbrown on 2011-03-02
BTW You can select the previous kernel in your grub menu at startup.

---

### Post by ttreadway81 on 2011-04-06
add 
options snd-hda-intel model=3stack
to the end of /etc/modprobe.d/alsa-base.conf
sorry for the delay in reply

---

### Post by FunkeyMonk on 2011-04-06
> **ttreadway81 said:**
> add 
options snd-hda-intel model=3stack
to the end of /etc/modprobe.d/alsa-base.conf
sorry for the delay in reply

That fix works for me.

Also, I installed the Beta 1 of Narwhal yesterday.   It's got the same problem on my Toshiba, and this fix works there, too.

---

