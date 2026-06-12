---
title: "FireFox frequently and abruptly closes"
date: 2010-06-25
forum: General Help
---

### Post by OxentroT on 2010-06-25
Sometimes I'll be in the middle of typing something. And to add insult to injury (being the hunt-and-peck type that I still am) I look up to submit and see the browser is no longer there. It just closed with no known cause. What could it be, script errors within a page?

Also, this could just be the paranoid me within. On a couple of occasions I have been redirected to pages that are other than the destination intended after typing in an address.
Could my browser have been hi-jacked? 8-[

---

### Post by mooreted on 2010-06-25
Open a terminal and type firefox then press enter. Use FF as normal until it crashes and look at the terminal. This may show errors that can help us figure out the problem.

Do you have any addons or extensions in FF? Could be an addon acting up.

Most crashes in FF are caused by flash.

---

### Post by philinux on 2010-06-25
Also try running in safe mode from the terminal.

```
firefox -safe-mode
```

That will eliminate any extensions.

---

### Post by lovinglinux on 2010-06-25
See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by efflandt on 2010-06-25
What cpu do you have, and if using real 64-bit flash instead of flashplugin-installer on 64-bit, does cat /proc/cpuinfo show the lahf_lm instruction?

I have an early Athlon64 3200+ and the only time firefox seemed to vaporize (in 64-bit 9.10) was when I used 64-bit flash before I learned of the flashplugin_lahf_fix.so someone posted.  But since Hulu stopped working with 64-bit flash in a browser, and Hulu Desktop did not see the extra plugin, I have been using flashplugin-installer instead, which is actually 32-bit flash with nswrapper) and have had no issues with firefox (9.10 or 10.04).  Although, flash is not too quick on this old machine (I have Visual Effects set to None).

If your firefox crashes on flash, flash ads can sometimes be an issue.

---

### Post by OxentroT on 2010-06-29
Good Morning! and Thank You all for the feedback. ):P


> Open a terminal and type firefox then press enter. Use FF as normal until it crashes and look at the terminal. This may show errors that can help us figure out the problem.

-Whenever I open a Terminal and type in ```
firefox
``` it shows no data. It just opens a Firefox browser.

_________________________________________________________________________

> Do you have any addons or extensions in FF? Could be an addon acting up.

-Yes I have Flash, JRE, Greasemonkey, and Flashgot, 

_________________________________________________________________________

> What cpu do you have, and if using real 64-bit flash instead of flashplugin-installer on 64-bit, does cat /proc/cpuinfo show the lahf_lm instruction?

I have a Lenovo Thinkcentre with PendiumD x86


Thank You all again and sorry for latency in feedback to response.

:guitar:

---

### Post by lovinglinux on 2010-06-29
Try to [create a new profile](http://firefox-tutorials.blogspot.com/2010/05/profiles.html) to see if the problem persists.

---

### Post by OxentroT on 2010-06-29
> Try to create a new profile to see if the problem persists.

I will try that and keep posted on this issue. 

Thank you.

:guitar:

---

### Post by bigtom71 on 2010-06-29
There seems to be a problem with flash in firefox which is causing the problem with the browser shutting down. Mozilla said that the next update should fix the problem.

---

### Post by OxentroT on 2010-06-30
That's what I suspected (or @ least hoped for anyways). As paranoid ol' me suspected feared the scant possibility of browser-jacking, as a couple of times I have been redirected to places other than my intended destination. 
However, I am still a sloppy typer some 12 years or so after my first encounter with a computer so it could have been my fault. :redface:

Need to download a typing class of some sort. But tendencies towards procrastination coincides with my underlying stubbornness.:lolflag:

I am going to go ahead and quit babbling on and mark-this-post-as-[SOLVED]

Thank You All For Your Inputs. 
And as always, r0ck-0n!         :guitar:

---

