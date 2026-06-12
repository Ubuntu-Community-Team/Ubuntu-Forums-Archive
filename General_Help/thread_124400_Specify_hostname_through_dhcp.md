---
title: "Specify hostname through dhcp?"
date: 2006-02-01
forum: General Help
---

### Post by JackDog on 2006-02-01
What is the best way to tell the DHCP server your preferred hostname with Ubuntu? 

With dhcpcd you just have to specify a "-h" option and if the dhcp server supports client requested hostnames, it will comply by using the updating dns with the hostname and informing the client of its hostname+domain.

---

### Post by JackDog on 2006-02-01
Anyone? Just need to figure out how to do this with ubuntu. I know it works with my gentoo machine. 

There has to be some dhcp configuration line somewhere that I can edit and at least hard code the hostname i want for now...

---

### Post by ranf on 2006-02-02
Try to find out how Gentoo is doing it.

I edited this file:
```
/etc/dhcp3/dhclient.conf
```

and put my hostname in this line:
```
send host-name "your.hostname";

```

---

