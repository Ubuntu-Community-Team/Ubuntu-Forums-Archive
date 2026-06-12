---
title: "libnet_select_device(): can't find interface eth1"
date: 2006-02-20
forum: General Help
---

### Post by ginguene on 2006-02-20
Hello

I am using a software to connect to the Intranet of my school and Internet : **XRGSupplicant 1.1.1**
my eth0 is my Wifi connection (disabled)
eth1 is the one i am using to connect.
It works perfectly as you see (i am surfing the Net :p)

But i want to use another software called [MyStar]("http://www.linuxeden.com/download/softdetail.php?softid=1152")
The reason i want to change? XRGSupplicant sux , there is no conf file, and i keep getting disconnected !

so i run *sudo ./mystar* after i made my mystar.conf where i selected eth1 as my Interface and here is the error i get :
```
libnet_init: libnet_select_device(): libnet_select_device(): can't find interface eth1
```

I looked on google and found : 
> ```
Can't open eth0: libnet_select_device(): Can't find interface eth0
```

Generally this occurs when the interface (eth0 in this example) is not up or doesn't have an IP address assigned to it. 

But i already have an IP assigned to eth1 and its up.

Anyone to help ? thank you

---

