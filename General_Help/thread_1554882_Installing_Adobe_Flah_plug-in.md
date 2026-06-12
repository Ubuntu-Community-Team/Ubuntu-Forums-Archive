---
title: "Installing Adobe Flah plug-in"
date: 2010-08-17
forum: General Help
---

### Post by mdrushal on 2010-08-17
I am a 'newbie' to ubuntu (with 45+ years as a 'computer nerd'). I am trying to follow the instructions for installing the Flash plug-in so I can view some of the action on web pages. I get on terminal and the prompt is [EMAIL="mike@mike-laptop"]mike@mike-laptop[/EMAIL]
The instructions say to key in "# rpm -Uvh <rpm_package_file>"
I have tried as many variations of this command as I can think of with no response.
I am assuming that my interpretation of <rpm_package_file> is incorrect. Any and all assistance will be appreciated.

---

### Post by Spice Weasel on 2010-08-17
You don't need to install using the .rpm, it's much easier to just use the [.deb]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10.1_for_Linux_%28.deb%29").

Or even better, type this into your terminal:

> sudo apt-get install ubuntu-restricted-extras flashplugin-nonfree

---

### Post by mdrushal on 2010-08-17
Thanks.  All is well.

---

