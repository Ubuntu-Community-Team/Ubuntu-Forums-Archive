---
title: "Chrome not installing for each user"
date: 2010-09-03
forum: General Help
---

### Post by NertSkull on 2010-09-03
Title says it all really.  I've installed chrome (tried both the stable and beta channels) but after it installs I can't find it for each user.

I have 5 different users and it will install for some of them but not all.

What am I doing wrong?

---

### Post by sikander3786 on 2010-09-03
What is the source of installation? Repositories or custom downloaded files? Whenever I install something from the repositories, it is installed for all users.

---

### Post by NertSkull on 2010-09-03
When I try the stable channel I used this one

[http://www.google.com/chrome/eula.html?hl=en&hl=en&platform=linux](http://www.google.com/chrome/eula.html?hl=en&hl=en&platform=linux)
(which is a redirect from here --> [http://www.google.com/chrome/intl/en/landing_chrome.html?hl=en&platform=linux](http://www.google.com/chrome/intl/en/landing_chrome.html?hl=en&platform=linux))

And when I tried the beta channel it was from here
[http://www.chromium.org/getting-involved/dev-channel](http://www.chromium.org/getting-involved/dev-channel)

and down near the bottom it has the subscribe to a channel link, and I did the google chrome beta for ubuntu (for 32-bit and 64-bit systems)

I thought those added them to the repositories, but maybe not. But both ways did not make it show up for all users.  So how do I add them as repositories?

---

### Post by Smart Viking on 2010-09-03
chromium is already in the repos, to install it:
```
sudo apt-get install chromium-browser
```

---

### Post by sikander3786 on 2010-09-03
Install Chrome as suggested by Smart Viking. You have been around Ubuntu for quite some time still I will like to remind you that installing software from the repositories (Software Center, Synaptic or APT-GET) is always beneficial due to its compatibility, stability and automatic update capabilities.

---

### Post by NertSkull on 2010-09-03
well I feel kind of foolish and like I've been chastised, but rightly so

I should have looked first to see if it was already in the repositories.  When I get home from work I'll try again, it'll probably work.  

thanks all

---

