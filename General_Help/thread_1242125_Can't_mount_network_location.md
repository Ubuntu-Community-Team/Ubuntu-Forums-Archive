---
title: "Can't mount network location"
date: 2009-08-16
forum: General Help
---

### Post by dtrot55 on 2009-08-16
I am trying to access my other ubuntu computer on the network with my ubuntu laptop.  Everytime i go to place-->networks and click on workgroup i get this error:

Unable to mount location
Failed to retrieve share list from server

My windows computers can see and access my ubuntu computers, but it seems my ubuntu laptop can't????  Any ideas???

---

### Post by lessgov2007 on 2009-08-16
This is what I had to do to fix this issue with Jaunty.

1- Install winbind

sudo apt-get install winbind

2- Edit /etc/nsswitch.conf

sudo nano /etc/nsswitch.conf

Where it lists hosts add "wins" before the "dns"

Example:  hosts: files wins dns

Here's what mine reads after the correction.

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

---

### Post by dtrot55 on 2009-08-16
I installed the winbind and made sure the .conf matched yours and still getting error...do i need to do on other ubuntu computer too???

---

### Post by lessgov2007 on 2009-08-16
> **dtrot55 said:**
> I installed the winbind and made sure the .conf matched yours and still getting error...do i need to do on other ubuntu computer too???Try viewing your network on the computer you made the corrections on. If it now shows the network, then it should also fix the other systems too.

Also, reboot the computer first! I almost forgot to mention this part.

---

### Post by dtrot55 on 2009-08-16
K...restarted laptop...and also did what you reccomended on the desktop and restarted that computer too...so will see what happens

---

### Post by dtrot55 on 2009-08-16
Still no luck :(

---

### Post by lessgov2007 on 2009-08-16
> **dtrot55 said:**
> Still no luck :( Two things. First do you have samba installed? Do you have Firestarter installed?

---

### Post by dtrot55 on 2009-08-16
samba yes...firestarter no...installing now...should i do it on the other ubuntu computer also?

---

### Post by lessgov2007 on 2009-08-16
> **dtrot55 said:**
> samba yes...firestarter no...installing now...should i do it on the other ubuntu computer also?Shouldn't have to install firestarter. I only asked because once it's installed you have to create a policy for samba in Firestarter. 

Here's a quick test to try. Do you know the IP of one of your computers? If so, in nautilus address bar type: smb://192.168.1.4 <--- that's an example IP address use one of your own. You can also do this test in your browser too. 

I'm surprised someone more network savvy than me hasn't replied to your thread yet.

Well I'm off to sleep now. I hope you get this worked out.

---

### Post by dtrot55 on 2009-08-16
looks like that worked...though wasn't able to hit the windows computers but the ubuntu computer did connect

---

### Post by dtrot55 on 2009-08-16
Thanks for the help...think it is all working now...though it doesnt work through the network browser but i can type in the ip in naut....

---

