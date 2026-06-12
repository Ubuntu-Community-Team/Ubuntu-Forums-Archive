---
title: "Update Manager not connecting to Server"
date: 2010-09-04
forum: General Help
---

### Post by mario.r on 2010-09-04
Hi

Version 8.1.  I am trying to update all software packages on my netbook.  When I run the update manager and press check, it scans for a while saying downloading 1 of 15 packages and then  returns with errors like:
[I][B]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_ZA.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_ZA.bz2)  Unable to connect to 10.0.1.248 8080:

W: Some index files failed to download, they have been ignored, or old ones used instead.[/B][/I]

Please help....how do I upgrade software on my netbook to their latest version?

---

### Post by JedMeister on 2010-09-04
Double check your network connectivity is ok. Do web pages load ok in your browser?

---

### Post by mario.r on 2010-09-04
Web pages load fine, network connectivity is not an issue.

---

### Post by JedMeister on 2010-09-04
Ok so general networking is ok. On closer inspection I just noticed: "Unable to connect to 10.0.1.248 8080". Do you have/have you had some sort of proxy set up? That looks like a LAN IP to me (maybe some sort of proxy or apt-cache?) Sound possible? I have heard that some proxies work fine for web but no so good for updates.

If that's the case this may not help but probably worth a try changing your download mirror. Open Synaptic: System>>Administration>>Synaptic Package Manager (on Ubuntu 10.04) then Settings>>Repositories and change the mirror you are using from the Download from dropdown. Then close and reload.

---

### Post by mario.r on 2010-09-05
I don't have a firewall set up, stand-alone netbook accessing the web via 3G connectivity.  So I tried your second suggestion with the Synaptic Package Manager.  But no matter which server I choose (or let Ubuntu choose for me) I get the same result and the same IP address : Port error after reload (unable to connect to 10.0.1.248:8080).  
[I][B]
W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/main/i18n/Translation-en_ZA.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/main/i18n/Translation-en_ZA.bz2)  Unable to connect to 10.0.1.248 8080:[/B][/I]

Any files perhaps that I could upload to help solve this?

---

