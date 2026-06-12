---
title: "Eclipse ADT plugin not working"
date: 2009-12-10
forum: General Help
---

### Post by killa.fr0gg on 2009-12-10
I am trying to get my system back up and running for Android development after switching to Ubuntu from OS X, but I cannot seem to install the ADT plugin. Each time I try, it tells me I am missing packages, but there's nothing for me to install! I have only been able to find things on the internet that express the same problems as mine, but no solutions. has anyone been able to set up this environment in 9.10?

Thank you very kindly for your help.

---

### Post by killa.fr0gg on 2009-12-12
bump. Is that considered rude? If it is I'm sorry.

---

### Post by nielsh on 2009-12-13
If you follow the instructions [here]("http://groups.google.com/group/android-beginners/msg/70625c22a2f82d89") then you should have a working Android development platform.

---

### Post by mIXpRo on 2009-12-13
check out the latest eclipse 3.5  [http://johnpaulett.com/2009/06/26/install-eclipse-galileo-3-5-on-ubuntu-jaunty/](http://johnpaulett.com/2009/06/26/install-eclipse-galileo-3-5-on-ubuntu-jaunty/)  it's written for jaunty but works on any ubuntu  


after that go to  help->install new software 
then you should see a window with a list of site to download from them "add ones" for eclipse , select all then next
now search in the new window for the plugin you wish and install it

---

### Post by Queue29 on 2009-12-13
The Eclipse bundled with Ubuntu does not include many of the things required by ADT, and it is a HUGE PITA to install those dependencies. You need to download either Eclipse Classic or Eclipse for Java Developers (classic is best- it includes everything) off of the website and use that. Sorry.

None of the above posters have actually done this, or they would know that.

---

### Post by WelterPelter on 2009-12-22
You know, ADT was working fine until this last update (0.9.5). Now it doesn't show up anywhere. 

Anyone else having this trouble?

---

### Post by killa.fr0gg on 2009-12-23
Nothing works. I give up, I have to change OSes. Thank you all for trying.

---

### Post by jstgtpaid on 2010-01-04
**Queue29's** suggestion worked for me.  I completely uninstalled the ubuntu version of eclipse and installed the 'classic' version from the install site.

If you follow the instructions at this site **[http://developer.android.com/sdk/installing.html]("http://developer.android.com/sdk/installing.html")** you should be all good.

However, I noticed I had a mouse click issue in eclipse, so I followed the instructions at this site **[http://wobiny.wordpress.com/2009/11/11/eclipse-mouse-click-problem-in-ubuntu-9-10/]("http://wobiny.wordpress.com/2009/11/11/eclipse-mouse-click-problem-in-ubuntu-9-10/")** to resolve that issue.

Now, everything is working peachy...

---

### Post by killa.fr0gg on 2010-07-18
This is old, but just to make sure the issue has an answer, this his been fixed in !0.04. Wonderful!

---

