---
title: "Apache Security"
date: 2011-04-06
forum: General Help
---

### Post by patdundee on 2011-04-06
Hi Guys
Hope this is the right area for this.

Running Apache on Ubuntu Server. I have been seeing 2 issues over the past few days. Apache has been running fine over the past year or so.

Item 1) Files are being uploaded by client correctly to their respective folders. Floder permissions are set by default to 0755. The after a while the actual content of the file uploaded is missing but the page is still there and also at times the page completly dissapears from the server.

I have also uploaded my own test pages and the same is happening with them.

Item 2) Apache just stops running ad of course no web sites run this also affects webmin and phpmyadmin which also stop running. SSH is also stopped. The server however still responds on the network to pings etc but everything on the server stops or runs extremely slow.

On rebooting the server all systems work again for a while then the same thing happens again.

This has only just started happening the servers have been running fine for ages. Ubuntu versions are Ubuntu 8.10 and Ubuntu 9.04
 
Any ideas would be most welcome
(ps my windows to small to throw the servers out)

---

### Post by indytim on 2011-04-06
I'd recommend starting off by looking at your log files. Mine are in /var/log/Apache2

IndyTim / DataMan

---

### Post by patdundee on 2011-04-06
Hi indy
 
Did that this morning and the only thing in common just before a crash is this
 
[COLOR=red][FONT=Arial][SIZE=2][Tue Apr 05 11:46:53 2011] [error] [client 90.197.80.5] Invalid method in request \x16\x03\x01[/SIZE][/FONT]
[/COLOR]
[COLOR=red][COLOR=black]Having researched the above it is to do with an HTTPS call from the client at the site but there is no site running HTTPS on the server or any links from any sites to an https page[/COLOR][/COLOR]
[COLOR=red][COLOR=#000000][/COLOR][/COLOR] 
[COLOR=red][COLOR=#000000]P[/COLOR]
[/COLOR]

---

