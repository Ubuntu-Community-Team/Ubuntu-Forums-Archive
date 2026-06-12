---
title: "CMD on linux?"
date: 2010-03-25
forum: General Help
---

### Post by X1R1 on 2010-03-25
Hi, I need to run some tests from my ubuntu machine and I need the windows command line (cmd) to do it. how can I install it ubuntu? where can I found the installer for this?

is that even posible? :popcorn:

thanks in advance for the help, I imagine it has something to do with wine but I have no idea how to proceed

---

### Post by d3v1150m471c on 2010-03-25
For the best results you'd need to run xp from a virtualbox and use its native cmd. There are emulators but arguably not so stable.

---

### Post by srs5694 on 2010-03-25
What do you need this for? It's conceivable that there's a better Linux-native solution, such as using bash or some other Linux-native shell. For that matter, it's possible that whatever your goal is not achievable in Linux via the Windows CMD.EXE!

That said, the cmd.exe program that comes with WINE seems to work for me in a cursory test, and I've found some online comments that suggest that Windows' own CMD.EXE works in WINE, too. See [this Wiki entry,](http://wiki.jswindle.com/index.php/Cmd) for instance.

In case you didn't know, [WINE](http://www.winehq.org) is Linux's Windows compatibility layer. It can run many, but by no means all, Windows programs.

---

### Post by X1R1 on 2010-03-26
I do tought about virtualbox, but I think maybe its a better lightweight solution for my test. Turns out that on my work network If I telnet from a linux machine I get rejected from the host, but If I telnet via windows it works fine. So I wanted to test this with a windows cmd on linux to see if that works out :D

---

### Post by srs5694 on 2010-03-26
The shell (in Linux terminology) you use to launch a program is very unlikely to make any difference to a Telnet server. It's conceivable that the Telnet client program you use would make a difference, but even that strikes me as being unlikely. The most likely cause is security settings on the Telnet server. It could be set to accept logins from only a handful of IP addresses, and your Linux system isn't among the ones that are authorized. You should speak to whoever administers that system and ask about this. If I'm right, the fix on the server should be easy, and a fix on your end will be next to impossible, short of changing your IP address in a way that's almost guaranteed to cause problems down the line.

BTW, use of Telnet is generally discouraged because it's very insecure. It might be tolerable on an isolated network, but as a general rule, SSH is the preferred solution for remote text-mode logins.

---

