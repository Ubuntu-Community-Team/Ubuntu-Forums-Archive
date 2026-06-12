---
title: "unable to shutdown/restart"
date: 2009-10-02
forum: General Help
---

### Post by gusanto on 2009-10-02
Hi all,
I don't remember when I start to have this problem.
Now I am unable to shutdown/restart from "switch user or shutdown" on the right top of the panel. If I click shutdown/restart, it will log out and go to the login window. If then I click shutdown/restart on the login window, it won't shutdown/restart either.
Though, if I shutdown/restart by clicking System>Shutdown, the system will shutdown/restart normally.
Any help is much appreciated.

---

### Post by Giblet5 on 2009-10-02
If you leave anyone else logged in (console, etc) or leave apps running and they take too long to exit, Ubuntu will log out instead of shutdown.

This is a common bug on 9.04. Some pointy-haired, Dilbertesque, manager-type probably signed-off on this behavior as a "feature".

I created two desktop launchers. One for restart (sudo reboot) and one for poweroff (sudo poweroff) and edited my sudo perms to remove the password requirement for those commands on my account.

Ugly, yes, but it works.

---

### Post by mojotexas on 2009-10-02
I have a similar issue.
When I shutdown, the system doesn't shut all the way down, it goes to a black screen, blinking cursor, and doesn't go any further. 
Any ideas?

---

### Post by Giblet5 on 2009-10-02
> **mojotexas said:**
> I have a similar issue.
When I shutdown, the system doesn't shut all the way down, it goes to a black screen, blinking cursor, and doesn't go any further. 
Any ideas?

This is a different problem. YOUR reboot is failing, or gdm is not restarting the X server.

Does it finish shutting down if you hit Ctrl-Alt-Del at that blinking cursor?

---

### Post by mojotexas on 2009-10-03
> **Giblet5 said:**
> This is a different problem. YOUR reboot is failing, or gdm is not restarting the X server.

Does it finish shutting down if you hit Ctrl-Alt-Del at that blinking cursor?
Giblet5,
 if you hit Ctrl-Alt-Del at that blinking cursor it will reboot. It flashes a message first: "MD stopping all devices"

---

