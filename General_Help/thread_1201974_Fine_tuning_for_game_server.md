---
title: "Fine tuning for game server"
date: 2009-07-01
forum: General Help
---

### Post by GeoMoon5 on 2009-07-01
Hey everyone,

What are some things I can do to fine tune my Linux server settings to help make my game servers a more fun gaming experience for players? 

Stuff like adjusting OS settings to reduce latency, free up processor load by disabling unused applications, etc. I'm running 32 bit Ubuntu server 8.10 and am hosting several srcds applications on it. Four game servers that are HL2 modifications to be exact.

Someone mentioned setting the tcp/ip socket limits up to reduce net overhead. I've never even heard of that, but that's the kind of stuff I'm hoping to find out about to help fine tune the game server performance.

This server is only used for hosting the game servers, so no need to worry about certain fine tuning hampering other applications.

Any help would be greatly appreciated! Thanks!  =D

---

### Post by t4thfavor on 2009-07-01
If you don't install other junk on your server, then you already have a pretty optomised environment. Its using the server kernel, and should be about as good as it gets as far as serving out packets.

Im sure there are a few things to disable, check out /etc/init.d/ and see if there are any things in there that you are CERTAIN you do not use. Be careful though as you can hose your system pretty easily be turning off the wrong stuff.

---

