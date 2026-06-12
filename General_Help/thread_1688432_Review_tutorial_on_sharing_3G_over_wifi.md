---
title: "Review tutorial on sharing 3G over wifi"
date: 2011-02-15
forum: General Help
---

### Post by Eric.B on 2011-02-15
Hi,

I've spent some time trying to get my 3G card connection shared over WIFI and despite the number of sites out there I had a lot of problems putting it all together.  So I wrote a small guide about it, but due to several issues (time/bandwidth) I can't retest it from scratch.

I was wondering if someone could take a look at it and make suggestions or corrections.

The idea is to take your 3G data card and turn your WIFI into an access point so you can connect other devices to it for internet access.

link is here
[http://www.sailsarana.com/share_3G_data_internet_over_wifi.php](http://www.sailsarana.com/share_3G_data_internet_over_wifi.php)

Thanks,
Eric

---

### Post by Eric.B on 2011-02-17
No comments?  I was hoping someone would offer an easier way (via an Ad-Hoc setup?) or perhaps suggest some improvements...

---

### Post by t0p on 2011-02-17
This functionality is something that I'm very interested in, as I have no wired internet access available at home and rely on a 3G cellphone to connect my computer(s) to the outside world.

Unfortunately, I'm not at home right now.  But when I get back home in a few days' time, I will give this a go.  I have bookmarked that page you linked to!  So I'll have bouquets/brickbats for you soon! :p

---

### Post by gobbledigook on 2011-02-17
hey :) 

your tutorial looks great! 

i would only like to add that if you wanted to put this on a dedicated machine you can actually use a [dd-wrt]("http://www.dd-wrt.com/phpBB2/viewforum.php?f=1") enabled router with a USB connection for the 3g card, all mega brainslayer builds have this 3g option all ready to go :)

---

### Post by Eric.B on 2011-02-19
Great thanks for the help. I'm also interested in what your performance is like because my GSM coverage is pretty poor here.  So when I bridge the GSM data over the WIFI I can't get a good idea of the performance.

---

### Post by shawnerz on 2011-04-06
Eric,
You are a Godsend!  I sent you a private email on your website.
Your instructions and examples worked great on a Hauwei (through Vodafone) K3765 plugged in to a laptop running Ubuntu 10.04 LTS (Lucid Lynx).
"Works like a champ!!" "Bob's your uncle-it works" and any other phrase you want to express my gratitude!
:popcorn:

---

### Post by shawnerz on 2011-04-08
I thought it was working. But after further testing, the bridge of 3G USB modem <-> WLAN0 does not work. :icon_frown:

Here is the list of equipment:
Laptop running Lucid Lynx 10.04.
Vodafone 3G USB dongle (Hauwei K3765)
Another laptop.
Blackberry Torch (9800).

Using WPA or running an open hotspot makes no difference.  I get the same results.

Here is a list of problems that I'm seeing:
The ppp0 IP address doesn't get populated in to /etc/dhcp3/dhcpd.conf file.  I manually have to add that in.  It's minor, but I thought I'd mention it.

Everything *looks* like it is working.  The bridge comes up without errors.  Firestarter comes up.

On my Blackberry, I can connect and get an IP address.  I get the icon that the phone can connect to the BIS (Blackberry Internet Server).  In Firestarter, I see the https connection.  But none of the apps that require the connection work: Weather Channel, backups, other wi-fi connections.  None work and I can't surf using the wi-fi connection.

On the separate laptop, in can connect and get an IP address.  The *only* application I've seen work is Skype.  I can't explain it, but Skype finds a way to tunnel through.
http (port 80) and https (443) won't connect.  Haven't tried other protocols such as ftp, or ssh.

I added all of the possible IP addresses (I only allow 5) in to Firestarter as allowed connections.  There is no difference.

Any ideas?
Thanks,
-Shawn

---

