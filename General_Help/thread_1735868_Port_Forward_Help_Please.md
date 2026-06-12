---
title: "Port Forward Help Please"
date: 2011-04-21
forum: General Help
---

### Post by Vizualize on 2011-04-21
I need help port forwarding my ZyXEL T1 v2.
Im trying to port forward the port 25565.
But I cant access my router settings.
HELP

---

### Post by highspider on 2011-04-21
If I understand you need the ip of the router to access its settings.

Try from shell ```

route

```default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

and look for default and then open fireforx and type in the IP
192.168.0.1

the default passwords are here
[http://defaultpasswords.in/zyxel-router-default-password-login-username-for-modems](http://defaultpasswords.in/zyxel-router-default-password-login-username-for-modems)

---

### Post by 3rdalbum on 2011-04-21
> **Vizualize said:**
> I need help port forwarding my ZyXEL T1 v2.
Im trying to port forward the port 25565.
But I cant access my router settings.
HELP

Go to the Network Manager and go to Connection Information. The "default route" is the address you have to put into your web browser to access your router's settings.

---

### Post by Vizualize on 2011-04-21
> **3rdalbum said:**
> Go to the Network Manager and go to Connection Information. The "default route" is the address you have to put into your web browser to access your router's settings.

I tried that but there is no option to port forward or  do anything
Thanks for your help

---

### Post by Vizualize on 2011-04-21
> **highspider said:**
> If I understand you need the ip of the router to access its settings.

Try from shell ```

route

```default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

and look for default and then open fireforx and type in the IP
192.168.0.1

the default passwords are here
[http://defaultpasswords.in/zyxel-router-default-password-login-username-for-modems](http://defaultpasswords.in/zyxel-router-default-password-login-username-for-modems)

I've tried all that and unfortunately for me it doesn't work
Thanks for your help

---

### Post by highspider on 2011-04-21
both are responses are only suggesting how get the address of how to connect to your router. so you can use then use port forward. like wehn you type in [www.google.com]("http://www.google.com") you go to google's web site to interact with google. or if you type in [http://91.189.94.12](http://91.189.94.12)
you would get the ubuntu's website.  you have type in the ip of your router in firefox 

your router should be default
[192.168.1.1]("http://www.routeripaddress.com/routers_with_default_address_192.168.1.1/")

from firefox
[http://192.168.1.1](http://192.168.1.1)

if that doesn't work then type 
```

route
``` from the commandline what a second for the info to pop up. and it similar to this
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
[COLOR=DarkRed]default [/COLOR]        [COLOR=DarkRed]192.168.0.1[/COLOR]     0.0.0.0         UG    0      0        0 eth0

the default in above is how I would get to my router by using firebox would be
[COLOR=DarkRed]http://192.168.0.1[/COLOR]  

You should either get strait in or be prompted for a username and password
the defualt if you never changed it should be
username: admin
password: 1234

or
username:       <leave blank>
password : 1234

or check my above post for other passwords

---

### Post by Vizualize on 2011-04-22
So, my problem is that l can't configure anything on my router's 'webpage', l think it's called wizard mode, but there is no other obvious mode to enter the router in.

Any and all help would be greatly appreciated, thanks.

---

### Post by tredegar on 2011-04-22
I am *assuming* your router is a ZyXEL P-660HW-T1 v2
It's (PDF) manual is here: [http://www.zyxel.co.uk/web/product_family_detail.php?PC1indexflag=20040812093058&CategoryGroupNo=AC5783AE-9475-41AD-BDA5-0997187F44AA]("http://www.zyxel.co.uk/web/product_family_detail.php?PC1indexflag=20040812093058&CategoryGroupNo=AC5783AE-9475-41AD-BDA5-0997187F44AA")

Part 2.2 (page 41) tells you how to login to your router.
Once you have logged in do not click "Go to wizard". Do click "Go to advanced setup", "Apply".

Port forwarding (NAT) and how to set it up on your router, is discussed in chapter 8 on page 125.

From the manual:
> If you forget your password [COLOR="Red"]or cannot access the web configurator[/COLOR], you will need to use the
RESET button at the back of the ZyXEL Device to reload the factory-default configuration
file. This means that you will lose all configurations that you had previously and the password
will be reset to “1234”.


---

