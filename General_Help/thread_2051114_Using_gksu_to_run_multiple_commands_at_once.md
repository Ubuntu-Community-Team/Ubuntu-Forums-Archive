---
title: "Using gksu to run multiple commands at once"
date: 2012-09-01
forum: General Help
---

### Post by jvofvnopz on 2012-09-01
I have been looking for a way to run multiple commands at a time with gksu/gksudo, and I'm not quitte able to figure out how. After Googling, the only info I found was a bug filing from 5 years ago:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg445413.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg445413.html)
The commands posted in the bug filing still don't work as of now (gksu 2.0.2).

Therefore, I'm wondering if it's possible to run multiple commands at once with gksu (or another program that might work better), and if so, how?

---

### Post by Lars Noodén on 2012-09-01
You'll probably have to put them together into a script and then call the script from gksu.

---

### Post by jvofvnopz on 2012-09-01
Actually I'm calling gksu from within a python script, and I need to use several booleans to see which commands I need to call, so putting them in a script wouldn't work, AFAIK.

---

### Post by Lars Noodén on 2012-09-01
If it can be typed at the keyboard by a human then it is very likely that it can also be made into a script.  As far as decisions go, shell scripts have [conditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals) like if-then-else and cases.  Maybe if you go into some of the details, a scripting solution will become apparent.  

Another reason for a script is that then you can add a line to [/etc/sudoers](http://manpages.ubuntu.com/manpages/precise/en/man5/sudoers.5.html) to authorize it to run.

---

### Post by jvofvnopz on 2012-09-01
In my python script, I use a few global booleans defined within the file  (controlled by some pygtk radio buttons and checkboxes) and several other variables  in order to create the commands, so I'm not necessarily sure of the feasibility of turning it into a shell script. I don't think editing /etc/sudoers is a good idea either, since I am packaging the script for installation. If you want to see the relevant script, you can see it here: [https://raw.github.com/luolimao/PKGBUILDs/master/orta-gtk-theme/OrtaSettingsManager.py](https://raw.github.com/luolimao/PKGBUILDs/master/orta-gtk-theme/OrtaSettingsManager.py)

---

### Post by Lars Noodén on 2012-09-01
Thanks.  My python skills are nearly non-existent but it looks like the way you are using gksudo that the user would only need to enter the password once per session, unless the credentials are allowed to time out.  In other words, sudo should be using cached credentials unless the user waits too long.  Is that not what's happening?

---

### Post by jvofvnopz on 2012-09-01
Well, for people who don't necessarily have their credentials cached, it would be good to be able to call gksu once instead of 5 or 6 times in a row. Also, if the user clicks cancel (e.g. if the user accidentally clicked ok, or something, and doesn't want to enter their password in) they are bombarded with several prompts in a row (even if credential caching is enabled).

---

