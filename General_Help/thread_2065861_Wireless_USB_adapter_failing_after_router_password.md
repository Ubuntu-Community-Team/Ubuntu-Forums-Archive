---
title: "Wireless USB adapter failing after router password change."
date: 2012-10-03
forum: General Help
---

### Post by MutantJohn on 2012-10-03
Hello Ubuntu Community,

I am in dire need of your help. I have a wireless USB adapter and it was working perfectly fine until my roommate decided to change the password. And ever since then,it's been trying to connect forever, repeatedly asking me for the password, and never actually connecting to our wireless router.

I've tried reinstalling the driver software, changing kernels, restarting the computer, shutting down and then powering on the computer. I've tried forgetting the network and re-entering settings, re-typing in passwords manually but none of this has done anything. And yes, I've reset the router.

I had a working system and a simple password shift from a computer that wasn't my own is causing a freak out. I mean, a password shift on the router's security.

It's some ASUS wireless adapter and even putting in the wrong password doesn't seem to matter here. Even worse, I'm literally the only one out of my entire co-op to be having this much trouble. Or any trouble, for that matter.

I've tried the whole lsusb command and it's recognized by the computer as well. The adapter is still responsive to commands as in, it'll shift trying to connect to the networks that I tell it to, it'll disable itself when I want it to and if I unplug, my computer notices that it's missing. Well, sometimes it doesn't and it gets stuck in this uninterruptible loop so I have to manually hard restart my computer but for all intents and purposes, the adapter is fine.

It's a functioning system that's running into some very odd and very, very, very aggravating problems.

So please Ubuntu Forum community, can you help an angry nerd out? Literally, the only thing that was supposed to have been changed was the password.

I think the error occurred because the password was reset while the adapter was still connected but I can't imagine how though.

---

### Post by albandy on 2012-10-03
> **MutantJohn said:**
> Hello Ubuntu Community,

I am in dire need of your help. I have a wireless USB adapter and it was working perfectly fine until my roommate decided to change the password. And ever since then,it's been trying to connect forever, repeatedly asking me for the password, and never actually connecting to our wireless router.

I've tried reinstalling the driver software, changing kernels, restarting the computer, shutting down and then powering on the computer. I've tried forgetting the network and re-entering settings, re-typing in passwords manually but none of this has done anything. And yes, I've reset the router.

I had a working system and a simple password shift from a computer that wasn't my own is causing a freak out. I mean, a password shift on the router's security.

It's some ASUS wireless adapter and even putting in the wrong password doesn't seem to matter here. Even worse, I'm literally the only one out of my entire co-op to be having this much trouble. Or any trouble, for that matter.

I've tried the whole lsusb command and it's recognized by the computer as well. The adapter is still responsive to commands as in, it'll shift trying to connect to the networks that I tell it to, it'll disable itself when I want it to and if I unplug, my computer notices that it's missing. Well, sometimes it doesn't and it gets stuck in this uninterruptible loop so I have to manually hard restart my computer but for all intents and purposes, the adapter is fine.

It's a functioning system that's running into some very odd and very, very, very aggravating problems.

So please Ubuntu Forum community, can you help an angry nerd out? Literally, the only thing that was supposed to have been changed was the password.

I think the error occurred because the password was reset while the adapter was still connected but I can't imagine how though.

Can you try the same adapter running other operating system? If works is a driver problem, if not, probably they blacklisted your mac address or your adapter is broken.

I never saw connectivity problems by a password change, maybe they changed the auth protocol or as I said before they blacklisted your mac address.

---

### Post by MutantJohn on 2012-10-03
Huh, I tried using the adapter on my girlfriend's Mac but I don't know how to do it.

But I did look it up and my MAC address was reset to a string of 0's so I used the ```
ifconfig -a
``` command and I got a non-zero string so I tried plugging that in and that didn't work out either.

So I think it's got a valid hardware address but stil, nothing is happening.

It's okay, I think I might be able to try using ethernet again but I'd really, really like this to work with wireless.

And after enough time of trying, my computer will finally just give up trying to connect. Such a world I live in T_T

---

### Post by MutantJohn on 2012-10-03
Alright, I got my ethernet cable set up instead. I never thought I'd actually be able to do it but the most ghetto looking ethernet configuration does the job. Yay!

You're probably right though, the adapter itself is broken. I think it might've been damaged from a power surge not too long ago. Oh well, my beast of a computer is fine and that's all that fundamentally matters.

---

