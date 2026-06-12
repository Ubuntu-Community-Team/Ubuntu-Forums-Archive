---
title: "Problem connection vis ssh to another Ubuntu machine"
date: 2012-05-31
forum: General Help
---

### Post by pratikmoona on 2012-05-31
Hi,

I recently installed Ubunutu 12.04 on two different machines. I want to SSH into the other from the first. So, I installed openssh server on the one I wish to connect to.

The installation went fine. I am able to log on to the localhost from that machine. But when I try to connect from the other machine I get the following message:
```
Permission denied, please try again.
```

Please help!

---

### Post by albandy on 2012-05-31
It asks you for a password before permission denied?
If this is the case, ensure you are using the correct user.

For example.

If my user in computer1 is username1 and in computer2 is username2, if I want to connect from computer1 to computer2 I will do:

ssh username2@computer2

And if I want to connect from computer2 to computer1 I will do:

ssh username1@computer1

---

### Post by pratikmoona on 2012-05-31
Hi,

Yeah, it asks for a password. I am asking for the right user (Any user on the other machine is a valid user right?).

My command is
[HTML]user@ipaddress[/HTML]

---

### Post by papibe on 2012-05-31
> **pratikmoona said:**
> Any user on the other machine is a valid user right?

Hi pratikmoona.

Not really, there are several predefined users (including root) that can't ssh into your machine by default.

Are you trying to connect from and to normal users?

Regards.

---

### Post by pratikmoona on 2012-05-31
> **papibe said:**
> Are you trying to connect from and to normal users?

Yes, the users I am trying to connect from and to are normal users. I am able to ssh using the same user to localhost from the second machine.

---

### Post by steeldriver on 2012-06-01
you can invoke ssh in verbose mode - that may show you where it's failing (or at least let you see how far it gets through the connection process)

```
ssh -v[v[v]] user@xxx.xxx.xxx.xxx

```

(up to 3 vs) 

regards

---

### Post by Sularco on 2012-06-01
The relevant entries from /var/log/auth.log should also give you a good idea what the cause of the problem is.

---

