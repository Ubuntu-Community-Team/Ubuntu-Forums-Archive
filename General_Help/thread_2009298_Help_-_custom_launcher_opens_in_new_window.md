---
title: "Help - custom launcher opens in new window"
date: 2012-06-24
forum: General Help
---

### Post by joehc on 2012-06-24
Hey guys

I have made a custom launcer to the website hypem.com on my unity sidebar. It works great. However, when I click on the icon, it opens the website, but in another window with no icon in the sidebar. How do I make it open in the same windows as the icon I'm clicking on? Maybe the image will explain it better..
[IMG]http://img577.imageshack.us/img577/9684/screenshotakk.jpg[/IMG]

My code for the custom launcher is this:

```

[Desktop Entry]
Name=Hypem
Comment=
Exec=/opt/google/chrome/google-chrome --app=http://hypem.com/popular/lastweek/1
Icon=/usr/share/applications/hypem-iphone.jpg
Terminal=false
Type=Application
StartupNotify=true

```

---

### Post by blackflame2996 on 2012-06-24
the window is probably listed as Google chrome. use the launcher icon, then click see if the Google chrome launcher controls the window.

---

### Post by joehc on 2012-06-25
> **blackflame2996 said:**
> the window is probably listed as Google chrome. use the launcher icon, then click see if the Google chrome launcher controls the window.

Will do, thanks for your help

---

