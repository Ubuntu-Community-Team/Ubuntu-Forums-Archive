---
title: "Firefox keeps crashing :("
date: 2010-12-31
forum: General Help
---

### Post by Florenceblues on 2010-12-31
Hai I'm really new to Ubuntu I used it for the first time 3 minutes ago with a live cd. The thing is every time I try to search something firefox crashes. My laptop connects to the network easily, and when I click on firefox it loads the about:home page. However when I searh google or anything Firefox just crashes. This is very upsetting my boyfriend can't figure it out. And so i'm all alone. Please help.

---

### Post by lithopsian on 2010-12-31
Although it doesn't solve your problem, try a different browser (Opera and Chrome are in the repositories and maybe already on your machine).  What they do will give some clues about what is happening.  You're not doing something obvious like running a 64 bit version on a 32 bit machine are you?  Play around with some other programs too, see if they ever crash.

---

### Post by Florenceblues on 2010-12-31
My boyfriend says its definitely 32 bit, and nothing else crashes.

---

### Post by wojox on 2010-12-31
Open your terminal and run **firefox** from it and when it crashes post back what the terminal says.

---

### Post by OpenGLSecond on 2010-12-31
> **Florenceblues said:**
> Hai I'm really new to Ubuntu I used it for the first time 3 minutes ago with a live cd. The thing is every time I try to search something firefox crashes. My laptop connects to the network easily, and when I click on firefox it loads the about:home page. However when I searh google or anything Firefox just crashes. This is very upsetting my boyfriend can't figure it out. And so i'm all alone. Please help.

Maybe upgrade firefox?

---

### Post by Florenceblues on 2010-12-31
> **wojox said:**
> Open your terminal and run **firefox** from it and when it crashes post back what the terminal says.


How do I do that? Sorry for the silly question, but like I said I'm very new to Ubuntu.


Edit- 

I do not have this problem in Ubuntu 10.04. It works perfectly only in 10.10. Any ideas?

---

### Post by ajgreeny on 2010-12-31
Try renaming the hidden ~/.mozilla folder in your home (hit Ctrl+H if you can't see it), then restart Firefox.  A corrupt user profile can sometimes cause this problem.

If that works OK you will then need to restore your bookmarks (probably most important) and perhaps a few other things from the renamed old folder, but let's go one step at a time.

---

### Post by OpenGLSecond on 2010-12-31
> **Florenceblues said:**
> How do I do that? Sorry for the silly question, but like I said I'm very new to Ubuntu.


Edit- 

I do not have this problem in Ubuntu 10.04. It works perfectly only in 10.10. Any ideas?

10.10 is still alpha(as far as I know)...

---

### Post by Florenceblues on 2010-12-31
Actually no 10.10 is no longer alpha and has been fully released for quite some time. I just decided to stick with 10.04.

---

### Post by wojox on 2010-12-31
> **OpenGLSecond said:**
> 10.10 is still alpha(as far as I know)...

10.10 is far beyond Alpha. I'm testing 11.04 Alpha as of now. :p

> **Florenceblues said:**
> Actually no 10.10 is no longer alpha and has been fully released for quite some time. I just decided to stick with 10.04.

10.04 is a good option. Did you try any of the suggestions posted above? 

Are you really still running from a Live-CD or did you install 10.10?

---

### Post by lovinglinux on 2011-01-01
Open Firefox Preferences, click the **Security** tab, then deselect the options to *Block reported attack sites* and *block reported web forgeries*.

Then type about[noparse]:[/noparse]config in the address bar, then type **network.dns.disableIPv6** in the filter, double click the option with that name that will appear in the list, in order to set the value to **false**.

I suppose you are running a clean profile. If you have copied the Firefox profile from Windows, then you might have corrupted files, a problematic extension or sub-optimal settings. See my Firefox [General Troubleshooting ](http://www.webgapps.org/firefox/general-troubleshooting) tutorial.

Also check the optimization tutorials there.

---

