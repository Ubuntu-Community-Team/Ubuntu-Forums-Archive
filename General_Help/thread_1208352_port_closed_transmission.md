---
title: "port closed transmission"
date: 2009-07-09
forum: General Help
---

### Post by gavoby on 2009-07-09
Hi there, I've tried everything to get my port open on transmission but to no avail. I am using port 51415 and tried tp forward the port manually but didnt work.
Was wondering if anyone had any ideas? Thanks.

---

### Post by credobyte on 2009-07-09
Let me guess .. v1.5 ( Transmission version ) ? :roll: If so, upgrade it to 1.7 and you'll be fine !

---

### Post by gavoby on 2009-07-09
I only find transmission 1.51 for jaunty.

---

### Post by credobyte on 2009-07-09
Follow this guide : [https://answers.launchpad.net/ubuntu/+question/72830](https://answers.launchpad.net/ubuntu/+question/72830)

---

### Post by gavoby on 2009-07-09
Does that automatically upgrade my existing transmission?
Do i restart my transmission for it to take affect?

---

### Post by credobyte on 2009-07-09
> **gavoby said:**
> Does that automatically upgrade my existing transmission?
Do i restart my transmission for it to take affect?

[LIST=1]
[*]No ( link given - read .. )
[*]Yes ( while upgrading, turn it off )
[/LIST]

---

### Post by gavoby on 2009-07-09
ok its upgraded i randomised the port and still port closed

---

### Post by Villiam on 2009-07-09
ubuntu usually has all ports auto closed on install. What I did to open a port for uTorrent is installed firestarter and use it to open up the torrent port. Opened in router too. May be this info helps.

[ubuntu]("http://www.linux-archive.org/ubuntu-user/")

---

### Post by danwood76 on 2009-07-09
This is probably more likely an issue with your router.
The randomized ports will not work if your router doesnt support Upnp.

What router do you use?

---

### Post by gavoby on 2009-07-09
how do i do that? If you dont mind.

---

### Post by gavoby on 2009-07-09
yzel p600, I have the upnp turned on

---

### Post by gavoby on 2009-07-09
> **gavoby said:**
> how do i do that? If you dont mind.
Zyxel p600

---

### Post by Arup on 2009-07-09
> **gavoby said:**
> how do i do that? If you dont mind.


[http://portforward.com/](http://portforward.com/)

---

### Post by danwood76 on 2009-07-09
In its default configureation I dont think Ubuntu has ports closed.
I never have to open ports up and I use deluge all the time.

The thing to determine if its a software issue or a closed port issue is to manually forward a port using NAT and test the port online with a site like this:
[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

---

### Post by gavoby on 2009-07-09
> **danwood76 said:**
> In its default configureation I dont think Ubuntu has ports closed.
I never have to open ports up and I use deluge all the time.

The thing to determine if its a software issue or a closed port issue is to manually forward a port using NAT and test the port online with a site like this:
[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

Ok tried that but canyouseeme couldn't connect to the port.

---

### Post by gavoby on 2009-07-09
I've tried port fowarding but no luck. I dont know what the problem is.

---

### Post by gavoby on 2009-07-09
> **gavoby said:**
> I've tried port fowarding but no luck. I dont know what the problem is.

i still can download but the download speed on a torrent goes up and down from 20 to 900 kbs every few seconds

---

### Post by 6205 on 2009-07-09
Lates Transmission for Jaunty can you get from [www.getdeb.net](www.getdeb.net) but IMO Deluge Torrent is much better, at least has much better UI.
[http://www.getdeb.net/search.php?keywords=Transmission](http://www.getdeb.net/search.php?keywords=Transmission)
[http://www.getdeb.net/search.php?keywords=Deluge](http://www.getdeb.net/search.php?keywords=Deluge)

For openning port for torrents i have added rule in ubuntu firewall using Gufw but you must also open the same port in your router and of course setup that port number also in Tranmission/Deluge torrent client.
[http://www.getdeb.net/search.php?keywords=gufw](http://www.getdeb.net/search.php?keywords=gufw)

---

### Post by gavoby on 2009-07-09
I tried deluge and the same thing is happening it says 'no incoming connections' i tried port fowarding too but still the same.

---

### Post by danwood76 on 2009-07-09
In deluges propeties where you put the port number in is a port test button which should show a green dot if the port is open.

Make sure you dont have transmission and deluge trying to use the same port at the same time.

---

### Post by gavoby on 2009-07-09
> **danwood76 said:**
> In deluges propeties where you put the port number in is a port test button which should show a green dot if the port is open.

Make sure you dont have transmission and deluge trying to use the same port at the same time.

No I don't have them both using the same port.
Anymore ideas?

---

### Post by danwood76 on 2009-07-09
It could be your ISP.
Some ISPs tend to block most ports except the common ones.

It is most likely a router configuration issue, the link posted earlier by Arup ([http://portforward.com/](http://portforward.com/)) will help you configure your router.

SOme routers require that after you setup the NAT you restart, when you restart you may need to check the IP addresses again as DHCP sometimes sucks on crappy routers.

---

### Post by gavoby on 2009-07-09
I've tried that thanks but still the same. I'm about tready to give up :(

---

### Post by credobyte on 2009-07-10
> **gavoby said:**
> I've tried that thanks but still the same. I'm about tready to give up :(

If it's really not possible to fix Transmission, why not to try other clients ( Deluge, Vuze, rTorrent, uTorrent on Wine, etc. ) ?

---

### Post by gavoby on 2009-07-10
I trird deluge but have the same problem, 'no incoming connections'

---

### Post by chriswyatt on 2009-07-10
I couldn't get UPNP to work so I ended up manually setting up on my router and opening up in the Firewall.  For incoming connections don't forget to forward it to the IP address of your computer on your router's settings page as well.

---

### Post by gavoby on 2009-07-10
as far as I know I've done all that, I'll try again maybe I missed something.
Thanks

---

### Post by gavoby on 2009-07-10
gav@gav-desktop:~$ netstat -an | grep "LISTEN "
tcp        0      0 0.0.0.0:9091            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:51532           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:3736            0.0.0.0:*               LISTEN     
tcp6       0      0 :::51532                :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
gav@gav-desktop:~$ 

ok itried this and this is what came up. Does anyone know what this means?

---

