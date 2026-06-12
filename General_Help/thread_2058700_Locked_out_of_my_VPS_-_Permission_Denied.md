---
title: "Locked out of my VPS - Permission Denied"
date: 2012-09-16
forum: General Help
---

### Post by bencrosthwaite on 2012-09-16
Hello Everyone,

I have a fairly serious problem which i would really appreciate some help with.

I have a Linode VPS where i host the websites i look after.  I secured this VPS using SSH key pair authentication.  I disabled the ability to SSH into the server as root after reading it was advisable to do so.

My problem is that i had my laptop stolen.  Now when i try and SSH into the VPS i am getting the "Permission denied (publickey)" using both root@<ip-address> and <username>@<ip-address>.  This is to be expected as my stolen laptop has the required SSH key-pair and my new laptop does not.

I need to know if there is any other way to gain access to my VPS. I am in panic mode at the moment =(

Regards,
-Ben

---

### Post by Old_Grey_Wolf on 2012-09-16
Contact Linode. They have physical access to the servers. Maybe they can use a console to login to the VM and enable root ssh so that you can fix your ssh key problem. Maybe they can help you some other way.

---

### Post by Cheesemill on 2012-09-17
Linode provide out-of-band access for just this reason, connection details are here:

[http://library.linode.com/troubleshooting/using-lish-the-linode-shell](http://library.linode.com/troubleshooting/using-lish-the-linode-shell)

---

