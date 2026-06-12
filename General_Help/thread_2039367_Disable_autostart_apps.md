---
title: "Disable autostart apps"
date: 2012-08-08
forum: General Help
---

### Post by Statia on 2012-08-08
I forgot to close my file manager once on logout from KDE, now it gets autostarted every time I log in to KDE. I only want my desktop widgets and Superkaramba apps to autostart. I already tried to save the session (System Settings - Startup and Shutdown - Session Management: Restore manually saved session) without the file manager, logging out, logging back in, but the file manager started again. How to make it stay away?

---

### Post by cortman on 2012-08-08
> **Statia said:**
> I forgot to close my file manager once on logout from KDE, now it gets autostarted every time I log in to KDE. I only want my desktop widgets and Superkaramba apps to autostart. I already tried to save the session (System Settings - Startup and Shutdown - Session Management: Restore manually saved session) without the file manager, logging out, logging back in, but the file manager started again. How to make it stay away?

Can you reverse the process given [here]("http://cortman.wordpress.com/2012/06/06/add-startup-program-to-almost-any-de/")? :)

---

### Post by drmrgd on 2012-08-08
On my Kubuntu install, I found the restore session to be a bit flaky.  Sometimes it just keeps opening stuff that I've closed just as you describe.  If you don't want to manually add each item you want autostarted as Cortman suggests, you could try to change the selection to start new session, log out and back, and open what you want, and change it back to restore session (in essence clearing it out and starting over again).  For some reason, though, this always has been a little bit wonky for me, unfortunately (though I didn't play with it very much to be honest!)

---

### Post by Statia on 2012-08-08
> **cortman said:**
> Can you reverse the process given [here]("http://cortman.wordpress.com/2012/06/06/add-startup-program-to-almost-any-de/")? :)

No, because the file manager is not listed in the Autostart. I had checked that already.

There is something there which makes me wonder if it is correct: 
gtk2-default-theme.rc.sh is listed twice: once under Startup, once under pre-KDE startup.

EDIT: removed the instance under pre-KDE startup, logged out, log back in, it's back again...

---

### Post by Statia on 2012-08-08
> **drmrgd said:**
>  you could try to change the selection to start new session, log out and back, and open what you want, and change it back to restore session (in essence clearing it out and starting over again).  For some reason, though, this always has been a little bit wonky for me, unfortunately (though I didn't play with it very much to be honest!)

That solved it, thanks!

---

