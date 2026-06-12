---
title: "Network testing/emulation"
date: 2010-01-20
forum: General Help
---

### Post by furry_freak on 2010-01-20
Hi. I'm not sure whether this is the right place to post this question, but I'm writing a program (in java) that's networked and I need to test the network code. The problem is that I only have one computer and all other computers I have access to are strictly fire-walled.

Basically, I need a way to test the network app on one computer. I've tried using the 'tunctl' tool ('uml-utilities' package) and 'brctl' ('bridge-utils' package) to create two virtual network devices that are bridged together. Unfortunately, I haven't been able to ping one virtual device from the other.

Does anyone know of an alternative method to do this?

(if anyone knows the above tools quite well, I can provide more detail on how I set it up)

---

### Post by zollie on 2010-01-20
what do you mean when you say "test the network?"

what EXACTLY are you trying to do??

---

### Post by furry_freak on 2010-01-20
> **zollie said:**
> what do you mean when you say "test the network?"

what EXACTLY are you trying to do??

I just want to test my programs network connection by having two instances of it running on the same computer, but both using a different network device. I only have one network card, so one of the network devices would have to be emulated or something.

Sorry for not being clear.

---

### Post by synapsys on 2010-01-20
You could use 127.0.0.1 to connect to the host machine, or possible run a virtual machine with an un-bridged ethernet connection.

---

### Post by zollie on 2010-01-20
> **furry_freak said:**
> I just want to test my programs network connection by having two instances of it running on the same computer, but both using a different network device. I only have one network card, so one of the network devices would have to be emulated or something.

Sorry for not being clear.

are you able to assign different TCP listen ports to your application?

In that case, just assign different ports & run 2 instances of the app at the same time on the same box.

you do not need to emulate two different network devices.

---

### Post by furry_freak on 2010-01-20
> **synapsys said:**
> You could use 127.0.0.1 to connect to the host machine, or possible run a virtual machine with an un-bridged ethernet connection.

I tried using the loopback address (127.0.0.1), but that didn't work. I could use a VM, but it's a bit awkward... If I can't find a more convenient way, then I guess that's my only option

---

### Post by zollie on 2010-01-20
> **furry_freak said:**
> I tried using the loopback address (127.0.0.1), but that didn't work. I could use a VM, but it's a bit awkward... If I can't find a more convenient way, then I guess that's my only option

are these client/server apps or just server apps?  Or client only?

you gotta provide more details, man.

---

### Post by furry_freak on 2010-01-20
> **zollie said:**
> are you able to assign different TCP listen ports to your application?

In that case, just assign different ports & run 2 instances of the app at the same time on the same box.

you do not need to emulate two different network devices.

... ](*,) That didn't even occur to me.

Well, the connection works :) but my codes a little buggy :(

---

