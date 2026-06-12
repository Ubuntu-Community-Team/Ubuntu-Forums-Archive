---
title: "Recovery of an ebox server"
date: 2010-01-24
forum: General Help
---

### Post by jamesr on 2010-01-24
Hi All,

This may not the right forum to ask this question, But I have a problem with my eBox server. Suddenly I cannot login to the programme, I receive an error
Secure Connection failed
SSL received a record that exceeded the maximum permissible length
(Error Code : ssl_error_rx_record_too_long)
I also noted that Apache response is very slow, response to the home page is much too long.

I Rebooted and noted errors during the bootup
open: permission denied
* Starting ebox    "xxx"                                                   [OK]
open: permission denied

Then repeats with another " process " in place of the "xxx"

Eventually boots in Xubuntu 8.04 LTS version, and still the slowness of Apache and the SSL error.

I also noted the majority is that one of the hard drives is starting to fail and tells I need to backup data soon.

I can see the /home directory but I cannot copy the samba directory (permission problems). Gradually I am recovering the rest of the system on to USB HD but I DO NEED to copy the Samba  directory. HOW!!!

So I can rebuild the total system.

I can also boot into a Ubuntu 8.04 LTS live CD and I also have permission problems. Can I  get round the permission problem by using the CLI terminal and the sudo command and if so how to recover full directory.

Regards
Jim

---

### Post by essexboyracer on 2010-02-11
Have you tried the ebox forum? What did you do last on the ebox? isn't there a root login that is setup intiially during install (on v1.4 at least)

---

### Post by jamesr on 2010-02-13
Hi,

Thanks for the reply, I managed to recover what I needed to recover. I use Mondo as backup, so I was able to using afio, recover what I needed. Unforetunately because of some the changes that ebox made to the system, I was unable to have internet access therefore no Ubuntu or mondo updates on the server but the rest of the network was OK. That was one of the reason that I asked here as well.

Thanks for the reply. Are you an ebox user?

---

