---
title: "Help to kill console killer, please.."
date: 2010-04-30
forum: General Help
---

### Post by ilna on 2010-04-30
I have removed desktop manager from /etc/init, and GRUB is configured to use console. After upgrading from Karmic to Lucid I have noticed just before login invitation all previuos console output is cleaning. As a result I can not see boot process messages with Shift-PgUp/PgDown.

How to prevent console output cleaning?

---

### Post by RedSquirrel on 2010-04-30
Have a look at the Release Notes for Lucid: [changes in boot-time output]("http://www.ubuntu.com/getubuntu/releasenotes/1004#Changes%20in%20boot-time%20output%20on%20Ubuntu%20Server")

The release notes claim the messages end up on tty7 (and in /var/log/boot.log).

I recently replaced Lucid with something else so I cannot verify that claim. 

When I had Lucid installed, I considered trying to change that behaviour (to have the boot sequence displayed above the login prompt), but for various reasons I decided to simply *move along*. ;)

---

### Post by ilna on 2010-04-30
I use Desktop (Kubuntu) edition rather Server one. And - yes, /var/log/boot.log contains **part** of boot messages - that part which takes place **after** switching console from plain text to graphic mode - this is another problem I'd want to resolve - to prevent the switching.

At any case - thanks, knowing about boot.log is useful.

---

