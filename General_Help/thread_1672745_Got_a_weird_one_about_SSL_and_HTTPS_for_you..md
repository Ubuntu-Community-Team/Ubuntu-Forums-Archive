---
title: "Got a weird one about SSL and HTTPS for you."
date: 2011-01-21
forum: General Help
---

### Post by bcfieldi on 2011-01-21
So I've done a number of searches and no one seems to be having this problem but me. 

I have no idea what has happened that may have caused this to occur but whenever I attempt to go to certain websites that are https such as this one, [https://6-tech.uncg.edu/](https://6-tech.uncg.edu/) I get a connection refused error 102. 4 days ago this was not happening. It occurs on both Chrome and Firefox. I cleared cookies, made sure that SSL 3 was checked on. I can get to the https websites from any other computer. I have openssl installed and everything is up to date. 

Any ideas on what could have happened? Anyone else having this problem?

---

### Post by bcfieldi on 2011-01-21
bump

---

### Post by bcfieldi on 2011-01-22
bump. Anyone?

---

### Post by tredegar on 2011-01-22
OK you have no replies.

But I tried your link yesterday and it worked fine.

Maybe try creating a new user and connecting to the link from that. Still the same problem?

If so then your linux is broken so do forensics or reinstall (and don't "play" too much next time).
If not then your user settings are broken.

What did you do that could have broken this?

---

### Post by bcfieldi on 2011-01-22
No, logging into guest does not work. Clearly the settings are broken, but it's not from playing. The website worked fine, I did a regular update through update manager and tried the website eight hours later, having done absolutely nothing else to my system otherwise, and it doesn't work. My SSL settings system-wide are broken somehow. 

Looks like I'll be doing a reinstall since I "played" too much. 

Thanks though.

---

### Post by dcstar on 2011-01-22
> **bcfieldi said:**
> So I've done a number of searches and no one seems to be having this problem but me. 

I have no idea what has happened that may have caused this to occur but whenever I attempt to go to certain websites that are https such as this one, [https://6-tech.uncg.edu/](https://6-tech.uncg.edu/) I get a connection refused error 102. 4 days ago this was not happening. It occurs on both Chrome and Firefox. I cleared cookies, made sure that SSL 3 was checked on. I can get to the https websites from any other computer. I have openssl installed and everything is up to date. 

Any ideas on what could have happened? Anyone else having this problem?

That site works fine on my system. The site uses AES-128 bit encryption so I would check that your system still supports that.

If you have a certificate for that site stored on your system already you may want to remove it. Also check/remove any Proxy settings in your system.

---

