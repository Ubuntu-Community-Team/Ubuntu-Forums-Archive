---
title: "Firefox keeps loading a while when opening new instance"
date: 2006-02-12
forum: General Help
---

### Post by palomar on 2006-02-12
Maybe a weird description in the topic tile, but to be more specific: when I have already started one or more instances of Firefox and I want to start another instance of firefox using the KDE launcher, every time the firefox windows appears immediately, but there is another ' item' of firefox in the taskbar which says 'loading'  and at my mouse pointer there is a firefox-icon jumping up and down. This takes on for about 30 seconds and then those 'loading' thing in the taskbar and mouse pointer will disappear.

When I start firefox using the console 'just type firefox' it starts OK. It only happens when I start FF using the KDE launcher. I have already checked the shortcut. By default the command is 'firefox %u', but changing it to 'firefox' won't solve it. 

So to be in short: starting firefox for the first instance via KDE launcher goes well. When I open another instance, when the first is still open, using KDE launcher I get the loading things. Starting firefox in the console always goes fine.

I have already updated firefox from default to 1.5.0.1

Anyone knows what to do?

---

### Post by dresnu on 2006-02-12
I don't know how to solve it, I just wanted to say that you 're not the only one 'cause this happens to me too.

---

### Post by Adrian_b on 2006-02-12
[QUOTE=dresnu]I don't know how to solve it, I just wanted to say that you 're not the only one 'cause this happens to me too.[/QUOTE]
I have it too, but it only just started.
Before i didn't have this problem.

---

### Post by ajgreeny on 2006-02-12
This is just the launch feedback which you can turn off if you want to, it's not another FF opened on the taskbar.

Go to the kde control centre, if it's not in your menus open a terminal and type "kcontrol" without the quotes.

In appearance and themes you will see the sub-menu for launch feedback where you can change whatever you wish.  Simple eh?

---

### Post by gingermark on 2006-02-12
[QUOTE=ajgreeny]This is just the launch feedback which you can turn off if you want to, it's not another FF opened on the taskbar.

Go to the kde control centre, if it's not in your menus open a terminal and type "kcontrol" without the quotes.

In appearance and themes you will see the sub-menu for launch feedback where you can change whatever you wish.  Simple eh?[/QUOTE]

I think the OP wants to open multiple instances of Firefox, rather than turn off the feedback.

---

### Post by palomar on 2006-02-12
Thanx! Disabling 'Launch Feedback' did make the trick :) At the shortcut properties -> application -> advanced properties I unchecked it and now now new instances start immediately :)

---

### Post by lowey23 on 2006-02-12
Thanks, all, worked for me too.

---

