---
title: "Removing Chromium from Lubuntu"
date: 2012-09-21
forum: General Help
---

### Post by vasa1 on 2012-09-21
Normally, *sudo apt-get purge app_name* suffices to remove a package (provided it isn't going to break something).

However, Lubuntu users who try to remove the Chromium browser from their system must ensure that there is at least one other browser present before Chromium can be removed. This is because of Debian's [www-browser requirement]("http://packages.ubuntu.com/precise/www-browser") which I read about in an [askubuntu QnA]("http://askubuntu.com/a/127833/25656").
In other words, not just any other browser, but a browser from the list in the link above should be present in order to be able to purge Chromium without being forced to install something else.
This is where things get a bit confusing.
I have the following browsers installed and fully functional:
Chromium (as part of the lubuntu desktop);
Google Chrome 21 (from Google's ppa);
Firefox 16 (beta; direct from Mozilla; not from the USC or from any ppa);
Midori 0.46 (from its Launchpad ppa because the USC version is older);
and
Seamonkey 2.12 from [seamonkey.org]("http://www.seamonkey-project.org/releases/seamonkey2.12/")
Yet, when I tried to uninstall Chromium which is now at version 20, the condition imposed was that Firefox be installed in its place.

I then looked at the list of www-browsers. I installed **dillo** from the Lubuntu Software Center. Ran sudo apt-get update and then tried to purge Chromium. No go. apt-get still wanted to install Firefox. Same with **E-links**. When I installed Epiphany, I could successfully uninstall Chromium without being prompted to install Firefox in its place.

(I feel that apt-get (or the system as a whole) didn't **see** my existing Firefox because I installed it in my home directory.)

Also, although I've mentioned Lubuntu, the same situation may be encountered in other *buntu flavors when one tries to remove the browser that comes supplied with the distro.

BTW, there's a bug marked "invalid" [here]("https://bugs.launchpad.net/apt/+bug/1022244").

---

### Post by vasa1 on 2012-10-08
Just to mention that I had no difficulty removing Chromium from Lubuntu 12.10. I installed Chrome via Google's ppa first. (But I had done the same thing with 12.04 and had the issue of *the system* wanting to install Firefox in place of Chromium.)

---

