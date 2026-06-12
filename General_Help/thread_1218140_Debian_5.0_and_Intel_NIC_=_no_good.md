---
title: "Debian 5.0 and Intel NIC = no good"
date: 2009-07-20
forum: General Help
---

### Post by Krupski on 2009-07-20
Hi all,

For the heck of it, I tried to install Debian 5 on a USB stick. All went well, except that there is no driver for my NIC (Intel 82567-LM on a DQ45CB motherboard).

I downloaded the latest driver source from Intel... but GCC isn't part of the Debian install, so I can't compile the source!

And without a network connection, I can't download and install "build-essential".  :(

Does anyone know a way around this Catch-22?

Thanks!

-- Roger

---

### Post by chriskin on 2009-07-20
why don't you download the debs from a working connection and then go to your computer, solve the network thing and work from there ok?
ubuntu allows you to download the debs from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
most probably debian allows you to do that too

---

### Post by snowpine on 2009-07-20
build-essential is on the Debian install CD-ROM.

---

