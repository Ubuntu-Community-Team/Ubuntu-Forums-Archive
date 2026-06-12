---
title: "`passwd` for ActiveDirectory account gives &quot;Authentication token manipulation error&quot;"
date: 2010-06-15
forum: General Help
---

### Post by gmoore777 on 2010-06-15
Question:

does anyone have `passwd` working for ActiveDirectory accounts on
64-bit LucidLynx using just winbind (not Likewise-Open)?

(Note: i am not interested in `passwd` working for local linux accounts nor am I interested in `passwd` working for non-LucidLynx machines.)

It fails for us:
$ passwd
Changing password for DOMAIN\first.last
(current) NT password:
passwd: Authentication token manipulation error
passwd: password unchanged
$

Everything else is fine with the 30+ 64-bit LucidLynx machines
in regards to logging into the Console, ssh-ing in, accessing Samba shares, etc ( `passwd` works fine on the 32-bit HardyHeron machines that we still have around. Those installations leveraged Likewise-Open. We do NOT want to use Likewise-Open for our LucidLynx installations.)

---

