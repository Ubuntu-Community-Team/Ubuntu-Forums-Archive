---
title: "Browser open on specific desktop?"
date: 2010-09-03
forum: General Help
---

### Post by zootoxin on 2010-09-03
Good Morning All, 

Just wondering if it would be possible to open firefox maximised + f11 on desktop number 2 of 4 when ever I boot up ubuntu 10.04

I only have a small screen and when ever I boot I go to desktop 2 open firefox and press f11 then leave it like that the whole time. 

So it would be sweet if I could have it there as default. 

Thanks

Zoot

---

### Post by mendhak on 2010-09-03
Interesting question.  For the full screen bit, I don't think there's an FF commandline option to start it full screen, but you can get an add-on called Full FullScreen

[https://addons.mozilla.org/en-US/firefox/addon/1568/](https://addons.mozilla.org/en-US/firefox/addon/1568/)

In its options, set it to be fullscreen on startup.  


Next, you could get [devilspie](http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/) and set FF to 'default' to workspace 2.  

Finally, create a startup script which simply launches firefox.

---

### Post by prshah on 2010-09-03
> **zootoxin said:**
> if it would be possible to open firefox maximised + f11 on desktop number 2 of 4 when ever I boot up ubuntu 10.04

If you are using Compiz, you can use the "Place Windows" plugin. System-Preferences-CompiConfig Settings Manager-Place Windows-Fixed Window Placement.

---

### Post by zootoxin on 2010-09-03
Hi guys, 

Thanks for the input. :)

Works like a charm using the addon and compiz 

Thanks again 

PS. Anyway to get google to sign in automatically?

---

### Post by lovinglinux on 2010-09-03
> **zootoxin said:**
> PS. Anyway to get google to sign in automatically?

Use [Secure Login]("https://addons.mozilla.org/en-US/firefox/addon/4429/") extension. It has an option that allows to create special bookmarks, which has a site specific identifying code, which triggers the auto-login. You can add this bookmark to your home page.

---

### Post by gldearman on 2010-09-03
> **mendhak said:**
> Interesting question.  For the full screen bit, I don't think there's an FF commandline option to start it full screen, but you can get an add-on called Full FullScreen

[https://addons.mozilla.org/en-US/firefox/addon/1568/](https://addons.mozilla.org/en-US/firefox/addon/1568/)

In its options, set it to be fullscreen on startup.

mendhak, thank you so much!  I have been looking for an app to do this, and this works perfectly.

---

