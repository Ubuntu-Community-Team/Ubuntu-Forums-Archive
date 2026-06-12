---
title: "Karmic and startup services.. How ?"
date: 2010-01-03
forum: General Help
---

### Post by Ordes on 2010-01-03
In the previous ubu's there had been always a menu entry, System > Admin > Services. Where one could enable/ disable the services to boot at startup (and not user specific), e.g vsftpd, ssh, etc

In karmic this menu is gone... 

How do i enable those services by command? Never had to do it before, and couldnt find the right answer yet..

I can start the services by e.g. $ sudo /etc/init.d/vsftpd start

But as this is my headless home server, i like to be able to setup which services/ daemons i run on boot and which not...

e.g how would i enable vsftpd and disable vsftpd on boot?

---

### Post by Saiko Berry on 2010-01-03
System > Preferences > Startup Applications

---

### Post by Ordes on 2010-01-03
nope... 

this is for the user... and it is only triggered when the user logs in... 

second:
services like ssh-server, vsftpd-server, are not listed in there. how do i manage those?

---

### Post by Ordes on 2010-01-03
it seems like 

update-rc.d [-n] B name  disable|enable [ S|2|3|4|5 ]

should be the right command.. 

but what is the B for? 
would the commands be like:

update-rc.d vsftpd enable

update-rc.d vsftpd disable

or do i also have to set the run levels?

---

### Post by bodhi.zazen on 2010-01-04
> **Ordes said:**
> it seems like 

update-rc.d [-n] B name  disable|enable [ S|2|3|4|5 ]

should be the right command.. 

but what is the B for? 
would the commands be like:

update-rc.d vsftpd enable

update-rc.d vsftpd disable

or do i also have to set the run levels?

upstart-rc.d is what you want.

See : [http://www.debuntu.org/how-to-manage-services-with-update-rc.d](http://www.debuntu.org/how-to-manage-services-with-update-rc.d)

---

### Post by Ordes on 2010-01-04
@bodhi

yeah thats what i need. however the ubu update-rc.d also has an option for disable/enable
[http://manpages.ubuntu.com/manpages/lucid/en/man8/update-rc.d.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/update-rc.d.8.html)

I try to figure out how the enable/ disable is applied correclty ...

---

### Post by bodhi.zazen on 2010-01-04
> **Ordes said:**
> @bodhi

yeah thats what i need. however the ubu update-rc.d also has an option for disable/enable
[http://manpages.ubuntu.com/manpages/lucid/en/man8/update-rc.d.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/update-rc.d.8.html)

I try to figure out how the enable/ disable is applied correclty ...

You can either change run levels with init 2 or manually look at eht links in your /etc/rcX.d/ or reboot.

---

### Post by Ordes on 2010-01-04
mhm... so, as init.d is already setup,  would be 

update-rc.d vsftpd enable

update-rc.d vsftpd disable

enough, to switch them on or off?

---

### Post by Ordes on 2010-01-24
update-rc.d FILENAME enable

update-rc.d FILENAME disable

works fine... if u want to get rid of it completely than use remove...

---

