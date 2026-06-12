---
title: "Lost root and main user's password while trying to install fingerprint reader"
date: 2011-09-05
forum: General Help
---

### Post by spicyfish on 2011-09-05
==========
First, some background info:

I have two accounts: matthew and myguest
matthew is my main account and is passworded.
myguest is a reduced priviledge account that requires no password to log in.

I configured matthew's password and root password to be different, and made it so I log in with matthew's password but sudo will ask for root password.

==========
The problem:

While logged into matthew, I tried to follow the guide here
[https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger)
In particular the section "Quick Howto for Ubuntu 10.04"
I believe the last two commands failed (I did the last one anyway, even though the second last one failed)
I may have run other commands/did other stuff after that, but I think they probably weren't important.

A few minutes later, I tried to run a command with sudo (asks for root password) and my password would be wrong every time. I logged out and tried to log back in, but it would be wrong every time as well (asks for matthew's password), so now I am locked out of that account and root.

I am running 10.04.3
I am currently on myguest.
matthew is still running right now.

This is a fresh install of ubuntu (few days old), but I have spent the last few days configuring it and installing drivers, etc. and would like to not have to do it all again. Worst case, I could format the partition and start over, as I have all my critical data backed up on an external hard drive.

Is there any way to fix this?

---

### Post by haqking on 2011-09-05
> **spicyfish said:**
> ==========
First, some background info:

I have two accounts: matthew and myguest
matthew is my main account and is passworded.
myguest is a reduced priviledge account that requires no password to log in.

I configured matthew's password and root password to be different, and made it so I log in with matthew's password but sudo will ask for root password.

==========
The problem:

While logged into matthew, I tried to follow the guide here
[https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger)
In particular the section "Quick Howto for Ubuntu 10.04"
I believe the last two commands failed (I did the last one anyway, even though the second last one failed)
I may have run other commands/did other stuff after that, but I think they probably weren't important.

A few minutes later, I tried to run a command with sudo (asks for root password) and my password would be wrong every time. I logged out and tried to log back in, but it would be wrong every time as well (asks for matthew's password), so now I am locked out of that account and root.

I am running 10.04.3
I am currently on myguest.
matthew is still running right now.

This is a fresh install of ubuntu (few days old), but I have spent the last few days configuring it and installing drivers, etc. and would like to not have to do it all again. Worst case, I could format the partition and start over, as I have all my critical data backed up on an external hard drive.

Is there any way to fix this?

you can reset following this [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Root is and should remain disabled in Ubuntu.

---

### Post by spicyfish on 2011-09-05
This does not work. It successfully allows me to change password, but when I try to boot up normally and log in it will fail.

---

### Post by spicyfish on 2011-09-05
Solved! Not sure how to mark as solved.

What I did:
In the recovery mode's shell prompt it allowed me to log in as root, and I basically just undid everything in the tutorial. Can now log in again in normal bootup.

Thanks haqking for replying/leading me to use recovery mode.

---

### Post by haqking on 2011-09-05
> **spicyfish said:**
> Solved! Not sure how to mark as solved.

What I did:
In the recovery mode's shell prompt it allowed me to log in as root, and I basically just undid everything in the tutorial. Can now log in again in normal bootup.

Thanks haqking for replying/leading me to use recovery mode.

No problem, you are welcome.

use the thread tools menu to mark as solved.

Cheers

---

