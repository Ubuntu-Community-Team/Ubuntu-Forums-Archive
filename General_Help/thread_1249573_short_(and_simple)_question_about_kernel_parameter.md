---
title: "short (and simple?) question about kernel parameters"
date: 2009-08-25
forum: General Help
---

### Post by P4man on 2009-08-25
Hi,

If you boot off a live cd, you can edit kernel parameters with F6. The default ones are:

"blablablab/casper/initrd.gz quiet splash --"

My question relates to the dashes "--" at the end. Do they mean anything? If you want to add other parameters, should you put them before or after the dashes, or remove them, or does it not matter?

thx.

---

### Post by dcstar on 2009-08-26
> **P4man said:**
> Hi,

If you boot off a live cd, you can edit kernel parameters with F6. The default ones are:

"blablablab/casper/initrd.gz quiet splash --"

My question relates to the dashes "--" at the end. Do they mean anything? If you want to add other parameters, should you put them before or after the dashes, or remove them, or does it not matter?

thx.

a) Before.

b) Don't know.

c) Have a look here: [http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

---

### Post by P4man on 2009-08-26
Thanks, but I can't see anything on the dashes in that link. The community documentation here seems to suggest putting the parameters *after* the dashes:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

if it matters at all.  I'll just test and see if it makes any difference.

---

