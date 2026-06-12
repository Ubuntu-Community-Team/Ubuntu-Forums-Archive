---
title: "Updating Ubuntu Firefox"
date: 2006-06-02
forum: General Help
---

### Post by Hoffmann on 2006-06-02
When I was a Breezt user, I have sucessfully upgraded Mozilla-Firefox 1.5.0.2 to Mozilla-Firefox 1.5.0.3, by following the link: [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

> ... sudo chown -R ${USER}:${USER} /opt/firefox Start Firefox normally and update (Help -> Check for updates...) Once the update is completed, close Firefox and then restore ownership to root: sudo chown -R root:root /opt/firefox ....

My question is:

Is it possible to do the same with Ubuntu-Firefox? I mean, just changing "/opt/firefox" above to "/lib/firefox/firefox"?

What do you think?

---

### Post by garyng on 2006-06-02
If it is security fix, I believe ubuntu has the obligation to fix it so apt-get update follow by apt-get upgrade should do it.

---

### Post by Hoffmann on 2006-06-02
[QUOTE=garyng]If it is security fix, I believe ubuntu has the obligation to fix it so apt-get update follow by apt-get upgrade should do it.[/QUOTE]
It is a security fix. The newest version of Firefox (1.5.0.4) is about that. Take a look on this link: [http://www.mozilla.org/projects/security/known-vulnerabilities.html#firefox1.5.0.4](http://www.mozilla.org/projects/security/known-vulnerabilities.html#firefox1.5.0.4)

Ok. I will wait for Ubuntu to releas the new  version of Firefox, so.

---

### Post by PriceChild on 2006-06-02
It will appear in the security repos soon....

Don't expect the future release of 2.0.0 to appear there though, that's why tehre's backports ;)

---

### Post by Hoffmann on 2006-06-02
> **PriceChild]It will appear in the security repos soon....

Don't expect the future release of 2.0.0 to appear there though, that's why tehre's backports  said:**
> 

You mentioned backports. I have a question to you. In order to install some programs (available just from backports), all I need to do is to add backport as following:
[QUOTE] On synaptic:
         1. Settings -> Repositories
         2. Click on Add and then Custom
         3. Paste the following four lines into the box and click Add Repository, one line at a time: 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
Is that correct? Or should I make any trick? I mean, ist it necessary to specify any program I want to upgrade?
Thanks!

---

### Post by garyng on 2006-06-02
just add the repositories and it is like installing any other packages.

---

### Post by dlpfmVfH on 2006-06-02
Why not use Swiftfox...
Swiftfox is an optimized firefox release,
You just unzip it in your home directory, and make a launcher on the gnome-panel

URL: [http://getswiftfox.com/](http://getswiftfox.com/)

---

### Post by garyng on 2006-06-02
[QUOTE=aboe]Why not use Swiftfox...
Swiftfox is an optimized firefox release,
You just unzip it in your home directory, and make a launcher on the gnome-panel

URL: [http://getswiftfox.com/](http://getswiftfox.com/)[/QUOTE]

I believe that is just personal preference. I won't do custom installation of any program unless it is absolutely necessary(and I haven't seen that case yet except for some development things in python). It can become a support mess. To me what is in ubuntu is already cutting edge enough, no need to chase around the latest, hottest.

---

### Post by dlpfmVfH on 2006-06-02
[quote=garyng]I believe that is just personal preference. I won't do custom installation of any program unless it is absolutely necessary(and I haven't seen that case yet except for some development things in python). It can become a support mess. To me what is in ubuntu is already cutting edge enough, no need to chase around the latest, hottest.[/quote]

That's true, I hope the devs, will update the firefox from the repositories,
and keep my swiftfox in my home-directory,
It doesn't interfere, it uses the same info and configs...

It is just a nice addition...and a little bit faster.

---

