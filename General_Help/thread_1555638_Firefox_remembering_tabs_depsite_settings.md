---
title: "Firefox remembering tabs depsite settings"
date: 2010-08-18
forum: General Help
---

### Post by Karl1982 on 2010-08-18
I have Ubuntu 10.04 x86 on my laptop.  I think I had this problem with older versions, but I can't remember.  Needless to say it's been going on for a while.  Firefox is set explicitly to go to my home page ([http://www.google.com/](http://www.google.com/)) when opening, but it frequently (50% or better) instead opens my tabs from my last session.  

How can I fix this?

---

### Post by sydbat on 2010-08-18
> **Karl1982 said:**
> I have Ubuntu 10.04 x86 on my laptop.  I think I had this problem with older versions, but I can't remember.  Needless to say it's been going on for a while.  Firefox is set explicitly to go to my home page ([http://www.google.com/](http://www.google.com/)) when opening, but it frequently (50% or better) instead opens my tabs from my last session.  

How can I fix this?When you close Firefox, do you choose 'Save & Quit'? That will open your tabs next time.

Also, go into Edit > Preferences and then the 'Privacy' tab. There are a lot of options in there to clear your history when shutting FF down.

---

### Post by Karl1982 on 2010-08-18
It no longer asks me whether I want to save and quit, or just quit, but originally I selected quit and don't prompt again.

In preferences, general tab, I have selected "When Firefox starts: Show my homepage."  Half the time it actually does that, the other half it opens whatever I closed the browser with last time.

Under privacy, I have "Remember history."  I'm not necessarily looking to clean history on exit.  I just want it to consistently open my home page when I start Firefox.

---

### Post by katoiam on 2010-08-18
funny cause I am having the opposite problem! My firefox doesn't remember what I had open. It no longer asks me if I want to save and quit and never remembers what tabs I had open even though that's what I want it to do!
Any ideas

---

### Post by Nytram on 2010-08-18
> **Karl1982 said:**
> I have Ubuntu 10.04 x86 on my laptop.  I think I had this problem with older versions, but I can't remember.  Needless to say it's been going on for a while.  Firefox is set explicitly to go to my home page ([http://www.google.com/](http://www.google.com/)) when opening, but it frequently (50% or better) instead opens my tabs from my last session.  

How can I fix this?

Do you close Firefox before you shutdown or reboot? If you leave it open it thinks it has crashed and will restore all the tabs when next started.

---

### Post by lovinglinux on 2010-08-19
[http://kb.mozillazine.org/Session_Restore](http://kb.mozillazine.org/Session_Restore)

---

### Post by Karl1982 on 2010-08-19
> **Nytram said:**
> Do you close Firefox before you shutdown or reboot? If you leave it open it thinks it has crashed and will restore all the tabs when next started.

I thought of that.  Actually, I've had it do it sometimes after just closing the browser and opening it again a few minutes later.

I'll try setting browser.sessionstore.resume_from_crash to false and see how it goes.  That's not exactly what I wanted to do, but it seems like the most likely culprit.  I don't want to disable session restoration entirely if it can be helped.

---

### Post by stevehanler on 2011-01-17
I'm having this same problem in Ubuntu 10.10. It happens if I shutdown my laptop without closing Firefox first. I have browser.sessionstore.resume_from_crash set to False.

---

