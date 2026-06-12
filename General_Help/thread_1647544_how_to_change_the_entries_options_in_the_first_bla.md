---
title: "how to change the entries options in the first black screen (dualboot)"
date: 2010-12-17
forum: General Help
---

### Post by doron387 on 2010-12-17
hi guys

i have ubuntu 10.10 installed using wubi inside win7.
when i power on the pc, i get a black screen with three os options :
windows 7, ubuntu, ubuntu.

there are 2 ubuntu options probably due to uninstalling of wubi and reinstalling of it.

both ubuntu entries lead to the same os, but i wish to get rid of one of them (for aesthetic reasons), i also wish to change the time out of this screen.

btw, how is this screen called ? (as i think this is not the grub menu screen. am i right ?)

thnx
doron387

---

### Post by Linyx on 2010-12-17
[SIZE="2"][/SIZE]> **doron387 said:**
> hi guys

i have ubuntu 10.10 installed using wubi inside win7.
when i power on the pc, i get a black screen with three os options :
windows 7, ubuntu, ubuntu.

there are 2 ubuntu options probably due to uninstalling of wubi and reinstalling of it.

both ubuntu entries lead to the same os, but i wish to get rid of one of them (for aesthetic reasons), i also wish to change the time out of this screen.

btw, how is this screen called ? (as i think this is not the grub menu screen. am i right ?)

thnx
doron387
I think "sudo update-grub" can remove your blank-entry....

and the screen which you are talking about, this is Grub-menu screen(i think so)
[SIZE="2"]Edit:-I don't know about that ,that this will work in Wubi...i think you had to remove that entry for Drive C: ,may some1 will post about that...[/SIZE]

---

### Post by bcbc on 2010-12-17
You need to use bcdedit (command line tool - look on Microsoft websites for usage instructions) to edit the boot entries (or you can download a tool called easybcd).
To change the timeout, you can do it from System Properties, Advanced Tab, Startup & Recovery... or of course bcdedit and easybcd. Don't set the timeout to zero.

I believe it's referred to as the Windows Boot Manager.

PS for wubi installs, never update packages grub-pc or grub-common or you will have problems.

---

### Post by doron387 on 2010-12-19
thanx bcbc,
easybcd works great
[solved]

---

