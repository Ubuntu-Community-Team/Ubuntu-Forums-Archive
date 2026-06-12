---
title: "MySQL not starting when bind-address set to LAN"
date: 2010-06-17
forum: General Help
---

### Post by MadEgg on 2010-06-17
I have MySQL installed on my Kubuntu 10.04 desktop machine which I use for developing web applications.

First, all worked fine. But then I wanted to synchronize the database with the MySQL database on my laptop, so I had to allow connections from the LAN interface. So I added

```

bind-address = 192.168.0.100

```

to /etc/mysql/my.cnf. This worked and the synchronization was performed. I want to do this on a regular basis so I would like to keep that line in there.

The problem now is that MySQL does not start on system boot. When I start up, mysql simply is not started. There are no errors in /var/log/mysql/mysql.err or /var/log/mysql.err; these files remain empty.

When I try to start it using 'sudo start mysql' I get the same result. The 'start mysql' shows up in 'ps aux', but the mysql process itself does not. 

Now, I found out that when I run

```
sudo -u mysql mysqld
```

The mysqld daemon does start, and the server works fine. To make matters even more strange, if I kill this process and afterwards run 'sudo start mysql' again, the server is started without a hitch.

This all happens without any error messages. The entire problem is resolved when I change bind-address back to 127.0.0.1, strange enough.

Anybody knows what is going on here, and how to fix it?

By the way, my local address is supplied over DHCP, and the connection is managed by NetworkManager. I used nm-applet to set the wired connection as 'available to all users', and when I switch to the console on the login prompt, the connection is indeed available.

---

### Post by MadEgg on 2010-06-21
Any clues?

---

### Post by MadEgg on 2010-06-23
I just set up my printer using CUPS on the new machine and found it it has the same problem. I changed the Cups configuration to listen on the local network instead of on the local host only, because other machines here need to print using the same printer.

Since I changed that, CUPS does not start on boot, but after booting, it starts just fine.

Is there no way that I can use NetworkManager while still being able to have daemons listen on the network interface?

---

