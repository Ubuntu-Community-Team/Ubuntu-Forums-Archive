---
title: "Monitor brightness"
date: 2012-08-02
forum: General Help
---

### Post by govind.abs on 2012-08-02
Dear friends,

im pretty new to ubuntu and currently using version 12.I use a samsung laptop.
I have started ignoring windows seven.But the only problem with ubuntu is that the [COLOR=Blue]**screen brightness is always reset to the maximum**[/COLOR] whenever i start ubuntu[COLOR=Blue].**I have to decrease it manually every time when i log in**.[/COLOR]The function keys to manage screen brightness also fails to decrease the backlight.Its always set high.So What could be the problem?.What should i do to over come this situation.

Somebody help me to solve this issue.

I would like to continue using ubuntu once i solve this issue.

Thanks in advance..

---

### Post by itagomo on 2012-08-02
have you looked here:

[http://www.cebuntu.com/how-to/how-set-brightness-on-startup-ubuntu-12-04/](http://www.cebuntu.com/how-to/how-set-brightness-on-startup-ubuntu-12-04/)

pasted the steps here:

1. Create a file in /etc/init.d/file_name,
**    sudo nano /etc/init.d/file_name**
2. Copy and paste the code below and save.
**    setpci -s 00:02.0 F4.B=50**
3. Now lets set some permissions.
**    sudo chown 755 /etc/init.d/file_name**
4. We want the script to run on boot up.
**    sudo update-rc.d file_name defaults**
Now restart your Ubuntu and the script we created will run on boot-up automatically.

---

