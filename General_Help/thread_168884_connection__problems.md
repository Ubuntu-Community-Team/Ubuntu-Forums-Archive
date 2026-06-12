---
title: "connection  problems"
date: 2006-05-01
forum: General Help
---

### Post by prib on 2006-05-01
ok i have jsut installed Ubuntu and then triend to open a web browser only to find that it does not display any websites, so i went to the about:config settings in firefox and changed the network.dns.disableIPv6 option and then i was able to access google which works find except when i click on a search result it seems to be unable to access any other pages (even when i just give the  whole address as oppossed to going throuhgh google. i dont know if it is relevant but i can also not connection to msn messenger through gaim which suggests that it is not jsut a fire fox problem. 

i connect to the internet via a adsl router which finds the computer fine but doesnt display the hostname as what i set it as (defualt "ubuntu") 

any help would be appreciated.

---

### Post by rvergara on 2006-05-01
check the MTU setting in your adsl router. it should be set to 1492 for adsl connections. I have seen that many of them are set at 1500 from factory.

Regards

Ramiro

---

### Post by Anilkumar on 2006-05-01
I think u have problem with etho connection. How are u connecting internet by using this following command

pon dsl-provider

if yes sometimes u will be having more than one connection.it will create problems
chek it out

---

### Post by prib on 2006-05-01
[QUOTE=Anilkumar]I think u have problem with etho connection. How are u connecting internet by using this following command

pon dsl-provider

if yes sometimes u will be having more than one connection.it will create problems
chek it out[/QUOTE]


i connect through the router using a dhcp server so i thought it would autop detect the settings?

---

### Post by prib on 2006-05-01
does any 1 have anything i can try cause i am all out of ideas

---

### Post by Jason_25 on 2006-05-01
Does 
```

cat /etc/resolv.conf

```
show the address of your router?

---

### Post by prib on 2006-05-01
[QUOTE=Jason_25]Does 
```

cat /etc/resolv.conf

```
show the address of your router?[/QUOTE]


yes it does

---

### Post by Jason_25 on 2006-05-01
What happens when you ping [www.google.com?](www.google.com?)

---

### Post by prib on 2006-05-01
[QUOTE=Jason_25]What happens when you ping [www.google.com?](www.google.com?)[/QUOTE]

it pings it normally as it does with any other address i seem to ping althought this time when i tried to use a web browser bbc.co.uk worked but no others, its like only the first site i try to access works but no others

---

### Post by Jason_25 on 2006-05-01
Do you have other pcs connected to the router to test?  Do they exhibit the problem?

---

### Post by prib on 2006-05-01
[QUOTE=Jason_25]Do you have other pcs connected to the router to test?  Do they exhibit the problem?[/QUOTE]

there are serveral other pc's runnign windows which work fine including this one when i boot into windows

---

### Post by prib on 2006-05-02
ok it seems like it is only the first site that i access that works then no others which is really strange any one got any suggestions?

---

### Post by Jason_25 on 2006-05-02
You might be having a problem with ipv6.  I've never had to mess with it but I think you can add 
```

blacklist ipv6

```
to /etc/modprobe.d/blacklist
and reboot to stop it from loading.

---

### Post by rvergara on 2006-05-02
Prib,

Did you check the MTU setting in your router as I suggested? MTU of 1500 causes erratic access to the web.

Ramiro

---

### Post by prib on 2006-05-02
[QUOTE=rvergara]Prib,

Did you check the MTU setting in your router as I suggested? MTU of 1500 causes erratic access to the web.

Ramiro[/QUOTE]

yeh mtu settings are fine

---

### Post by prib on 2006-05-02
[QUOTE=Jason_25]You might be having a problem with ipv6.  I've never had to mess with it but I think you can add 
```

blacklist ipv6

```
to /etc/modprobe.d/blacklist
and reboot to stop it from loading.[/QUOTE]


That also doesnt seem to work.

it really doenst make sense, why would i be able to access one site(always the first one i visit when i have restarted he comp) and no others. i dont know if gaim not working is the same problem or a different one. I have tried various web browser all with the same result which suggests it is not a firefox problem

i really appreciate peoples help as i'm completly out of ideas, any one got ne more suggestions?

---

### Post by prib on 2006-05-02
another point when i look at my dhcp clients through the router there is 3 clients and two of them including my connection have the same host name which is the host name of the other computer, even though in ubuntu the host name is set as ubuntu.

---

### Post by prib on 2006-05-02
-deleted-

---

