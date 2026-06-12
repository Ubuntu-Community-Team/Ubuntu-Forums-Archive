---
title: "Trouble installing video driver"
date: 2009-10-21
forum: General Help
---

### Post by Xotol on 2009-10-21
[SIZE=1]Hello -[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]I am new to Ubuntu (9.04 - jaunty), and am trying to install a video driver - VIA Xorg. I downloaded the .tgz file from the website, mounted the src file, and tried to follow instructions on a "read me" file. Thus:[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]**************************[/SIZE]
[SIZE=1]How to compile the VIA Xorg driver[/SIZE]
[SIZE=1] [/SIZE]
[LIST]
[*][SIZE=1]Check to make XServer your current working directory.[/SIZE]
[*][SIZE=1]Generate configure file automatically, enter[/SIZE]
[/LIST][SIZE=1]                         chmod +x autogen.sh[/SIZE]
[SIZE=1]                         ./autogen.sh[/SIZE]
[SIZE=1] [/SIZE]
[LIST]
[*][SIZE=1]Compile VIA Xorg driver, enter[/SIZE]
[/LIST][SIZE=1]                   make[/SIZE]
[SIZE=1][/SIZE]
[SIZE=1] [/SIZE]
[LIST]
[*][SIZE=1]Install VIA Xorg driver, enter[/SIZE]
[/LIST][SIZE=1]                     make install [/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]The driver will be installed into /usr/lib/xorg/modules/drivers[/SIZE]
[SIZE=1][SIZE=1]****************************[/SIZE]
At step #3, I get this error displayed in the terminal window. 
[SIZE=1]make: *** No targets specified and no makefile found. Stop.[/SIZE]
 
At step #4, I get this error.
make: *** No rule to make target ‘install’. Stop.
 
Someone suggested I "add it to the repository" but I'm not sure how to do that. I'm thinking installing a video driver shouldn't be so hard. What am I doing wrong?
 
Thanks!
[/SIZE]

---

### Post by Woody1987 on 2009-10-21
in a terminal run
```
sudo apt-get install xserver-xorg-video-openchrome
```

That will install the driver for you. although im pretty sure it is installed automatically when you install ubuntu.

---

