---
title: "Google Chrome vs Chromium"
date: 2010-09-07
forum: General Help
---

### Post by kellyapproved on 2010-09-07
I see in the Ubuntu Software Centre, you can download Chromium Web Browser.

I've read the about on it and see that it is an open source browser, but what would be the advantage of installing this over downloading Google Chrome from the Chrome website?

---

### Post by SmokeyThePanda on 2010-09-07
The advantage is that it has no branding. Google Chrome is branded to Google. Chromium isn't. Besides, Chromium was built natively for Linux, I believe. Always go with the native programs if possible. Especially if they are in your repos.

---

### Post by Dayofswords on 2010-09-07
chromium, i believe, is just chrome minus branding, logo and flash integration

---

### Post by juil on 2010-09-07
Chromium has build updates every hour and is an open source project, while Google Chrome is the brand based on it.

---

### Post by Sef on 2010-09-07
> Chromium has build updates every hour and is an open source project, while Google Chrome is the brand based on it.


In general, apps from the repositories are not upgraded beyond security patches, if they are supported by Ubuntu.  If the [Chromium PPA]("https://launchpad.net/~chromium-daily/+archive/ppa") is chosen, then upgrades daily will be done.

---

### Post by kellyapproved on 2010-09-08
> **Sef said:**
> In general, apps from the repositories are not upgraded beyond security patches, if they are supported by Ubuntu.  If the [Chromium PPA]("https://launchpad.net/%7Echromium-daily/+archive/ppa") is chosen, then upgrades daily will be done.

I'm not sure what version Chrome is available from the Google website, but for arguments sake, lets say version 3 is the most current version.

Does that mean that the version in the repository will always be version 3 even if lets say version 3.5 comes out some day?

Wouldn't that also mean that it is better to install Chrome from the Google website rather then the Repository?

Thanks

---

### Post by tgalati4 on 2010-09-08
I was under the impression that Chrome is the stable base and Chromium is the leading/bleeding edge.  You would normally want Chrome, as it should be more stable.  Chromium is the development framework where new stuff gets tested.  After a few months, the stable code gets rolled into an updated Chrome.

On my Jaunty and Intrepid machines, I recently upgraded my Chrome from 5.0.X to 6.0.472.55.  That would normally be a major change, but both seem to work fine.  Flash video playback from [http://amctv.com](http://amctv.com) seems relatively smooth and the html5 effects on [http://www.google.com](http://www.google.com) (buckeyball and color blind dots) seem to work without issue.

---

### Post by wojox on 2010-09-08
[Chrome Versus Chromium ]("http://www.google.com/support/forum/p/Chrome/thread?tid=380b7ffc5d845696&hl=en")

---

### Post by kellyapproved on 2010-09-08
> **wojox said:**
> [Chrome Versus Chromium ]("http://www.google.com/support/forum/p/Chrome/thread?tid=380b7ffc5d845696&hl=en")

Thanks for the link.  It looks like what I really want is Google Chrome, stable and mainstream.

However, if a new version of Chrome becomes available, how would an Ubuntu user find out about it?

With Internet Explorer, when a flaw is found, Microsoft patches it with updates usually available on a Tuesday and it's automated.  Is there something similar with Chrome and Ubuntu or as a user, am I on my own with this browser?

---

### Post by pastalavista on 2010-09-08
> **kellyapproved said:**
> Thanks for the link.  It looks like what I really want is Google Chrome, stable and mainstream.

However, if a new version of Chrome becomes available, how would an Ubuntu user find out about it?

With Internet Explorer, when a flaw is found, Microsoft patches it with updates usually available on a Tuesday and it's automated.  Is there something similar with Chrome and Ubuntu or as a user, am I on my own with this browser?

Basically to install Chrome, you add the google ppa to your repositories and it's updated as soon as the update is released via the Ubuntu Update Manager. Chromium is already in the repos.

---

### Post by wojox on 2010-09-08
Go here and [Now available for Linux]("http://www.google.com/chrome/index.html?hl=en&brand=CHMA&utm_campaign=en&utm_source=en-ha-na-us-bk&utm_medium=ha") and choose Ubuntu 32 or 64 bit. This will keep it up to date for you by adding the Google repository.

---

### Post by kellyapproved on 2010-09-08
> **wojox said:**
> Go here and [Now available for Linux]("http://www.google.com/chrome/index.html?hl=en&brand=CHMA&utm_campaign=en&utm_source=en-ha-na-us-bk&utm_medium=ha") and choose Ubuntu 32 or 64 bit. This will keep it up to date for you by adding the Google repository.

Thank you.  I tried to install Google Chrome under a user account, gave admin permission, but it came up with an error message about being unable to find an installer.

I then logged in using the admin account and was able to install Google Chrome without any problems.  Under applications=>internet, I also see Google Chrome listed.

When I log back into my user account, the icon for Google Chrome is not in applications=>internet.  How would I access it under the user account?

Sorry for all the questions, this is really the first true attempt at installing/using Linux that I am undertaking.

---

### Post by kellyapproved on 2010-09-08
I guess I found my solution for using Google Chrome under the user account.  I found that you can use the create launcher to make a shortcut which pointed to the Chrome executable.  This seems to have worked for me.

> **kellyapproved said:**
> Thank you.  I tried to install Google Chrome under a user account, gave admin permission, but it came up with an error message about being unable to find an installer.

I then logged in using the admin account and was able to install Google Chrome without any problems.  Under applications=>internet, I also see Google Chrome listed.

When I log back into my user account, the icon for Google Chrome is not in applications=>internet.  How would I access it under the user account?

Sorry for all the questions, this is really the first true attempt at installing/using Linux that I am undertaking.

---

### Post by bbqsandwich on 2010-09-08
Another difference is that Google Chrome sends some information about your browser usage to Google, which could be a privacy concern for some:

[http://en.wikipedia.org/wiki/Google_chrome#Usage_tracking](http://en.wikipedia.org/wiki/Google_chrome#Usage_tracking)

---

