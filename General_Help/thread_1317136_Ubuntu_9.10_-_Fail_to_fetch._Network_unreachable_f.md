---
title: "Ubuntu 9.10 - Fail to fetch. Network unreachable from Synaptic"
date: 2009-11-06
forum: General Help
---

### Post by Boibondas on 2009-11-06
Hello folks,

Since I updated to Ubuntu 9.10 I lost the possibility to use the Synaptic. 
Every time I try to install ANY package from the Synaptic (and from Ubuntu Software Center as well) the download fails to start and I get the following message:

[FONT=Verdana][SIZE=1]W: Failed to fetch [http://.](http://.)...  
Cannot initiate the connection to it.archive.ubuntu.com:80 (2001:760:ffff:b1::34).- connect (101: Network is unreachable)[/SIZE][/FONT]

I have no internet connection problems and I tried to ping  it.archive.ubuntu.com:80 and it did not fail.

I have a direct connection.

Any suggestion? Thanks

---

### Post by pjbgravely on 2009-11-06
This maybe a long shot but it is something to try.

Click: System/Administration/Software Sources/ 

Go to "Download from" and click the down arrow after URL.

Click "other", then click "Select Best Server". 

This may fix your problem or give you more clues.

Paul

---

### Post by P4man on 2009-11-06
That looks like an IPv6 address?
are you behind a proxy? If so try configuring it in synaptic > settings > preferences > network.

---

### Post by Boibondas on 2009-11-06
> This maybe a long shot but it is something to try.

Click: System/Administration/Software Sources/ 

Go to "Download from" and click the down arrow after URL.

Click "other", then click "Select Best Server". Thanks Paul,

My original server was labeled as "Italian Server". I switched to "Best Server" (which turned out to be a Romanian one) as you told me but when I went back to the Synaptic I could not find the package I wanted anymore. Hence I did the job again and switched to what was called "Main Server". Now the packages reappeared and everything works.

---

