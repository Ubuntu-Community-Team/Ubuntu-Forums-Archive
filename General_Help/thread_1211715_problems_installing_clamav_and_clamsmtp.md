---
title: "problems installing clamav and clamsmtp"
date: 2009-07-12
forum: General Help
---

### Post by ceilingcat on 2009-07-12
I have been trying for two days to get clamsmtp running with Postfix.
Uninstall and reinstall .. searching the web for solutions to the continuous errors which
keep occurring.

There are many guides on the web to installing clamsmtp, but they each seem to be a little different from each other, and none I have tried so far seem to be helpful to me.

Here is the error that now confronts me

> kitchen-table postfix/error[3636]: A5E5F321EC: to=<fake@fake.net>, orig_to=<fred>, relay=none, delay=2.1, delays=1.7/0.01/0/0.44, dsn=4.4.2,status=deferred (delivery temporarily suspended: lost connection with 127.0.0.1[127.0.0.1] while receiving the initial server greeting)Can anybody advise me on why Postfix cannot communicate with a mail client after clamsmtp is installed?

---

### Post by mthalis on 2009-07-12
Read this
[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

---

### Post by ceilingcat on 2009-07-13
> **mthalis said:**
> Read this
[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

Ok mthalis .. thanks for your reply. The link you posted is one site I had previously consulted.  Moreover, it does not address clamsmtp at all, which is where I think my problems lie.

If I understand correctly, clamsmtp intercepts mail before it gets to Postfix, clamav scans it and then forwards it to Postfix for delivery after stripping out any viruses it finds.   I am guessing that Postfix is not listening to the correct port. I have tried many variations of the port settings, but I cannot make it work.

---

### Post by ceilingcat on 2009-07-13
Weirdness besets Ubuntu.   I installed clamsmtp on a fresh virtual Ubuntu machine and the installation worked perfectly first time with the parameters given on [http://howto.seewebsolutions.ro/?x=cat:7&paged=2](http://howto.seewebsolutions.ro/?x=cat:7&paged=2)

The info is right towards the bottom of the page.

I have used the same method on my desktop box but to no avail.  

The latest error I am getting is  > dark_matter clamsmtpd: 100001: CLAMAV: couldn't connect to: /var/run/clamav/clamd.ctl: Permission denied

grrrr

---

