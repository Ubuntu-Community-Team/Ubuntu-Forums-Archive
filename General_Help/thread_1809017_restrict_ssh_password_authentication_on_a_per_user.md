---
title: "restrict ssh password authentication on a per user basis"
date: 2011-07-21
forum: General Help
---

### Post by androssofer on 2011-07-21
Hi,

I have two accounts on my Ubuntu machine, 1 is a restricted account that friends can use and another is mine and is used to administer the system etc etc...

is it possible to restrict ssh so public key authentication is required for my account, but either is allowed for the restricted account?

i read the ssh man page, but wasn't able to understand how to use patterns in the config file to achieve this...

---

### Post by Drenriza on 2011-07-21
So you want ssh to apply to you but not your guest account? Whats the deal in that, then you can make a telnet guest account instead.

Personally i administrate this on router level and not server level.

---

### Post by androssofer on 2011-07-21
well I want public key authentication on mine to make it more secure. the restricted account is basicly only used for internet forwarding. so friends wanting to forward internet only have to type a password, but if I wanna administer(not done often) stuff etc I need to use a public key connection.

---

### Post by androssofer on 2011-07-21
anyone?? :-(

---

