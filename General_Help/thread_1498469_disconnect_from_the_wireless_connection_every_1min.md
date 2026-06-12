---
title: "disconnect from the wireless connection every 1min"
date: 2010-05-31
forum: General Help
---

### Post by Danili on 2010-05-31
Hi everybody
I have been useing Ubuntu for 1-2years now. Lately I've been having some troubles with my wireless Internet connection, almost every 1min i disconnect and connect again few sec after and thats like hell if you try to fx. update. I have 85-92% signal so thats not my problem. I use Ubuntu 10.04 and the standard network manager. I'm connected to a netgear router and my computer is a acer aspire one.
if you need any extra information just ask.

i hope someone can help thanks :)

---

### Post by sdennie on 2010-05-31
If you can reproduce the error that easily, you might want to run the following:

```

tail -f /var/log/messages

```

And then wait for/cause the disconnect.  The logs may tell you want is going on.  The forums may not be able to fix the problem but, you at least will have a starting point for a bug report.

---

### Post by Danili on 2010-05-31
May 31 05:39:31 danili-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="704" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
May 31 06:41:49 danili-laptop kernel: [19132.303533] ath5k phy0: unsupported jumbo
May 31 06:53:30 danili-laptop kernel: [19833.860426] ath5k phy0: unsupported jumbo
May 31 07:01:49 danili-laptop kernel: [20332.243525] ath5k phy0: unsupported jumbo
May 31 07:21:26 danili-laptop kernel: [21508.979193] ath5k phy0: unsupported jumbo
May 31 07:43:11 danili-laptop kernel: [22814.168046] ath5k phy0: unsupported jumbo
May 31 07:47:51 danili-laptop kernel: [23094.752169] ath5k phy0: unsupported jumbo
May 31 12:00:32 danili-laptop kernel: [38255.455384] ath5k phy0: unsupported jumbo
Jun  1 03:07:10 danili-laptop kernel: [92654.174084] ath5k phy0: unsupported jumbo

i hope this was what you where asking for

---

### Post by sdennie on 2010-05-31
That's exactly what I was looking for.  A google search for "ubuntu ath5k phy0: unsupported jumbo" might find the solution and, if not, you can file a bug with that output on launchpad.net and hopefully a solution will be found.

---

### Post by smellyman on 2010-05-31
there is a lot of out there on that error and a bug report was filed.
 
I saw a simple answer of changing the channel on your router.
 
another was installing the madwifi drivers for your atheros card.

---

### Post by Danili on 2010-05-31
i found this guide: [http://petejcullen.wordpress.com/2009/12/10/fixing-the-madwifi-driver-on-ubuntu-9-04-jaunty-netbook-remix/](http://petejcullen.wordpress.com/2009/12/10/fixing-the-madwifi-driver-on-ubuntu-9-04-jaunty-netbook-remix/)

thats exactly my prob but i followed the guide and after the restart i only had wired connection in my network manager :S so i did the thing in the bottom of the guide to get back to ath5k any idea why it went wrong?

---

### Post by Danili on 2010-05-31
the channel change in the route didn't help either.

the driver change might be the awnser if i could just do it right

---

