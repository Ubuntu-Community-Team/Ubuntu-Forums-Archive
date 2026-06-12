---
title: "grism does not install on Ubuntu 11.10"
date: 2012-03-06
forum: General Help
---

### Post by donmarco5 on 2012-03-06
Hi.  I tried to install the current version of Grism, a stock portfolio program, on Ubuntu 11.10.  It could not install because a dependency was not satisfied - libglade2-ruby.  I used the update manager and it said my pc is up to date.  Grism has no problem installing on Ubuntu 10.04.  Is there a way to install libglade2-ruby on my pc before I install Grism?  Any help would be greatly appreciated.  Thank you.

---

### Post by latinlightning on 2012-03-06
Have you tried Synaptic Package Manager? I'm running 11.04 and when I use the Quick Filter option in Synaptic by typing "libglade2-ruby" it shows up immediately for me.

---

### Post by donmarco5 on 2012-03-06
[SIZE=3]Thank you for responding, latinlightning.  In Ubuntu 11.10, synaptic package manager is not installed automatically so I installed it.  After I updated it I put libglade2-ruby into quick report and nothing was listed.  I also tried installing libglade2-ruby with the terminal and it said it could not locate the package.  I do not understand why Ubuntu 10.04 installs grism effortlessly and Ubuntu 11.10 is making this such a problem.  Is it possible that I need to install a package that includes libglade2-ruby before I can install grism?[/SIZE]

---

### Post by raja.genupula on 2012-03-06
try ```
sudo apt-get install -f
```
whats it giving to you ? , please gives terminal code what you have did and what it give back .that will help us to understand .

---

### Post by Script Warlock on 2012-03-06
it's not possible yet to install grism on ubuntu 11.10/12.04 i have tried it many times but to no avail. sorry grism must be updated too since the last release was 2008 and outdated. check [this]("http://mygeekopinions.blogspot.com/2011/07/how-to-install-grism-stock-market.html") out

---

### Post by donmarco5 on 2012-03-06
[SIZE=3]Thank you Script Warlock for your reply.  I guess I will have to reinstall Ubuntu 10.04 so I can have ALL of my necessary programs working again.  I think its a shame that the newer version of Ubuntu can't do what an older version can.  Does anyone know of a stock portfolio program like Grism that works with Ubuntu 11.10?  Once again, I thank all of you for responding.[/SIZE]

---

