---
title: "Can't login to ubuntu"
date: 2012-09-29
forum: General Help
---

### Post by firekage on 2012-09-29
Hi. I would like to ask again for your precious help. I run Ubuntu 12.04 with nvidia GTX260.

I wanted to have autologin so i enabled it. Also i wanted to block my  session right after login to Ubuntu so in start apps i entered

```
gnome-screensaver-command -l
```and after this i rebooted my  machine...but right now there is problem with login to Ubuntu. I though  that after booting up it blocks my system/screen and when i want again  to log than it would ask for my password but it doesen't. My system  start up, booting but when it should have entered gui mode it hungs up  right at this:


[http://imageshack.us/a/img803/4061/dsc00366resized.jpg]("http://imageshack.us/photo/my-images/803/dsc00366resized.jpg/")

Uploaded with [ImageShack.us]("http://imageshack.us")

(Don't look at the bottom line with gnome-screensaver-command -d because i tough that i would gain acces if i enter it) 

I did some things to revert it back, but it didn't help, as a root i:

-in /etc/lightdm deleted lightdm.conf;
-reconfigured lightdm with sudo dpkg-recofigure lightdm;
-deleted gnome-screensaver-command.desktop from ~/config./autostart;

but it still stops at this. Is there a way to fix it?
[URL="http://imageshack.us/photo/my-images/803/dsc00366resized.jpg/"][IMG]http://imageshack.us/a/img803/4061/dsc00366resized.jpg</a>[/IMG]
[/URL]

---

### Post by firekage on 2012-09-30
I see that this topic is too tough for us ;)...

---

