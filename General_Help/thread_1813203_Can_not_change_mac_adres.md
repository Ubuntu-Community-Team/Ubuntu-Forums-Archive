---
title: "Can not change mac adres"
date: 2011-07-27
forum: General Help
---

### Post by papaapa on 2011-07-27
Hello!

I use GNU MAC Changer. It changes my local network connection mac adress properly. But it does not changes my wireles mac adres. I try it with sudo ofcourse the error which i get is : "ERROR: Can't change MAC: interface up or not permission: Too many open files in system". I disable the wireles connection and then try to change the mac but i get the same error. I try these commands :

# ifconfig eth0 down
# ifconfig eth0 hw ether 00:80:48:BA:d1:30
# ifconfig eth0 up
# ifconfig eth0 |grep HWaddr

But i get the exactly same error.

(I can change the wireles mac from Windows 7 properly.)

Can someone please help me ?

Thank you!

---

### Post by Wayne_V on 2011-07-27
1.  Is eth0 your wireless NIC?   What is the output of 'ifconfig -a'?

2.  From the man page:

> hw class address
              Set the hardware address of this interface, if the device driver supports this operation.

What device driver does you wireless NIC use?

---

### Post by blackbird3216 on 2011-07-27
Changing mac addresses?

I thought mac addresses were a property of the network card and cant be changed manually. That's why mac filtering works, right?

---

### Post by tredegar on 2011-07-27
> I thought mac addresses were a property of the network card and cant be changed manually. 
MAC addresses are built into the networking hardware, but they can usually be changed.
> That's why mac filtering works, right?
MAC filtering should not be considered "secure" when MAC addresses can easily be spoofed.

---

