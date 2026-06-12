---
title: "Cannot Recover From Sleep"
date: 2010-10-22
forum: General Help
---

### Post by LeifAndersen on 2010-10-22
I did a bit of searching but other people's problems seems a bit different than mine, so maybe one of you can help me.

I have a Sony Vaio VPC EB11fm, and the sleep doesn't work properly in Ubuntu 10.10 (it worked fine in 10.04), or rather, it can't wake up from sleep.  When I hit the power on button (or any button that should trigger a wakeup), the machine just starts up as if I had hit the shutdown button rather than the sleep button.  (Even though the sleep light was on, and the battery was slightly draining, as expected).

This differs from the other threads I've seen because apparently other people just get a black screen, and it just sits there (as I said, mine boots up just fine, as if I had hit the power off button rather than the sleep one).

I would have submitted a bug report, but I have no idea what programs/files I need to submit.  Commands like:

```
ubuntu-bug suspend
``` or ```
ubuntu-bug shutdown
```

don't seem to work because they apparently don't have packages.

Thank you...I really need sleep to work and would rather not go back to 10.04 if I don't have to. :)

---

### Post by Quackers on 2010-10-22
That's exactly what mine does when I try to hibernate. Suspend works perfectly for me. To wake up from suspend I just press the space bar. If I try waking from hibernate I have to press the power button and it does what appears to be a cold boot (except it then refuses to see my webcam, which isn't a problem at any other time).

---

### Post by LeifAndersen on 2010-10-22
Mmm...sorry, I must not have made myself clear enough.  This happens when I hit suspend (I haven't tried hibernate).

---

### Post by Quackers on 2010-10-22
No, you were perfectly clear about that. It is odd that I have the same symptoms, but only with hibernate, not suspend, and we both have Vaio's.

---

### Post by LeifAndersen on 2010-10-23
Ah, okay, yes that is weird...although I 'really' need to get this fixed soon, otherwise I'll have to leave for the old version...or possibly another distro. :(

---

### Post by Quackers on 2010-10-23
If you go to System > Preferences > Power Management Preferences and select the General tab, the second option is "when the suspend button is pressed". That's not set to hibernate is it?

---

### Post by LeifAndersen on 2010-10-24
Nope, it's set to suspend.

---

### Post by Quackers on 2010-10-24
Does your pc react the same way if you select suspend from the menu?

---

### Post by LeifAndersen on 2010-10-24
Yup...any way I select suspend it does the same thing.

---

