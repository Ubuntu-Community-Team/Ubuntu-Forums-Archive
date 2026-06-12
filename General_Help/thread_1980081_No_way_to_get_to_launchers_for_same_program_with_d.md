---
title: "No way to get to launchers for same program with different options"
date: 2012-05-14
forum: General Help
---

### Post by allauthors on 2012-05-14
I have two instances of chrome (chromium-browser) one which is run in "app mode" with the --app="internal internet web-application URL" and one without for regular browsing.  The problem is that whichever one I pin to the dashbar first the other one will just open up as a second instance (second little arrow)... I really want to be able to have them both quick-launch-able.   The command line parameters do make them two completely different logical app.  

I tried soft and hard linking a different command name to the /usr/bin/chromium-browser binary, but it still detects and keeps them together.

Does anyone have any suggestion how to get both on the bar?

Ubuntu 12.04 Precise

---

### Post by HiImTye on 2012-05-14
[http://askubuntu.com/questions/35488/what-custom-launchers-and-unity-quicklists-are-available](http://askubuntu.com/questions/35488/what-custom-launchers-and-unity-quicklists-are-available)

alternately, you can go to 'edit menus' and then add another launcher, with different options, and add that to the bar

---

### Post by allauthors on 2012-05-14
The linked answer allows one to create the right-click menu options for the app from the single icon but still keeps it all together as the one icon (and adds a click to launch).  Using Edit Menu will add a separate launcher to the Dash interface itself, but when you try to add it to the sidebar, it only lets you add one or the other but not both. 

 I'm looking for a way to have both "commands" as completely separate icons on the main dock/sidebar/whatever-we-call-it-these-days.  

I already have both as separate menu items which can be launched by typing their different name from the dash home. but despite the separate launchers, once launch they occupy only a single spot on the sidebar/dock when I want them to occupy two so that I can pin them both separately.  Any options for that?

---

### Post by HiImTye on 2012-05-14
I see what you're talking about, you could try manually setting the class of one of the windows, that might force it to use a separate slot on the bar

---

