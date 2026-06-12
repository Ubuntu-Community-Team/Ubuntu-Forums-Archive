---
title: "firefox 3.5 (shiretoko) javascript issues"
date: 2009-08-10
forum: General Help
---

### Post by v1nsai on 2009-08-10
I think I'm having problems with javascript in shiretoko firefox 3.5 whatever.  I was trying to attach something to an email in Hotmail, and when I clicked the attach button, nothing happened.  I clicked many, many times and yelled many profanities at the screen, but still nothing happened.

This could possibly be my fault however.  When I installed shiretoko and got comfortable with it I wanted it to be the only firefox, so I deleted the symlink to firefox 3.0 in /usr/bin and replaced it with a symlink to firefox 3.5 that was named firefox, so now when I or any program like pidgin try to access a web page, it will be deferred to firefox 3.5 (one firefox to rule them all).  

I'm not sure what implications that might have but I felt it was worth mentioning.  Can anyone suggest a way to get this working again?  I'm looking for another site to test out my javascript functionality so I'll post back if it turns out to be just Hotmail.

---

### Post by v1nsai on 2009-08-11
bumping, still haven't fixed this.  Still haven't found another site that uses a lot of javascript to test it out on, but I deleted my .mozilla folder to fix another problem and that problem was fixed but I still can't attach files in Hotmail.  I had no problem doing this under windows.

I would really appreciate a suggestion or something.

---

### Post by v1nsai on 2009-08-11
I got smart and typed 'test javascript' into google and I do not have javascript.  I checked in preferences, and according to a little box next to 'enable javascript' I do indeed have javascript enabled.

So what the hell?

---

### Post by dcstar on 2009-08-11
> **v1nsai said:**
> I got smart and typed 'test javascript' into google and I do not have javascript.  I checked in preferences, and according to a little box next to 'enable javascript' I do indeed have javascript enabled.

So what the hell?

Some web sites check your browser version and will not work properly with new browsers like Shiretoko because they haven't changed their own code yet (eBay for one when selling items, for instance).

Contact this website and tell them you are having problems.

---

### Post by john stiles on 2009-08-11
I recommend installing the new Firefox using the Ubuntuzilla: Mozilla Software Installer which should keep it and you up to date. [http://tombuntu.com/](http://tombuntu.com/) has written a good article on this.

---

### Post by v1nsai on 2009-08-12
That absolutely ROCKS thanks a million John.  The main site I was having trouble with was Hotmail, I couldn't get it to let me put an attachment in an email because clicking the Attach button didn't do anything.  This fixed it.  Awesome, thank you!

---

### Post by Thanh-BKK on 2009-08-12
Hi.

I don't know if this is of any help but ui am experiencing the exact same issue (i.e. the javascript on Hotmail behaving very erratically) yet for me it happens on a Windows-Computer with Firefox 3.5. 

Usually if javascript gets stuck refreshing the page helps in my case. 

No such issue in Ubuntu by the way, using Swiftfox 3.5.

Kind regards.....

Thanh

---

