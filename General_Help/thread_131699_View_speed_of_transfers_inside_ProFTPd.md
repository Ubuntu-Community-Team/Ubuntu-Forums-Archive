---
title: "View speed of transfers inside ProFTPd?"
date: 2006-02-16
forum: General Help
---

### Post by jackmacokc on 2006-02-16
I am running a small ftp server and was wanting to monitor the speed of incoming and outgoing transfers. Is there a good way to do this? ftpwho and ftptop doesnt really show me anything. Searches in this forum yielded me no results.


Thanks!

---

### Post by taurus on 2006-02-16
Have a gdesklets' network applet running where it shows you the upload and download speeds of your eth0.  

[http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=79](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=79)
-or-
[http://gdesklets.gnomedesktop.org/shot/ftb_4.png](http://gdesklets.gnomedesktop.org/shot/ftb_4.png)

---

### Post by jackmacokc on 2006-02-16
[QUOTE=taurus]Have a gdesklets' network applet running where it shows you the upload and download speeds of your eth0.  

[http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=79](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=79)
-or-
[http://gdesklets.gnomedesktop.org/shot/ftb_4.png](http://gdesklets.gnomedesktop.org/shot/ftb_4.png)[/QUOTE]

Well I might as well just use system monitor. I'm not looking for the overall speed of eth0, but more specifically the speeds of individual users.

---

### Post by jackmacokc on 2006-02-17
Well I found my own answer, as is usually the case. But just in case someone searching wants the answer - try downloading gproftpd. Its the gui interface that can be used to configure proftpd (not recommended, if you ask me). But it can also be used to see the transfer speeds of the individual users.

I wish there was an easier method...

---

