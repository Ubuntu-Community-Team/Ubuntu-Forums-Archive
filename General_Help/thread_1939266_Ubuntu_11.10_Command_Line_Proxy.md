---
title: "Ubuntu 11.10 Command Line Proxy"
date: 2012-03-11
forum: General Help
---

### Post by dudle1989 on 2012-03-11
Hi

I am currently a studend at a college now our to acces the internet we have a proxy that we use. This all worked perfectly in windows 7. Now I configured proxy settings for my Ubuntu system firefox works, I can use the System Update tool and that works too. Now when I try to use the command line tool to update/download a package I get a timeout.

My current proxy settings is:
[http://www2.pentech.ac.za/proxy.pac](http://www2.pentech.ac.za/proxy.pac)

This is my command:
sudo wget [http://www.medibuntu.org/sources.list.d/oneiric.list](http://www.medibuntu.org/sources.list.d/oneiric.list) -O /etc/apt/sources.list.d/medibuntu.list

This is the response:
Resolving [www.medibuntu.org](www.medibuntu.org)... 88.191.127.22

And after a while i get the time out:
Connecting to [www.medibuntu.org|88.191.127.22|:80](www.medibuntu.org|88.191.127.22|:80)... failed: Connection timed out.

THanks

---

