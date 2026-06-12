---
title: "Shutdown all computers on network"
date: 2010-08-27
forum: General Help
---

### Post by Monotoko on 2010-08-27
Hi there, 

I am looking to run a script when the shutdown on my main computer is initiated and I need this script to be run before my network interface is taken down.

Basically the main computer stays on, and at night I used to have to go downstairs in order to switch the other computers off and sometimes forget to switch my netbook off.

I then wrote a script and it works quite well by ssh'ing into each and shutting down, but because I am lazy and figured it would be kinda cool, I am looking to make it shut everything down automatically once the main one is shutdown.

Anyone have any ideas?

Daniel

---

### Post by AlphaLexman on 2010-08-27
I don't think **ANY** 'root' user has that much power!

---

### Post by holiday on 2010-08-27
You could install a cron on each machine to ping your main server and then shutdown on fail. 

Say every fifteen minutes? 

It *might* work. It may have some unintended consequences though. You may be fabulously coding on your laptop and then BANG - b/c your server has choked on some undigested beef. 

My hunch is that this is something you don't want to do. We have to wash dishes, brush our teeth... Why not set an activity timeout to put the babies to sleep?

Maybe I'm missing something?

---

