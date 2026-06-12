---
title: "ubuntu 10.10 libssl-dev broken"
date: 2010-12-29
forum: General Help
---

### Post by __________ on 2010-12-29
Hi, 

I need help to install libssl-dev in Ubuntu 10.10.

When I do:

apt-get install libssl-dev

I get:

libssl-dev: depends: libssl0.9.8 (= 0.9.8o-1ubuntu4) but 0.9.8o-1ubuntu4.1 will be installed

E: broken packet

I get the same result with Synaptic.

Thanks

---

### Post by ruben_linux on 2010-12-29
i had the same problem and i download the paket of this web: [http://pkgs.org/requires/libssl0.9.8](http://pkgs.org/requires/libssl0.9.8) and after: sudo dpkg -i libssl0.9.8******

i dont remember which was the program that i wanted install. :-)
but this step be good

---

### Post by mc4man on 2010-12-29
Maverick is well past both those versions (- the libssl0.9.8 (0.9.8o-1ubuntu4.1) that's installed and the -dev that's available in your current sources  - libssl-dev (0.9.8o-1ubuntu4)

From changelog
> openssl (0.9.8o-1ubuntu4.3) maverick-security; urgency=low

  * SECURITY UPDATE: ciphersuite downgrade vulnerability
    - openssl-CVE-2010-4180-secadv_20101202-0.9.8.patch:
      disable workaround for Netscape cipher suite bug in ssl/s3_clnt.c
      and ssl/s3_srvr.c
    - CVE-2010-4180

 -- Steve Beattie <sbeattie@ubuntu.com>  Thu, 02 Dec 2010 16:24:31 -0800

openssl (0.9.8o-1ubuntu4.2) maverick-security; urgency=low

  * SECURITY UPDATE: TLS race condition leading to a buffer overflow and
    possible code execution. (LP: #676243)
    - patches/debian/openssl-CVE-2010-3864-secadv_20101116-0.9.8.patch:
      stricter NULL/not-NULL checking in ssl/t1_lib.c
    - CVE-2010-3864

 -- Steve Beattie <sbeattie@ubuntu.com>  Tue, 16 Nov 2010 10:07:49 -0800
Open up Software Sources and make sure the under the 'Updates' tab that the first 2 are enables (security and updates - see screen

Then click close and reload 
If they were enabled then run from a terminal
sudo apt-get update

If the newest versions of both don't show up then maybe try a different server (use the main - screen 2, again - close, reload or run update command

If software sources isn't in your menu then open synaptic - Settings - Repositories

---

### Post by __________ on 2010-12-29
Solved!
Thanks a lot!

---

### Post by mihirgokani007 on 2011-01-29
Thanks :P !!! Enabling updates worked.

> **mc4man said:**
> Maverick is well past both those versions (- the libssl0.9.8 (0.9.8o-1ubuntu4.1) that's installed and the -dev that's available in your current sources  - libssl-dev (0.9.8o-1ubuntu4)

From changelog

Open up Software Sources and make sure the under the 'Updates' tab that the first 2 are enables (security and updates - see screen

Then click close and reload 
If they were enabled then run from a terminal
sudo apt-get update

If the newest versions of both don't show up then maybe try a different server (use the main - screen 2, again - close, reload or run update command

If software sources isn't in your menu then open synaptic - Settings - Repositories

---

### Post by dhunnapotha on 2011-03-08
thanks.. the update thing helped !!

---

### Post by cepete02 on 2011-04-13
> **mc4man said:**
> Maverick is well past both those versions (- the libssl0.9.8 (0.9.8o-1ubuntu4.1) that's installed and the -dev that's available in your current sources  - libssl-dev (0.9.8o-1ubuntu4)

From changelog

Open up Software Sources and make sure the under the 'Updates' tab that the first 2 are enables (security and updates - see screen

Then click close and reload 
If they were enabled then run from a terminal
sudo apt-get update

If the newest versions of both don't show up then maybe try a different server (use the main - screen 2, again - close, reload or run update command

If software sources isn't in your menu then open synaptic - Settings - Repositories

THANKS! your directions worked like a charm! (so much easier than some of the other postings)!

Carl

---

### Post by JeffreySun on 2012-04-29
It's really helpful, thanks !

---

### Post by oldos2er on 2012-04-29
Old thread closed.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

