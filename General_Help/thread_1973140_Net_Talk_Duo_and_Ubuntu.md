---
title: "Net Talk Duo and Ubuntu"
date: 2012-05-04
forum: General Help
---

### Post by debiantu on 2012-05-04
Hello all,

I'm currently using Ubuntu 12.04 and would like to plug in my net talk Duo into the USB port of the Ubuntu computer.

Does anyone know how to do this?  I was able to do it with a Windows computer by downloading the drivers from:

[http://faq.nettalk.com/index.php?_m=downloads&_a=viewdownload&downloaditemid=53&nav=0,2](http://faq.nettalk.com/index.php?_m=downloads&_a=viewdownload&downloaditemid=53&nav=0,2)

So how does one do it under Ubuntu?

thanks!

---

### Post by masgad on 2013-03-02
I managed to install nettalk Duo on Ubuntu 12.04 as follows: (I am using the classic gnome)
1- install wine: ```
sudo apt-get install wine
```
2- download [COLOR=#000000][FONT=Nazli]DUO USB Driver (Windows 32/64-bit) from [/FONT][/COLOR][http://www.nettalk.com/en/downloads](http://www.nettalk.com/en/downloads)
(The version that I used is the latest at time of writing: [COLOR=#000000][FONT=Nazli]version 1.34[/FONT][/COLOR])
3- install the downloaded driver: right click on it and select "open with wine..."
4- Create a new wired network connection 
        a- click on the network icon  on the top panel, then select edit connection, then add
        b- in the wired tab, set the MAC address as shown on the bottom of your nettalk (or connect it to your computer USB port and run ifconfig in the terminal)
        c- in "IP4 settings", set the "method" to "shared to other computers"
        d- save
5- from the "Applications" menu on the top panel, select "Wine"->"Programs"->"NetTalk"
6- click the phone handset icon in the small window that will appear and select "Start NetTalk Service"
7- plug your netTalk in the USB port
If it works well, you will have the green led (Congratulation)

---

