---
title: "no network devices found"
date: 2011-05-02
forum: General Help
---

### Post by jasonjackson on 2011-05-02
Hi. I'm trying to install no-ip on my linux VPS but after I do the "sudo make install" step, I get the following 

if [ ! -d /usr/local/bin ]; then mkdir -p /usr/local/bin;fi
if [ ! -d /usr/local/etc ]; then mkdir -p /usr/local/etc;fi
cp noip2 /usr/local/bin/noip2
/usr/local/bin/noip2 -C -c /tmp/no-ip2.conf

Auto configuration for Linux client of no-ip.com.

No network devices found! Ending.
make: *** [install] Error 1

I'm completely new to linux so I have no idea what to do. I'm searched and can't seem to find anything helpful.

---

### Post by jasonjackson on 2011-05-02
bump

---

### Post by jasonjackson on 2011-05-15
Well this forum has been a lot of help...

---

### Post by mörgæs on 2011-05-15
If one does not get any answers, it could be because of the question asked...

You could have begun with explaining why you wanted to compile rather than install from Synaptic. I have been using Ubuntu from release 5.10 and have only compiled one application; most people in here don't ever do it.

Besides: Bumping turns a lot of people away.

---

### Post by jasonjackson on 2011-05-15
> **mörgæs said:**
> If one does not get any answers, it could be because of the question asked...

You could have begun with explaining why you wanted to compile rather than install from Synaptic. I have been using Ubuntu from release 5.10 and have only compiled one application; most people in here don't ever do it.

Besides: Bumping turns a lot of people away.

I don't really know. I was just following the tutorial on the no-ip website. It didn't say any other way to do it. Also, it was either bump it or start a new topic. I'm paying for this VPS and I'm trying to get my money's worth. Sorry if I sound rude. I don't mean to be. Linux has been very frustrating so far.

Here's the tutorial I was following: [http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html](http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html)

I have Ubuntu 10.10 x86_64 if that helps.

---

