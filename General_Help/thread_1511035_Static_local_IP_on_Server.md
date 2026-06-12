---
title: "Static local IP on Server"
date: 2010-06-16
forum: General Help
---

### Post by AlexRamallo on 2010-06-16
I'm trying to host a webserver using the ubuntu server edition, and I got it set up perfectly(apache, mysql, php, ssh :D) but I'm having trouble with the port forwarding part. I know what port forwarding is and how to do it, I've done it thousands of times, but my router(linksys) for some reason is starting to change around the local IPs of my computers and I can't be constantly updating the ports on the router. I need to be able to give the server computer a static local IP address so that this doesn't happen, I know Ubuntu desktop edition has a way to do it(as well as Windows), but the server edition doesn't have a GUI so its not as easy to do

---

### Post by AlexRamallo on 2010-06-16
no one knows?

---

### Post by Neezer on 2010-06-16
Check this site out.

[http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html)

basically,

open

/etc/network/interfaces

with your favorite editor. You'll have to use sudo to have the right to edit the file.

Then make it look something like this:

```

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1


```


You might have to change things based on your network setup, but that should work. I like to change mine to something that the router won't assign in its DHCP range. I like 192.168.1.2 for my server.

then restart networking with:

```

sudo /etc/init.d/networking restart

```

Hope this helps.

---

### Post by lisati on 2010-06-16
My personal preference is to let the router hand out static IP addresses, which should be possible from your router's configuration page. This can help avoid IP address conflicts if for some reason you hook your gear up to a different router.

I don't have a Linksys router, so someone else might have to guide you through the specifics.

---

### Post by AlexRamallo on 2010-06-16
Thanks Neezer that linked really helped! :)

---

