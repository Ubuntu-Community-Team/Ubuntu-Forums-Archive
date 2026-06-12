---
title: "DNS question"
date: 2012-06-02
forum: General Help
---

### Post by Diametric on 2012-06-02
Hello,

If I wanted to know what IP's have been assigned to me via my ISP, where would I get this info? I'm sure this is logged, I just can't seem to find where.

Thanks!

---

### Post by Easy Limits on 2012-06-02
Type whatsmyip in your web browsers address bar.

You can also look in your router configuration, if you use one.

---

### Post by Diametric on 2012-06-02
Thanks, but I'm looking (hoping) for a log file.  Some process that captures what my IP's have been and writes that data to a file so that I can, at any given point, query said file and know what my dhcp assigned IP's have been for any given time.

Cheers!

---

### Post by codemaniac on 2012-06-03
> **Diametric said:**
> Hello,

If I wanted to know what IP's have been assigned to me via my ISP, where would I get this info? I'm sure this is logged, I just can't seem to find where.

Thanks!

You can check your IP address by firing the below command on your terminal .
```
/sbin/ifconfig
```

---

### Post by jenic on 2012-06-03
> **Diametric said:**
> Hello,

If I wanted to know what IP's have been assigned to me via my ISP, where would I get this info? I'm sure this is logged, I just can't seem to find where.

Thanks!

If you are directly connected to the modem (I'm assuming you have one) you might see DHCP grab your allocated IP. For instance, my router is openwrt and within its logs you can clearly see the dhcpd output for obtaining its public IP address.

Perhaps you want this information because of dynamic DNS? There are great tools around to set your record automatically at set intervals or based on interface events. Look into 'ddns' which should be compatible with just about any dynamic dns service as you can give custom GET strings.

My own ( rfc1918 ) address allocation looks as such in /var/log/daemon.log:

```
May 28 13:12:11 Dracarys dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May 28 13:12:11 Dracarys dhclient: DHCPOFFER of 192.168.0.101 from 192.168.0.1
May 28 13:12:11 Dracarys dhclient: DHCPREQUEST of 192.168.0.101 on wlan0 to 255.255.255.255 port 67
May 28 13:12:11 Dracarys dhclient: DHCPACK of 192.168.0.101 from 192.168.0.1
May 28 13:12:11 Dracarys dhclient: bound to 192.168.0.101 -- renewal in 19821 seconds.

```Hope that helps! :)

---

### Post by d3v1150m471c on 2012-06-03
> **Diametric said:**
> Hello,
...I wanted to know what IP's have been assigned to me via my ISP...


IP != DNS, [https://en.wikipedia.org/wiki/Domain_Name_System](https://en.wikipedia.org/wiki/Domain_Name_System)

---

### Post by Cheesemill on 2012-06-03
If you want to set up a log of your external IP address then you can add the following line to roots crontab using 'sudo crontab -e':
```
0 * * * * echo "`date`  `curl -s ifconfig.me`" >> /var/log/externalip
```This will log your external IP once every hour to /var/log/externalip.  You may need to install [curl]("apt://curl") first.

---

### Post by Diametric on 2012-06-04
> **Cheesemill said:**
> If you want to set up a log of your external IP address then you can add the following line to roots crontab using 'sudo crontab -e':
```
0 * * * * echo "`date`  `curl -s ifconfig.me`" >> /var/log/externalip
```This will log your external IP once every hour to /var/log/externalip.  You may need to install [curl]("apt://curl") first.

I think this is what I was looking for, thank you.  from your answer, I guess there is no automatic logging of IP's over time and this would accommodate that.

thanks again!

---

