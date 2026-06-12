---
title: "Problem accessing usb storage device on router"
date: 2010-04-10
forum: General Help
---

### Post by garwal on 2010-04-10
I am using a Belkin F5D 8235-4 ver 2 wireless router. My linux box is connected direct. I have a 16G flash drive installed in the usb port on the router that I want to use for storage so I can dump files I share with my other machines on the network. Windows sees this usb and works fine by just using the web browser and using 192.168.2.1\usb  no problem. Then I try to use my unbuntu and can not for the life of me figure out how to set up a permanent link to that drive in linux. I would like to have a direct connection on my desktop. Of course I tried Belkin and was told we do not support Linux. So here I am asking the experts for help..Where I should have started in the first place.Thanks for any advice.
Gary

---

### Post by Morbius1 on 2010-04-10
If you open up nautilus and type: **smb://192.168.2.1/usb**
what error does it give you?

---

### Post by garwal on 2010-04-11
> **Morbius1 said:**
> If you open up nautilus and type: **smb://192.168.2.1/usb**
what error does it give you?

I am getting the password required to share usb
then it shows user-name domain and password.

I have not set up any user or password for this so I do not know what it is wanting ?
Thanks for the help
Gary

---

### Post by Morbius1 on 2010-04-11
I do not believe there is anything on the linux side that you can do to solve this problem.

The usb device is under the control of the router that appears to be taking the role of a samba server. The router is in control of who can access the usb device. There must be a way you can connect to the router's admin page to configure who has access or at least what username and password it wants.

---

### Post by dtyates on 2010-08-30
Hi there

Not sure if I've of much help but I just bought this router and had the same problem. I managed to get passed the username and password problem by putting the following in

username: guest
domain: belkin
password: <blank> (no password)

that let me in

hope it helps

Dave

---

### Post by jonnyboysmithy on 2011-12-21
> **dtyates said:**
> Hi there

Not sure if I've of much help but I just bought this router and had the same problem. I managed to get passed the username and password problem by putting the following in

username: guest
domain: belkin
password: <blank> (no password)

that let me in

hope it helps

Dave
Thank you!! Thats solved it for me!:D:D:D

---

