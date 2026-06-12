---
title: "Can't Save file"
date: 2010-03-13
forum: General Help
---

### Post by daldude on 2010-03-13
When I try to save a file that I have edited using gedit I get a error 
Could not save the file /etc/pwrstatd.conf.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

Is this something to do with not being logged on as root? If so how do I log on as Root or edit the file as a root user?

---

### Post by howefield on 2010-03-13
Try opening the file with elevated rights, eg

```
gksudo gedit /etc/pwrstatd.conf
```

Then edit and save.

---

### Post by daldude on 2010-03-13
Thanks for the info but I found a easier way on the 
**12 frequently asked questions**




**[SIZE=3][COLOR=#000000][B]How can I open a file manager with root authority (omnipotence)?**[/COLOR][/SIZE][/B]

[SIZE=3]9. Applications - Accessories - Terminal

Type: [COLOR=#0000ff]gksudo nautilus[/COLOR][/SIZE]



after editing the file I rebooted because I was not sure if my system was then in a root user access mode. If I close the file browser that came up  and terminal window used to type the command when I used the gksudo nautilus will that also disable root user access to my system?

:D

---

### Post by Enigmapond on 2010-03-13
> **daldude said:**
> Thanks for the info but I found a easier way on the 
**12 frequently asked questions**




**[SIZE=3][COLOR=#000000][B]How can I open a file manager with root authority (omnipotence)?**[/COLOR][/SIZE][/B]

[SIZE=3]9. Applications - Accessories - Terminal

Type: [COLOR=#0000ff]gksudo nautilus[/COLOR][/SIZE]



after editing the file I rebooted because I was not sure if my system was then in a root user access mode. If I close the file browser that came up  and terminal window used to type the command when I used the gksudo nautilus will that also disable root user access to my system?

:D

Yes, once the browser is closed, so is root access.

---

### Post by howefield on 2010-03-13
> **daldude said:**
> after editing the file I rebooted because I was not sure if my system was then in a root user access mode. 

Yes, rebooting is so much easier than entering a command in the terminal. ;-)

> If I close the file browser that came up  and terminal window used to type the command when I used the gksudo nautilus will that also disable root user access to my system?

Whichever way you do it, you'll not remain as root once you close the file or nautilus window.

---

