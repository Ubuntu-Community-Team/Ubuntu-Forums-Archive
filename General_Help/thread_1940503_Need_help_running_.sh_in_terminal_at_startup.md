---
title: "Need help running .sh in terminal at startup"
date: 2012-03-13
forum: General Help
---

### Post by HalfofaLife on 2012-03-13
Hi,
I'm a relatively new Ubuntu and I have a Minecraft server I run on an old box. My question is how do I get the .sh file to auto run in terminal at start-up?

Here is whats in the .sh file:

#!/bin/sh
cd '/home/brock/bukkit_test'
java -Xms1536M -Xmx1536M -jar minecraft_server.jar nogui

---

### Post by gordintoronto on 2012-03-14
What version of Ubuntu? It's easy with Ubuntu Desktop.

---

### Post by HalfofaLife on 2012-03-14
Ubuntu 11.10 (Desktop, not Server)

---

### Post by Habitual on 2012-03-14
> **HalfofaLife said:**
> ...the .sh file to auto run in terminal at start-up?

sudo vi + rc.local
and add
/path/to/java -Xms1536M -Xmx1536M -jar /path/to/minecraft_server.jar nogui

---

### Post by gordintoronto on 2012-03-14
Run Startup Applications, it's pretty straightforward from there.

---

