---
title: "Setting gamma on boot - how?"
date: 2011-01-06
forum: General Help
---

### Post by system11 on 2011-01-06
Since xorg.conf no longer exists in 10.04, I can't set the display device gamma settings on boot.  This needs to be a system wide setting instead of a user login startup hack.  Is there a way to tell xorg what gamma to use anymore?  Some way to force or override the defaults would be nice.

"Progress" :/  I can only assume the xorg people who decided automatic is best, don't use Thinkpad laptops, which are all incredibly bright and washed out on defaults.

---

### Post by tredegar on 2011-01-06
You can generate an **xorg.conf**, and it will be used.
See [here]("http://www.linuxquestions.org/questions/ubuntu-63/need-optical-mouse-with-side-buttons-that-works-out-of-the-box-with-lucid-814150/#post4010372")

---

### Post by system11 on 2011-01-07
I know about that one, we'd rather not use a hard set xorg.conf.  Looking at the Xorg binary arguments, it seems like you can pass gamma values on the command line.  Could anyone tell me which script actually starts Xorg please?

Alternatively, is this something that can be done through xorg.d scripts?

---

### Post by tredegar on 2011-01-07
> I know about that one, we'd rather not use a hard set xorg.conf.
Then just run **xgamma** at startup:
**xgamma -gamma 0.5**

**startx** starts X

---

### Post by system11 on 2011-01-07
> **tredegar said:**
> Then just run **xgamma** at startup:
**xgamma -gamma 0.5**

**startx** starts X

It's for a kickstart build - the user isn't defined until later and multiple users may share one machine from time to time, so I needed it to be system level.  I considered replacing the Xorg binary with a script that calls the real Xorg while appending -gamma, but that's not a very nice solution and will cause problems later with updates.

I tried a skeleton xorg.conf with only the Monitor section defined with predictably dire results ;)  Another approach might be to put something in Xsession.d, I guess that's the next one to try.

---

