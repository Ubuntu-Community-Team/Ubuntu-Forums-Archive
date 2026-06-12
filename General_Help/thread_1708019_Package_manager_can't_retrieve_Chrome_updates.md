---
title: "Package manager can't retrieve Chrome updates"
date: 2011-03-16
forum: General Help
---

### Post by bkline on 2011-03-16
Anyone else running into this failure?

> Chrome Failed to fetch [http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-beta/google-chrome-beta_10.0.648.133-r77742_amd64.deb](http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-beta/google-chrome-beta_10.0.648.133-r77742_amd64.deb) 404  Not Found [IP: 72.14.204.91 80]


---

### Post by falko on 2011-03-16
You're trying to download a non-existing package. I get

> The requested URL /linux/chrome/deb/pool/main/g/google-chrome-beta/google-chrome-beta_10.0.648.133-r77742_amd64.deb  was not found on this server.

when I type this URL in my browser.

---

### Post by bkline on 2011-03-16
> **falko said:**
> You're trying to download a non-existing package. ....

Thanks for the reply.  However, I'm not randomly trying to retrieve that package in my browser.  Update Manager is trying to pull it down because Google's repository is telling it to.  Sorry if I didn't make that clear in my OP.

---

### Post by bkline on 2011-03-16
Looks like they fixed the problem.  I guess they forget they're supposed to post the file first and then tell the clients to come get it. :-)

---

