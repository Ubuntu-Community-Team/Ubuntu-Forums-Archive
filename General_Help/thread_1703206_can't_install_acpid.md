---
title: "can't install acpid"
date: 2011-03-09
forum: General Help
---

### Post by remush on 2011-03-09
When executing the following command

> sudo apt-get install acpid

I get the following response

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package acpid

Its a default install of ubuntu server 9.10 with default sources.list for australia.

Its a very old computer though, here are the specs

Pentium 2, 333MHz
Motherboard Chipset Intel 82440LX/EX
ACPI is : Not Supported according to some system detection software I have, is that the reason ?

Is there another way to get the computer to shutdown safley when the powerbutton is pressed, instead of power loss occuring ?

---

### Post by dcstar on 2011-03-09
> **remush said:**
> When executing the following command

> sudo apt-get install acpid

I get the following response

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package acpid

Its a default install of ubuntu server 9.10 with default sources.list for australia.

Its a very old computer though, here are the specs

Pentium 2, 333MHz
Motherboard Chipset Intel 82440LX/EX
ACPI is : Not Supported according to some system detection software I have, is that the reason ?

Is there another way to get the computer to shutdown safley when the powerbutton is pressed, instead of power loss occuring ?

You cannot install packages that **do not exist**.

If you have ancient hardware that does not support modern power off functions, then that is it.

---

