---
title: "a how to send mailto links to webmail 11.10"
date: 2012-01-06
forum: General Help
---

### Post by sdowney717 on 2012-01-06
install the 'desktop-webmail' package
run this package, found in internet and select one of the providers

(I run gnome shell, so I assume unity is similar)

**NOTE:** 
Now you *_might_* have to setup thunderbird (even with bogus names) to get the next part to show up, I DID. Until then, the system info for default mail never listed 'desktop webmail' as a selectable option.

then goto default applications found in system info
set the default mail to desktop-webmail instead of thunderbird or evolution
 
I run chrome and I also installed the mailto extension and set it to my webmail

some various screen shots along the way.

[https://chrome.google.com/webstore/search/mailto](https://chrome.google.com/webstore/search/mailto)

I also updated desktop-webmail package to version 003 by following this link.
[https://bugs.launchpad.net/ubuntu/+source/desktop-webmail/+bug/754321](https://bugs.launchpad.net/ubuntu/+source/desktop-webmail/+bug/754321)

> if you dont know how, use this:

 sudo add-apt-repository ppa:asac/sandbox
 sudo apt-get update
 sudo apt-get install desktop-webmail

verify that you use a 003 based version using:
 dpkg -l desktop-webmail

So now when I click on a mailto link, it loads the webmail page instead.

---

### Post by sdowney717 on 2012-01-06
this system info now shows desktop web mail instead of thunderbird

---

