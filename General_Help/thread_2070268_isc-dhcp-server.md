---
title: "isc-dhcp-server"
date: 2012-10-12
forum: General Help
---

### Post by ubhi on 2012-10-12
Hi,
i want to disable isc-dhcp-server ( on all boot level ) using update.rc-d in Ubuntu 12.04 LTS, like chkconfig in RHEL, but using disable command it won't work, i don't want to remove isc-dhcp-server, but want to temp disable it...
please help..

---

### Post by ubhi on 2012-10-12
Very Strange no reply. please suggest someone...
how do i disable temporarily DHCP server to run at every level (1-6), so i can use again in future.....
what if i used :- 
sudo update-rc.d -f isc-dhcp-server remove ( it will remove it or disable it temporarily)
Please suggest

---

### Post by Lars Noodén on 2012-10-12
Yes, [font=Courier New]sudo update-rc.d -f isc-dhcp-server remove[/font] will only temporarily disable the server.  You can reinstate it later, again using update-rc.d.  The script will remain available in /etc/init.d  Note that you'll probably also want to disable isc-dhcp-server6 at the same time.

---

### Post by ubhi on 2012-10-12
> **Lars Noodén said:**
> Yes, [font=Courier New]sudo update-rc.d -f isc-dhcp-server remove[/font] will only temporarily disable the server.  You can reinstate it later, again using update-rc.d.  The script will remain available in /etc/init.d  Note that you'll probably also want to disable isc-dhcp-server6 at the same time.
Thanks Lars, As you said sudo update-rc.d -f isc-dhcp-server remove -- will only temporarily disable the server. then How to reinstate it later, whether i have to re-install it or just add throug update-rc.d...

---

### Post by Lars Noodén on 2012-10-12
Reinstate it using [update-rc.d](http://manpages.ubuntu.com/manpages/precise/en/man8/update-rc.d.8.html)

```

sudo update-rc.d isc-dhcp-server defaults
sudo update-rc.d isc-dhcp-server6 defaults

```

---

### Post by Lars Noodén on 2012-10-12
Also, for one-off changes in status you can access the System V script directly:

```

sudo /etc/init.d/isc-dhcp-server start
sudo /etc/init.d/isc-dhcp-server stop

```

Neither of those will affect what the server does when the whole machine gets restarted or shut down.

---

### Post by ubhi on 2012-10-12
> **Lars Noodén said:**
> Also, for one-off changes in status you can access the System V script directly:

```

sudo /etc/init.d/isc-dhcp-server start
sudo /etc/init.d/isc-dhcp-server stop

```

Neither of those will affect what the server does when the whole machine gets restarted or shut down.
but when i restart my computer isc-dhcp-server service runing again..i don't want to run isc-dhcp-server running on startup, whenever i required then it start... please help..

---

### Post by Lars Noodén on 2012-10-12
To keep the DHCP server from starting up automatically when the machine is started, disable it using update-rc-d

```

update-rc.d -f isc-dhcp-server remove
update-rc.d -f isc-dhcp-server remove

```

If, once in a while, you need to start it manually, use the System V script:

```

sudo /etc/init.d/isc-dhcp-server start
sudo /etc/init.d/isc-dhcp-server stop

```

---

### Post by ubhi on 2012-10-13
> **Lars Noodén said:**
> To keep the DHCP server from starting up automatically when the machine is started, disable it using update-rc-d

```

update-rc.d -f isc-dhcp-server remove
update-rc.d -f isc-dhcp-server remove

```

If, once in a while, you need to start it manually, use the System V script:

```

sudo /etc/init.d/isc-dhcp-server start
sudo /etc/init.d/isc-dhcp-server stop

```
Thanks Lars.. its done...

---

