---
title: "Can't change default web browser in Ubuntu 11.10?"
date: 2011-12-24
forum: General Help
---

### Post by soylentcola on 2011-12-24
So I'm running Ubuntu 11.10 (duh) and I'm trying to change my default browser from Firefox to Chromium but for some reason, every time I go to system settings -> System Info -> Default Applications and change it, it doesn't seem to save. It continually tells me every time I open Chromium that it's not my default browser.

Even trying to set it in Chromium doesn't seem to work. Is there something I'm missing here?

---

### Post by soylentcola on 2011-12-26
Bumping~

---

### Post by soylentcola on 2011-12-28
Still nothing? :c

---

### Post by cyprys on 2011-12-28
Works for me. Try to log into new user's account and change it there. If it works you'll want to look at your $HOME permissions.

---

### Post by soylentcola on 2011-12-29
Strangely enough, I made a new (standard) account and everything stuck just fine.  I upgraded my current account to Administrator (as apparently it was a "Custom" acocunt) to see if that'll fix this problem, I may just uncheck a few things I don't really know about.

But just for knowledge's sake, how exactly does one check their $HOME permissions?

---

### Post by West201 on 2011-12-29
I found this very old article on setting default browser using the terminal. I would give it a try. 

[http://www.howtogeek.com/howto/ubuntu/set-the-default-browser-on-ubuntu-from-the-command-line/](http://www.howtogeek.com/howto/ubuntu/set-the-default-browser-on-ubuntu-from-the-command-line/)

---

### Post by West201 on 2011-12-29
Here is another link. 
[http://www.simplehelp.net/2009/05/07/how-to-change-the-default-web-browser-in-ubuntu/](http://www.simplehelp.net/2009/05/07/how-to-change-the-default-web-browser-in-ubuntu/)

---

### Post by cyprys on 2012-01-07
> **soylentcola said:**
> (...) But just for knowledge's sake, how exactly does one check their $HOME permissions?

Please, mark the thread as solved (giving you find the resolution satisfying).

What I meant was going to your $HOME directory (which probably is /home/soylentcola - btw. cool nickname) and listing all files without write permission. The result should be a reasonably short list. I only assume this setting is stored in $HOME (don't really know how does *Debian alternatives system* work in detail). The above can be accomplished in terminal with the following set of commands:
```

cd
find . ! -perm /u+w

```

---

### Post by MJV_fi on 2012-01-10
I (may have) had the same problem with Ubuntu Studio 11.10 (with XFCE). I set Chrome as my default browser in preferred applications but when I launched it, it still claimed it wasn't set as the default browser. So I saved the preference from inside Chrome as well. And still, the next time I logged in, I didn't have a default browser set.

I finally realized that setting the value in preferred applications and from inside Chrome somehow must have set it differently, i.e. making Chrome my default browser when launching it cleared the setting from preferred applications. So I finally made the choice stick by selecting "no" on Chrome startup when it asks to make it my default and configuring it to skip asking me again.

I'm not sure if your problem was exactly the same, and thus if the same solution applies... I installed Chrome from a downloaded .deb file (and removed Firefox), don't know if that made a difference.

---

### Post by doktorOblivion on 2012-01-10
To see what is default browser now:
xdg-mime query default text/html

To update it:
xdg-mime default firefox.desktop text/html
(or xdg-mime default google-chrome.desktop text/html if you're switching to Chrome)

---

### Post by MJV_fi on 2012-01-12
> **doktorOblivion said:**
> To see what is default browser now:
xdg-mime query default text/html

I get "firefox.desktop" but Settings > Preferred Applications says "google-chrome". Weird.

---

### Post by tgerbert on 2012-01-16
> **MJV_fi said:**
> So I finally made the choice stick by selecting "no" on Chrome startup when it asks to make it my default and configuring it to skip asking me again.

Brilliant! Really, it was a minor problem but it was so annoying - drove me nuts. Setting the default as you described worked a charm.

I wonder what's different about setting the default between the two methods - I would have assumed both used xdg...

---

### Post by Cyr4x on 2012-01-16
For me, the default applications panel doesn't show any of the Google Chrome versions (stable, beta, dev) to choose as a default browser. I install it from the original Google repo. There's only a Firefox to choose on the list. If i install Chromium instead of Chrome it appears on the list too.

'xdg-mime query default text/html' command says, that the google-chrome.desktop is a default browser, but other applications (i.e. Thunderbird) still open Firefox.

EDIT:
Fixed. Just needed to copy google-chrome.desktop from /usr/share/applications to ~/.local/share/applications

---

