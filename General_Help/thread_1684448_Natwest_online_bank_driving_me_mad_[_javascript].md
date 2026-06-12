---
title: "Natwest online bank driving me mad [ javascript]"
date: 2011-02-09
forum: General Help
---

### Post by SlugSlug on 2011-02-09
Hi all,

Can anyone help? It seems all aspects of Java & JavaScript work ok in Firefox apart from Natwest Banking.

I am on about the part where you click account to see last 5 transactions ~ mine wont drop down to show me. 

This also fails to work in chromium-browser.

Can anyone help?  I've tried a load of java installs.

---

### Post by SlugSlug on 2011-02-10
Lts 10.04
ff 3.6.13

---

### Post by coldraven on 2011-02-10
I'm only guessing here. Try installing the "User Agent Switcher" add-on in Firefox.
[https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/?src=api](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/?src=api)
Change your user agent to Internet Explorer and see if that works.

---

### Post by gandaran on 2011-02-10
> **SlugSlug said:**
> Hi all,

Can anyone help? It seems all aspects of Java & JavaScript work ok in Firefox apart from Natwest Banking.

I am on about the part where you click account to see last 5 transactions ~ mine wont drop down to show me. 

This also fails to work in chromium-browser.

Can anyone help?  I've tried a load of java installs.
which java plugin do you have installed, sun-java or the open-java icedtea?

---

### Post by cipherboy_loc on 2011-02-10
In firefox, go to `about:plugins` (type that into the address bar) to show you what plugins you have installed. It could be that you don't have the java plugin linked correctly. BTW, did you  install through apt-get or the Java tarball?



Cipherboy

---

### Post by SlugSlug on 2011-02-10
I've been installing diffrent java's via apt-get I  am now on ice tea

---

### Post by SlugSlug on 2011-02-10
about : plugins attached

---

### Post by SlugSlug on 2011-02-14
If I start firefox with a new profile `about: plugins` crashes FF & so does the natwest site

---

### Post by stinkeye on 2011-02-14
Install Sun Java
[**_[COLOR="DarkRed"]http://sites.google.com/site/easylinuxtipsproject/java[/COLOR]_**]("http://sites.google.com/site/easylinuxtipsproject/java")

---

### Post by SlugSlug on 2011-02-14
deleted cookies & firefox -safe-mode   reset everything and its working again

---

### Post by SlugSlug on 2011-02-15
for anyone else who has this - am not sure why but it's flash that screws it up 

uninstall adobe flash plugin and install the swfdec plugin

---

