---
title: "chrome is now jerky on youtube video, firefox good"
date: 2012-07-06
forum: General Help
---

### Post by sdowney717 on 2012-07-06
Either the recent Chrome, Kernel, flash update to 11.3 has caused chrome to halt and jerk on youtube. Bad enough to make it unwatchable.

Firefox runs smoothly 

So what to do? I have liked using chrome for a year and dont want to go back to Firefox.

---

### Post by sdowney717 on 2012-07-06
firefox is using flash 11.2
chrome is using flash 11.3

11.3 is jerky so how to get chrome to use version 11.2?

notice first pic is chrome using 11.3, second is firefox using 11.2 ??????????????????

---

### Post by sdowney717 on 2012-07-08
Chrome is awful this AM, scrolling has gotten really slow and jerky on all websites and videos wont even open in full screen.
I am wondering what happened in the last few days?

---

### Post by Rexilion on 2012-07-08
Chrome is using the new Pepper API for it's plugins. Adobe and Google are working together to develop and extend Flash for this API. It's relatively new.

Hence, each time you upgrade chrome, you are rolling the dice.

Perhaps chromium would do?

---

### Post by sdowney717 on 2012-07-09
found the solution is to disable pepper flash!
This was causing all sorts of trouble and some not so obviously flash related, slow jerky scrolling, unresponsive pages.
They should completely pull this idea until it works.
Now it is working as before.

I am surprised to not see lots of complaints here.

[https://productforums.google.com/forum/?fromgroups#!topic/chrome/Mi-YgjNGaaQ](https://productforums.google.com/forum/?fromgroups#!topic/chrome/Mi-YgjNGaaQ)

> On Friday, June 29, 2012 5:45:54 AM UTC-7, bfo wrote:
> Linux users: In Chrome version 20 or later, Adobe Flash Player uses a new API to run its plug-in in Linux Chrome. The new API is a cross-platform API for plug-ins known as the Pepper API (PPAPI).

Thanks for the tip!

So the workaround for this is to change the Flash plug-in that gets loaded:

1. In the URL bar enter chrome://plugins/
2. Locate the Flash plug-in, you should see multiple versions listed
3. Click Disable for the plug-in with the location /opt/google/chrome/PepperFlash/libpepflashplayer.so
4. You should still have one enabled in another location, like /usr/lib/adobe-flashplugin/libflashplayer.so
5. Restart Chrome (quit and open again)

It's nice that they now include Flash with Chrome for 64-bit Linux, but if it can't do fullscreen it's kind of pointless.



---

### Post by Pilot6 on 2012-07-09
On many systems new pepperflash works OK with full screen.

---

### Post by Rexilion on 2012-08-25
Perhaps you have some compositing window manager that interferes?

---

