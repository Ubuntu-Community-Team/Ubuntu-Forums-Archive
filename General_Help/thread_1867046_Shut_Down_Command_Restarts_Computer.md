---
title: "Shut Down Command Restarts Computer"
date: 2011-10-22
forum: General Help
---

### Post by spacestation on 2011-10-22
When I shut down the computer, it shuts off for a second and restarts automatically.:confused:

I want to stress the strangeness of this, is that it appears that the computer has shutdown for a few seconds. After I finally imagine that the computer is in fact powered down, suddenly it lights up and starts without any provocation. 

The computer completly turns off and the light goes out and then it turns back on all by itself,

At the bios screen the power button can be pressed to facilitate complete shutdown. Problem is in Gnome shutdown command.

The best I could do was to use: "sudo shutdown now"  and it halts to a safe point to hit the physical shutdown button on the computer. One simple solution would be to basically change the command of the Gnome Shutdown button to effect "shutdown now" instead of "shutdown -h now", because halting normally has a strange delayed restart of the computer.

I tried editing gconf-editor to make the gnome-button change its value, but there were only a few options like "interactive" and "shutdown" without interactive questioning.

The computer is an Emachine. It is about 4 years old, and in fairly good condition. I installed Ubuntu to get rid of a virus infested Windows XP. Other than this strange shutdown anomaly, Ubuntu sped up the computer and made it otherwise into a top-performance machine again.

I ask myself: how does Linux control the shutdown of a computer? I think the answer is the kernel finds the hardware that controls physical power-off, and thus relays the "shutdown -h now" command to the hardware. So it could be related to the kernel not finding my emachine's hardware. I also use Slackware and know that upgrading the kernel sometimes fixes a bug like this. Currently using Lucid Lynx just upgraded.

---

