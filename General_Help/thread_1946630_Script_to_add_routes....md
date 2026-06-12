---
title: "Script to add routes..."
date: 2012-03-25
forum: General Help
---

### Post by rado3105 on 2012-03-25
I created file with this commands inside:

#!/bin/bash
ip route add 10.13.58.0/24 dev ppp0
ip route add 10.13.57.0/24 dev ppp0
ip route add 10.13.56.0/24 dev ppp0
ip route add 10.13.54.0/24 dev ppp0
ip route add 192.168.76.0/24 dev ppp0

and named it: vpn-routes and saved in my home folder, when i start it using command:
sudo ./vpn-routes it doesnt create new routes.
What I am doing wrong? thanks

---

### Post by rado3105 on 2012-03-25
I solved it thanks:

[http://rado3105.blogspot.com/2012/03/how-to-install-and-seup-vpn-client-in.html](http://rado3105.blogspot.com/2012/03/how-to-install-and-seup-vpn-client-in.html)

---

