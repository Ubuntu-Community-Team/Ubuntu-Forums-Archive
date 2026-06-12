---
title: "i have problems with internet"
date: 2006-04-09
forum: General Help
---

### Post by raker on 2006-04-09
i have problems with internet when i am on unbuntu dapper drake flight 5...
my connection work as much as i use the computer, if pass a few minutes my connection lost and i must restart my computer if i want works again. 
my mb is asus p5gdc-v deluxe, which has marvell yukon.
thanks,

---

### Post by ubernoob on 2006-04-10
still the same problem?

what is the output of ifconfig?

And if you want to restart the net, you can do
sudo ifdown eth0
sudo ifup eth0

No rebooting in linux ;)

---

### Post by caeza on 2006-05-13
i've the same problem with Dapper Flight 7.
I never have this problem before.

---

### Post by rvergara on 2006-05-13
[QUOTE=raker]i have problems with internet when i am on unbuntu dapper drake flight 5...
my connection work as much as i use the computer, if pass a few minutes my connection lost and i must restart my computer if i want works again. 
my mb is asus p5gdc-v deluxe, which has marvell yukon.
thanks,[/QUOTE]


Are you connecting via pppoe?

In Administratio->Administration->networking, you can edit the properties of your pppoe connection, verify you have ticked the option to mantain the connection on in the configuration tab.

Hope this helps.

Ramiro

---

