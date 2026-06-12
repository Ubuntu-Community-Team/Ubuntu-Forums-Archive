---
title: "openbox + gnome in lucid -&gt; fail"
date: 2010-05-04
forum: General Help
---

### Post by Hugo Alvarado on 2010-05-04
Hi,  I have been using openbox as my window manager in gnome, along with xcompmgr in jaunty and karmic.

I used to simply add these commands in "Startup Applications":

openbox --replace&
xcompmgr -c -t-5 -l-5 -r4.2 -o.55 &

each one in a separate entry...but it is not working on lucid. I have disabled compiz, and if I run them on a terminal, they work - openbox becomes the wdm (replaces metacity) and xcompmgr runs fine. 

How can I get them to autostart?

Thanks.

---

### Post by kerry_s on 2010-05-04
you don't need to add "&" on the end.
in fact i don't even think you need to add the startup.
have you tried doing your changes using alt+f2 then saving the session in the startup advanced tab? 
(hope i remember right, been awhile since used gnome, application wording might be wrong)

---

### Post by Hugo Alvarado on 2010-05-05
Thanks, I tried your suggestion, system->preferences->startup applications->options tab then hit the button "remember currently running applications" now openbox and xcompmgr start up every time.

---

