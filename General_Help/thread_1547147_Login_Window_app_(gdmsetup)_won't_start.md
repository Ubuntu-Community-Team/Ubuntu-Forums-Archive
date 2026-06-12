---
title: "Login Window app (gdmsetup) won't start"
date: 2010-08-06
forum: General Help
---

### Post by Twelveone on 2010-08-06
I'm trying to run the "Login Window" application in Ubuntu to allow me to setup automatic login. When I select it from the System > Administration menu, all I get is a message in the task bar stating an application is starting then that disappears but the app does not start.

I've also tried starting it from the command line using 
gksu /usr/sbin/gdmsetup 
but this has the same result and does not yield any more clues to the problem

I have setup 10 systems with exactly the same image. 8 work perfectly and 2 will not allow the Login Window app to open.

I may have resolved the immediate problem by editing the /etc/gdm/gdm.conf-custom file, but I would like to resolve the underlying issue.

Finally having enabled the automatic login manually I have noticed that other applications are very slow to start on these 2 PC's

I also should mention I'm using 8.04 LTS

Can anyone help?

---

### Post by dino99 on 2010-08-06
try: sudo dpkg-reconfigure gdm

and check that the graphic driver is activated: system admin hardware driver

---

### Post by Twelveone on 2010-08-11
> **dino99 said:**
> try: sudo dpkg-reconfigure gdm

dpkg-reconfigure made no difference


I'm not sure what you mean by 

> **dino99 said:**
> check that the graphic driver is activated: system admin hardware driver

There are no proprietory drivers in use on the system, so nothing shows in System > Administration > Hardware Drivers

---

