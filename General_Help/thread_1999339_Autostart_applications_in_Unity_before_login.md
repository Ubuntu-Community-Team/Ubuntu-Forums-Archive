---
title: "Autostart applications in Unity before login"
date: 2012-06-07
forum: General Help
---

### Post by yesmat on 2012-06-07
Hi All,

I am running Ubuntu 12.04 desktop with all default installation and all is running well.

I have installed a remote support application "Teamviewer7", which allows me to remote into my desktop from office. I set up the application to autostart, but it only starts after login, not before.

Because the application only starts after I login, this means that if i have to remotely reboot my desktop PC, I can't regain access again untill i get home and login again.

There must be a way to get Teamviewer to start (as a service, by windows terminology) _before _login.

I imagine I would have to edit/add a script under /usr/share/applications or possibly under /etc/xdg/autostart

I am not sure which directory would apply in this scenario and what script do I need to add?

Your feedback is highly appreciated

Thanks

---

### Post by mikewhatever on 2012-06-07
...is turning autologin on an option? I very much doubt Teamviewer was designed to run as service, but perhaps I am wrong.

---

### Post by yesmat on 2012-06-08
wouldn't want to do that, the PC is located in a semi public area and wouldn't want to turn that feature on.

I guess this is nothing to do with what application we are talking about. I was thinking that there must be a way to get the Ubuntu machine to run the app before login.

But then again may be you are right, possibly Teamviewer is not designed to do that, but in saying that I would like to know how to enable an application to start before login anyway, only then i give it a try.

---

