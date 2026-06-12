---
title: "Apt question"
date: 2011-09-16
forum: General Help
---

### Post by brendonsoh on 2011-09-16
Hello, I've been using Ubuntu since 7.04 and I've never really encountered this problem

I use firefox nightly (firefox-trunk) so after thats installed and set as my default browser, naturally I want to remove stable firefox, so I do apt-get remove firefox, however it tells me I must install Chromium, which I dont really want, is there anyway to remove firefox without installing Chromium?

---

### Post by gmargo on 2011-09-16
The probable reason is that your system has some package installed that depends on **firefox**.  Or, more likely, depends on a "provider" package such as **www-browser**.  The **www-browser** role can be fulfilled by a number of actual browsers like firefox and chromium-browser.

One way to ask the system why it thinks it needs firefox or chromium is with the **aptitude why** command; this result from my system says that sun-java6-plugin wants some browser:
```

$ aptitude why firefox
i   sun-java6-plugin Depends firefox | firefox-2 | iceweasel | mozilla-firefox | iceape-browser | mozilla-browser | epip
                             hany-gecko | epiphany-webkit | epiphany-browser | galeon | midbrowser | moblin-web-browser 
                             | xulrunner | xulrunner-1.9 | konqueror | chromium-browser | midori | google-chrome        

```So try running "**aptitude why firefox**" on your system to see what program wants it.

The ultimate solution will probably be to either (a) remove the dependent package, or (b) install an alternative www-browser package other than chromium (like lynx or links) just to satisfy the dependency.

---

### Post by brendonsoh on 2011-09-16
Cant I use firefox-trunk for that?

---

### Post by Blasphemist on 2011-09-16
> **brendonsoh said:**
> Cant I use firefox-trunk for that?
Yes, I'm sure you can but it's a chicken or egg thing in a way. I don't think you can have both firefox's at the same time. And you can't uninstall one without having something fullfilling the requirement. 

Install Chromium, uninstall existing firefox, install new firefox, remove chromium if you want.

---

### Post by gmargo on 2011-09-16
> **brendonsoh said:**
> Cant I use firefox-trunk for that?
Can't say without knowing where you're getting "firefox-trunk" from or how it's packaged.

---

