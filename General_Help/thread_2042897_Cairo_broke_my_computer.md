---
title: "Cairo broke my computer"
date: 2012-08-15
forum: General Help
---

### Post by JPR65 on 2012-08-15
I am using ubuntu 12.04. I installed cairo, then, it crashed on me, so I restarted my machine. When I restarted, nothing loaded (I mean no task bar, side bar). Thus, I can't access any applications--or anything (I mean, I can't even open a terminal!). As I am fairly new to linux, I might be missing something stupid. I'm pretty sure that if I can open the Software Center, I could uninstall cairo, and fix whatever problem I'm having... Unfortunately, I can't open Software Center.  As an alternative, I could reinstall linux...but that seems like a last resort. Any advice?

---

### Post by ubudog on 2012-08-15
Hi there, try this.  Press CTL+ALT+T to open a terminal.  Type the following commands to remove Cairo and reset Unity.

```
sudo apt-get remove cairo-dock
```
Enter your password, and wait for that to finish.  You may have to press 'Y' to accept.

```
unity --reset
```
This will reset Unity.

Hope that helps,
ubudog

---

### Post by cortman on 2012-08-15
It's likely the cairo composite manager. Ubudog gives the right solution.

---

### Post by JPR65 on 2012-08-15
I couldn't get the terminal to open using the shortcut you gave. I did some investigation, and got the shortcut cnrt-alt-f1. This worked, and I was able to access a fullscreen terminal. The first command you gave me worked, and I removed cairo. Then I tried the second command, but it said that unity was not installed? I then rebooted linux, but got the same result as before I got rid of cairo. What now?

---

### Post by JPR65 on 2012-08-15
Ok. I installed unity, then reset it using the commands you gave me. Voila! Everything is back to normal! Thanks for all the help!

---

### Post by ubudog on 2012-08-15
> **JPR65 said:**
> Ok. I installed unity, then reset it using the commands you gave me. Voila! Everything is back to normal! Thanks for all the help!

Glad that worked.  :)

---

