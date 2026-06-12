---
title: "telnet quitting oddly"
date: 2010-08-17
forum: General Help
---

### Post by embolalia1187 on 2010-08-17
This is an incredibly strange problem.
I've been trying to figure out how to telnet into an AIX server from a Linux client at work for years. I've run into countless problems with keys not working and whatnot. I finally found the "wy60" package, which properly emulates a Wyse60 terminal, and the gnome-terminal setting to properly set the backspace and delete keys.
Cutting to the chase, I set up a profile that changes the font and automatically runs "wy60 -c telnet 192.168.1.1", the command to emulate a Wyse60 terminal and telnet to the server. Last week, just after having installed wy60, this worked. With no other windows open, I open a shortcut/launcer with command "gnome-terminal --tab-with-profile=HBD", that being the profile in question. Last Friday, that worked perfectly. I come in today, and suddenly it doesn't.

The problem seems related to the changed font. Leaving it with the default, things work fine (but it's too small to work with all day). Changing it to a larger monospace font and then opening the profile, I can get to the AIX login prompt. If I log in as a non-root user, it's supposed to bring me to a text menu where I can select between the main application or an AIX prompt. With the changed text, it is as it starts to display this screen that it exits with a "Connection closed by foreign host" error. If I log in as root, it takes me directly to a command prompt, where I can enter the command for the application, and it works fine. Of course, I don't want to log in as root if I don't have to, especially not over telnet.

Now here's a little oddity that just makes it all the more bizarre. I have a virtual machine that I've been setting up, to eventually use to make Linux install CDs for the office. Last Friday, I tried the above in both the VM and regular machine. Rather than shutting down the VM, I simply saved it's state. So when I went back to it today, the VM was exactly as if it was still on from Friday. In the VM, the gnome-terminal shortcut and profile still work perfectly. So either there is something different about the VM (which is the exact same version of the exact same distro, with a few different programs), or something in the real machine changed when I shut it down and brought it home (it's a laptop) over the weekend.

---

