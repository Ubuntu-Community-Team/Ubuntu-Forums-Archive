---
title: "Hmmm... Wake on LAN from sleep?"
date: 2009-10-19
forum: General Help
---

### Post by GermanMafia on 2009-10-19
I recently converted my Windows server to an Ubuntu server, but as I'm paying for electricity now having the computer on all the time isn't a very effective approach. Whenever the Ubuntu computer goes to sleep, it doesn't wake up when I try to connect over the network. Surely there's an easy fix to this, but I've searched far and wide and all I've come across is sending magic packets from another application, something that I don't really want to do as my roommates wouldn't be able to figure it out. I just want the computer to wake up whenever someone tries to access files over the network. Thanks!

---

### Post by sedawk on 2009-10-19
As you found out wake-on-lan requires magic packets to be
send to wake up the server.
What you need is a server that doesn't take much energy
while being idle.
E.g. a PC with onboard graphics that only runs in text
mode, not graphic mode and that is configured (Bios+OS)
to save power when idle by turning off idle hardware and
switching the CPU in a low power mode.

What you are looking for is a mate that is sitting
fully dressed and idle in front off the TV and waiting
for someone to pick him up for a pizza.
What you are not looking for is a mate that is
sleeping and has to get a shower first and also
has to put on make-up before leaving the house.

---

### Post by GermanMafia on 2009-10-19
I would love to get an energy saving PC, but as usual, cash is tight. I also will eventually be moving this PC to the media area when I bring my projector, so it needs some power as well.

---

### Post by Giblet5 on 2009-10-19
> **sedawk said:**
> What you are looking for is a mate that is sitting fully dressed and idle in front off the TV and waiting for someone to pick him up for a pizza.
What you are not looking for is a mate that is sleeping and has to get a shower first and also has to put on make-up before leaving the house.

How do I install that first one from a command line?

---

