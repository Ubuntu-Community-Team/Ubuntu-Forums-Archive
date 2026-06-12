---
title: "Trouble Reconfiguring xserver-xorg"
date: 2010-04-25
forum: General Help
---

### Post by gberg on 2010-04-25
Hi all, first post here.

I loaded ubuntu 9.10 last night for the first time, excited about using a new OS other than windows for the first time. I am dual booting with vista.

After loading ubuntu and finding everything running great, i downloaded updates to get everything up to speed, including drivers for my ati graphics card. I think this is where i've hit my first issue.

After restarting, the ubuntu splash screen shows, then it stops at a blank screen with only the "_" solid, not blinking, at the top of the screen. I've managed to follow the instructions provided here:

[http://kubuntuforums.net/forums/index.php?topic=3085112.msg80048#msg80048](http://kubuntuforums.net/forums/index.php?topic=3085112.msg80048#msg80048)

but only for so far. When i enter the line
```
sudo dpkg-reconfigure xserver-xorg
```it asks for my password, then returns to the standard prompt without going to the reconfigure screen i've seen in another forum post. In other words, i haven't managed to access the reconfigure screen.

Any ideas?

---

### Post by garyedwardjohnston on 2010-04-25
i run into this ALL TO OFTEN :(

pop in t6he live cd and reboot...select try without changes

open a terminal and

```
gksudo nautilus
```

navigate to etc/X11 and open xorg.conf

select everything and delete it to make it an empty file

restart and x will start with failsafe settings

as for properly configuring the xorg.conf file for use with your card, research, try, and when it fails follow these instructions again to recover from errors

good luck

ps  you might want to drop an email to ati and ask them for better linux support :)

---

### Post by mick222 on 2010-04-25
What card do you have it might just be a case of removing the ati drivers look in system admin hardware drivers and see if you can remove them there.Is it ubuntu or kubuntu you are using the link is to a kubuntu site.
If you really  want to configure xorg.conf and don't have one.
start in failsafe mode and go to the root shell option .
Type[PHP]sudo Xorg -configure[/PHP]
That will create an xorg.conf file called xorg.conf.new
[PHP]sudo mv /xorg.conf.new /etc/xorg.conf[/PHP]
the path to xorg.conf.new might be different from what I typed but it will tell you it in the terminal window.

---

### Post by gberg on 2010-04-25
Thanks!

I ended up booting in recovery mode and using nano to access the file. cleared it and it works now.

---

