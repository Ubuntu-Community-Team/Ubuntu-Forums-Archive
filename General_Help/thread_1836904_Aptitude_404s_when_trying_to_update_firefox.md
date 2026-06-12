---
title: "Aptitude 404s when trying to update firefox"
date: 2011-08-31
forum: General Help
---

### Post by AzureRaptor on 2011-08-31
Nearly-pristine install of natty, amd64, no unusual repositories, all other things working great, kudos to devs for this version!

The following problem just started today - normally the command:

```

sudo aptitude update && sudo aptitude full-upgrade

```works just fine, fetches all the updates, & lets me see what's available to update/upgrade today.

But today, I got:

```

The following packages will be upgraded:
  firefox firefox-globalmenu firefox-gnome-support firefox-locale-en
The following packages are RECOMMENDED but will NOT be installed:
  ubufox xul-ext-ubufox
4 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 17.9 MB of archives. After unpacking 8,192 B will be freed.
Do you want to continue? [Y/n/?] Y
Err http://security.ubuntu.com/ubuntu/ natty-security/main firefox-globalmenu amd64 6.0.1+build1+nobinonly-0ubuntu0.11.04.1
  404  Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com/ubuntu/ natty-security/main firefox amd64 6.0.1+build1+nobinonly-0ubuntu0.11.04.1
  404  Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com/ubuntu/ natty-security/main firefox-gnome-support amd64 6.0.1+build1+nobinonly-0ubuntu0.11.04.1
  404  Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com/ubuntu/ natty-security/main firefox-locale-en all 6.0.1+build1+nobinonly-0ubuntu0.11.04.1
  404  Not Found [IP: 91.189.92.167 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-globalmenu_6.0.1+build1+nobinonly-0ubuntu0.11.04.1_amd64.deb: 404  Not Found [IP: 91.189.92.167 80]


```Any ideas?  Does anybody know if the servers are having a problem right now?  I can ping that address from the target box just fine, and when I go to that web address, things seem to be there...?

---

### Post by AzureRaptor on 2011-08-31
Ok, this is embarrassing.  I need to take a few deep breaths and not panic before I post.  :}  The last time I tried the command was about 10 min. before I posted; it'd failed about 4 times in a row.

It's working fine now, of course.  :redface:  Thank you all for your time.

---

