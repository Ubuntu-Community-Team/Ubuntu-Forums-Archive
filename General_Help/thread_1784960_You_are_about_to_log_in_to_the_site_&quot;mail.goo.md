---
title: "You are about to log in to the site &quot;mail.google.com&quot; with the username"
date: 2011-06-17
forum: General Help
---

### Post by pyrforos on 2011-06-17
Hi guys
After the last update every time when i try to see my mails from gmail , with the use of any app like plasmoid-gmail or kmail notifier, appears a window with this title
> "You are about to log in to the site "mail.google.com" with the username "*********", but the website does not require authentication. This may be an attempt to trick you.
Is "mail.google.com" the site you want to visit?"
 Any ideas how to solve this?

---

### Post by DirtyPC on 2011-06-17
Try

sudo apt-get install prism-google-mail

---

### Post by pyrforos on 2011-06-17
```
 Unable to locate package prism-google-mail

```

Do we know the reason for the error?(not the above the one i mentioned at the first post  ) Because i'd like to fix that not just use another app...

---

### Post by DirtyPC on 2011-06-17
Well the prism app is the official, and that worked fine for me after others did the same thing for me. prism is the official one anyway. Search it in ubuntu software center, its just called gmail

---

### Post by ankspo71 on 2011-06-18
Hi,
I'm not sure what the problem could be, but have you tried deleting the configuration files for those applications? Sometimes those configuration files get messed up after updates. The configuration files are located inside hidden directories inside your home folder. KDE application's configuration files would be located inside /home/yourname/.kde/share/config/

"kgmailnotifier" is working good for me and Gmail itself has been working good for me too, so I'm thinking the problem is within the config files.
Hope this helps.

---

### Post by Thewhistlingwind on 2011-06-18
traceroute mail.google.com

Never discount the possibility of a real man-in-the-middle.

(74.125.127.17)  Here.

(If I am currently being stupid, please tell me.)

---

### Post by pyrforos on 2011-06-18
ok i uninstalled-reinstall the app. Deleted all config files from .kde .The problem persists...

@Thewhistlingwind:
Im not sure what you want me to do.I traceroot-ed mail.google.com but it seems ok...

I also tried this [http://forums.mozillazine.org/viewtopic.php?f=38&t=288262](http://forums.mozillazine.org/viewtopic.php?f=38&t=288262) with no affect ..

---

### Post by ankspo71 on 2011-06-18
This link might help:
[http://support.mozilla.com/en-US/questions/748119](http://support.mozilla.com/en-US/questions/748119)

---

### Post by pyrforos on 2011-06-18
> This link might help:
[http://support.mozilla.com/en-US/questions/748119](http://support.mozilla.com/en-US/questions/748119)
didn't work

---

### Post by pyrforos on 2011-06-20
so. i guess there is nothing to do except to wait for an update

---

### Post by auspex on 2011-06-21
I'm not sure how "wait for an update" is going to help, since there doesn't seem to be a bug report, and nobody but you and me seems to have this problem.  

How can prism-google-mail possibly be the "official" notifier, when it isn't in the official repos [it _was_ in Universe, but prism itself is no longer in Natty]?

fwiw, I've seen that same error in a completely different app - iirc, it happened when using a URL with an embedded username/password.  If that's what kgmailnotifier is doing, I'm not sure I like it, since it rather defeats the purpose of using an HTTPS login.

---

### Post by pyrforos on 2011-06-24
[http://kde-look.org/content/show.php](http://kde-look.org/content/show.php)
Seems like the creator works on that... 
going to report the bug @ [http://code.google.com/p/gmail-plasmoid/](http://code.google.com/p/gmail-plasmoid/)

---

### Post by Dangertux on 2011-06-24
I believe what Thewhistlingwind was eluding to is a type of attack that tries to harvest your credentials by impersonating the server you are attempting to connect to. Your client then provides credentials to something that isn't what it claims to be.

While the error given by the application does indicate that as a possibility, it could also be a simple error in the software design. However, it is in your best interest to make sure that the server that claims it is mail.google.com is what it says. Which is why Thewhistlingwind provided the mailserver IP from his/her perspective. If it differs from your traceroute results, then you should be cautious.

---

### Post by Capt-Nuss on 2012-12-11
Hi,

i'm getting the same error for all of my mailaccounts. They are located at sveral different free mail provideres and some are selve hosted. I do'nt beliefe in a man-in-the-middle attac.
I created a new user on my computer and configuered Kmail to use one of my accounts. Everything works fine!
Next step was to remove the Kmail config from my standard account, but i did not succed, i'll guess i missed somthing.
Was the problem solved here, or did you just stop discussing about it?
i first faced this at the end of november.

THX

---

### Post by Capt-Nuss on 2012-12-12
Problem solved for me ;-}

A Proxy was configured in "System Settings > Network Settings > Proxy"
@home i don't have any proxy, so i'm shure that i did not entered it here. Anyway, after deleting it, i can get my mails!

---

