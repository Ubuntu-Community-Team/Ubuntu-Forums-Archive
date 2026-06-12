---
title: "Privacy and Firefox."
date: 2010-01-05
forum: General Help
---

### Post by zozza on 2010-01-05
I remember that one complaint about XP was the way that when you used Firefox or IE index.dat files were created which were violations of privacy.  

If, after browsing, one deletes the relevant firefox files are there any other locations or logs in Ubuntu that record details or times of browsing?

Currently these files seem to contain browsing history:

~/.mozilla/firefox/xxxxx.default/cookies.sqlite ~/.mozilla/firefox/xxxxx.default/formhistory.sqlite ~/.mozilla/firefox/xxxxx.default/downloads.sqlite ~/.mozilla/firefox/xxxxx.default/places.sqlite ~/.mozilla/firefox/xxxxx.default/places.sqlite-journal 

srm -vr ~/.mozilla/firefox/xxxxx.default/Cache/


I have looked in the /var/log directory and cannot see anything but perhaps other people know?

I just want to know if and where browsing activity is located (apart from in the /user/.mozilla directory).

Thanks.

---

### Post by Barriehie on 2010-01-06
> **zozza said:**
> 
...
~/.mozilla/firefox/xxxxx.default/places.sqlite
~/.mozilla/firefox/xxxxx.default/places.sqlite-journal 

srm -vr ~/.mozilla/firefox/xxxxx.default/Cache/
...
Thanks.

The first two files are for your bookmarks and FF will run faster if you put the cache in RAM and it will be volatile.  In the preferences you can tell FF what to 'forget'.  There is also an addon, [[color="blue"]clear private data[/color]](https://addons.mozilla.org/en-US/firefox/search?q=clear+private+data&cat=all&advancedsearch=1&as=1&appid=1&lver=3.0&atype=0&pp=20&pid=2&sort=&lup=), that does just that.

---

### Post by zozza on 2010-01-06
Yes, I don't mind Firefox using the cache or history because I can delete it later.

What I was wondering is if the log files in Ubuntu (for example those under /var/log) also contain browsing information.

Thanks.

---

### Post by Barriehie on 2010-01-06
> **zozza said:**
> Yes, I don't mind Firefox using the cache or history because I can delete it later.

What I was wondering is if the log files in Ubuntu (for example those under /var/log) also contain browsing information.

Thanks.

sys, kern, and I believe messages, contain IP address'.  /etc/syslog.conf is the config file for system logging.

HTH,

---

