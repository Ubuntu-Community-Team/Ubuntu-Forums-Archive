---
title: "Help with intructions"
date: 2012-05-05
forum: General Help
---

### Post by layers on 2012-05-05
I am trying to make a LAN game of Warcraft 3 between an Ubuntu and XP. We are in the same LAN (we can play Age of Empires 2 together with no difficulties). However, when Ubuntu tries to join a game, it cannot see any hosted games. If Ubuntu hosts, XP cannot see games. I found that this is a known problem on Wine's website, but I am not sure how to do the instructions.

According to the instructions, I can add a gateway, OR to route some address to the my local network. Which one should I do for minimal effect on the network (I don't want to mess up anything)?

> How to fix problems related to the Local Area Network option?

If you try to play using the Local Area Network option, and do not see a game hosted from your machine on another or vice versa, and you are in the same subnet, this is likely caused by not having a default gateway. The game relies on sending UDP packets to the broadcast address and Linux will not send them unless there is a default gateway or another rule to handle them. To fix it, there are two methods:

Add a default gateway. 
- OR - 
Route 255. 255. 255. 255 to your local network.

---

