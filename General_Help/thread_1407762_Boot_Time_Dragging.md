---
title: "Boot Time Dragging"
date: 2010-02-15
forum: General Help
---

### Post by fgerst on 2010-02-15
I have just completed a clean install of Intrepid Ibex. However, my boot time is dragging significantly, specifically after my login. After the splash screen, the computer hangs for approx. 1-2 minutes before my desktop appears and I can interact with the computer. What can I do to improve this time? 

Attached is a bootchart.

---

### Post by ironclaw on 2010-02-16
Can you upload the bootchart as a png instead or enlarge it? Some of the text is not readable.

---

### Post by fgerst on 2010-02-16
Try that out. Thanks for your help.

---

### Post by fgerst on 2010-02-16
Sorry I'm having a little trouble here...

---

### Post by ironclaw on 2010-02-16
Hmm... It looks like it's actually booting up quite quickly, so from your description, it must be taking a long time to get into the GNOME Desktop after the system has booted up. I have no idea why that would be. If you log out and log back in without rebooting, does it take a long time?

An idea would be to create a new user account, and see if that account takes a long time to log in. If it doesn't, then it must be some custom user configuration that is slowing down your log in.

---

### Post by fgerst on 2010-02-16
No, the time is significantly reduced when I just log out/log in.

---

### Post by philinux on 2010-02-16
> **fgerst said:**
> No, the time is significantly reduced when I just log out/log in.

Any reason for running Intrepid? Support finishes this April.
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history)

I seem to remember this bug when I ran intrepid.

Might be compiz. Try disabling it.

---

### Post by fgerst on 2010-02-16
Also, I just tried making a new account and the problems persists.

---

### Post by fgerst on 2010-02-16
> **philinux said:**
> Any reason for running Intrepid? Support finishes this April.
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history)

I seem to remember this bug when I ran intrepid.

Might be compiz. Try disabling it.

This did the trick! Thanks.

---

