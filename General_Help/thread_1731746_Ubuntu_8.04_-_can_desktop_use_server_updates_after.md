---
title: "Ubuntu 8.04 - can desktop use server updates after 12th May?"
date: 2011-04-17
forum: General Help
---

### Post by Cato2 on 2011-04-17
I have some PCs still on Ubuntu 8.04 Desktop including one that's remote - I realise that desktop updates will be stopped from May 12th, but will the Server packages still be available to Desktop installations for the next 2 years?  I believe that APT doesn't know the difference anyway.

I had a look at the announcement but it doesn't cover this question: [http://ubuntu-news.org/2011/04/11/ubuntu-8-04-reaches-end-of-life-on-may-12-2011/](http://ubuntu-news.org/2011/04/11/ubuntu-8-04-reaches-end-of-life-on-may-12-2011/)

---

### Post by dino99 on 2011-04-17
from hardy release:

About Ubuntu 8.04.4 LTS
-----------------------

This is the fourth maintenance release of Ubuntu 8.04 LTS, which
continues to be supported with maintenance updates and security fixes
until April 2011 on desktops and April 2013 on servers.

So as i understand you might switch desktops to lucid to get updates

---

### Post by sanderj on 2011-04-17
> **Cato2 said:**
> I have some PCs still on Ubuntu 8.04 Desktop including one that's remote - I realise that desktop updates will be stopped from May 12th, but will the Server packages still be available to Desktop installations for the next 2 years?  I believe that APT doesn't know the difference anyway.

I had a look at the announcement but it doesn't cover this question: [http://ubuntu-news.org/2011/04/11/ubuntu-8-04-reaches-end-of-life-on-may-12-2011/](http://ubuntu-news.org/2011/04/11/ubuntu-8-04-reaches-end-of-life-on-may-12-2011/)

Interesting question. I don't know the answer. You could wait and see, or you could install 6.06 LTS Desktop version ([http://old-releases.ubuntu.com/releases/6.06.1/](http://old-releases.ubuntu.com/releases/6.06.1/)) on a test (virtual) machine, and see if it gets updates from the server repository (supported til 2011-06).

BTW: AFAIK Ubuntu server has no GUI, so that would mean you won't get updates in Firefox, X server, etc.
Furthermoe: I don't know if a server has the same kernel vesion as desktop version.

---

