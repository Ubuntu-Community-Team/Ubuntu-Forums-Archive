---
title: "Gnome Term + Vim = shortcut conflict"
date: 2012-03-18
forum: General Help
---

### Post by gennoveus on 2012-03-18
Hi,

This seems like a common problem but I wasn't able to find anything to help me on the internet. I apologise in advance if I have repeated a question or have put this question in the wrong forum.

Right, on to the question, then:

I've decided to learn Vim and am enjoying it, but I am being frustrated by a shortcut conflict:
[LIST]
[*]Gnome Terminal's find command: "ctrl-shift-f"
[*]Vim's "scroll forward one screen" command: also "ctrl-shift-f"
[/LIST]

Gnome terminal intercepts the shortcut and opens the find dialog box ... does anyone know how to disable the command or is there some sort of workaround?

Thankyou

---

### Post by accessgranted on 2012-03-18
I believe you have to purge the menu. Im not sure of any other way.
apt-get purge appmenu-gtk appmenu-gtk3

---

### Post by gennoveus on 2012-03-18
> **accessgranted said:**
> I believe you have to purge the menu. Im not sure of any other way.
apt-get purge appmenu-gtk appmenu-gtk3

Thank you for your reply.

Won't this remove the appmenu and all config files? All I want to do is disable one shortcut of Gnome Term when running Vim.

Please let me know if I haven't understood your solution properly; I'm still in the process of learning this stuff.

---

### Post by gennoveus on 2012-03-22
I'm really stuck.

If I'm doing something stupid, or if I haven't provided enough information, please let me know ...

---

### Post by gennoveus on 2012-03-22
Maybe I should clarify:

Disabling all the shortcut keys is relatively easy, there are simple options for disabling and changing them.

But for some reason just that one shortcut (ctrl-shift-f) seems like it's hard coded into the program? It's the only option that I can't find a workaround for. 

Please help.

EDIT: Also, I had a look at the key bindings with gconf-editor but Ctrl-Shift-F isn't there ...

What am I doing wrong? Is my only option to stop using gnome terminal and switch to xterm or something?

---

### Post by gennoveus on 2012-03-23
5 days and nothing ... oh well. Maybe the shortcut really is hard-coded into Gnome Terminal.

For anyone who is having the same problem as me, what I did was give up on Gnome Terminal completely and changed to xterm instead.

---

