---
title: "Ubuntu shuts off randomly."
date: 2011-11-02
forum: General Help
---

### Post by LeetNeo on 2011-11-02
I don't know why it does this, I'm running 11.10, and it randomly shuts off when I'm doing like anything. Happened four times, I don't know what's wrong, it puts me off, I'm thinking about moving back to Windows, because this is bothering me a lot. Can anyone help? It shows this black screen with text, it's soo fast I can't read what it says.

-LeetNeo.

---

### Post by searchfgold6789 on 2011-11-02
Is this a fresh install, or have you been running Ubuntu for a while? And can you post the hardware specs, at least?

---

### Post by LeetNeo on 2011-11-02
> **searchfgold6789 said:**
> Is this a fresh install, or have you been running Ubuntu for a while? And can you post the hardware specs, at least?

It's a fresh install with a few applications. It's a Laptop with Pentium Dual Core 2.0GHz, 4GB's of ram, integrated Intel graphics card, and it's called "Gateway NV44".

-LeetNeo.

---

### Post by raja.genupula on 2011-11-02
dmesg >> log.txt

do this in your terminal and post the output of it here between ```
 
``` tags

---

### Post by Immolatus on 2011-11-02
Install "sensors" and run it in the terminal under normal load. Are there any flashing lights(kernel panic)? could just be above critical temps. How old is the machine? is it very dusty?

---

### Post by LeetNeo on 2011-11-02
> **raja.genupula said:**
> dmesg >> log.txt
 
do this in your terminal and post the output of it here between tags
 
I'm not at home at the moment. I'll try it when I get home.
 
> **Immolatus said:**
> Install "sensors" and run it in the terminal under normal load. Are there any flashing lights(kernel panic)? could just be above critical temps. How old is the machine? is it very dusty?
 
The machine never shut down randomly when I used Windows 7 on it. I'm not very good with Linux really. It's probably dusty but never shuts down. Also sorry I'm on a broken keyboard which is vandalised and I can't hit comma. Sorry about the poor grammer.
 
-LeetNeo.

---

### Post by Redcard on 2011-11-02
Are you plugged in or not?  There have been people reporting bugs regarding incorrect reads from the battery, and that can cause the system to poweroff/hibernate if unplugged.

---

### Post by LeetNeo on 2011-11-02
> **Redcard said:**
> Are you plugged in or not?  There have been people reporting bugs regarding incorrect reads from the battery, and that can cause the system to poweroff/hibernate if unplugged.

It's plugged in properly.

-LeetNeo.

---

