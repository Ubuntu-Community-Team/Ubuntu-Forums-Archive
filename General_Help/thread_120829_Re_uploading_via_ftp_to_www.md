---
title: "Re: uploading via ftp to www"
date: 2006-01-23
forum: General Help
---

### Post by invalid on 2006-01-23
I know there is a graphical frontend for proftpd, that may allow this - but I can not remember the name of it off the top of my head.

My suggestion, however, is to have users use local public_html folders. In your ftp account settings, simply lock the users to their home directory (/home/user). Give them a folder (/home/user/public_html) and let them upload away.

You can access these by [http://yourdomain/~user](http://yourdomain/~user)

I hope this helps a bit, maybe someone else can remember the name of the graphical frontend that may help some more.

Edit: Hm.. trying to figure out why my reply is above the question.. maybe changes in the forum? Or maybe I clicked a strange option.. in either case, this is very silly and confusing.

---

### Post by Neoph on 2006-01-23
Running Apache 2 and proftpd.

I'd like to be able to upload web pages to /var/www using ftp.

I've installed Apache and proftpd. But have not had any success in changing the default ftp dir to /var/www and creating a user that can access it with a ftp client and upload web pages.

Any help is appreciated.

Thanks

Neo

---

