---
title: "Can't boot to recovery mode, can't login"
date: 2010-04-13
forum: General Help
---

### Post by carn1x on 2010-04-13
Hi all,

Fairly new to this

Tried to make the /etc/pam.d/gdm mod to auto-auth keyring.

Now when I boot up it says "error initiating conversation with authentication system - general failure" preventing me from logging in.

So I read that I can enter recovery mode by pressing Esc on boot up to boot to a root shell.

However no amount of button mashing Esc on boot up seems to have any effect, always bringing me to the graphical login.

I guess I could boot to a liveUSB but this has all started when I got to work this morning, and don't have a USB key handy, and I'd like to get this sorted so I can do some work today!

Any ideas please? 

And why does the /etc/pam.d/gdm tweak seem to be causing so many issues (googling reveals the technique has a lot of other users finding the same problem as me, however they seem to be able to get to recovery mode)?

Thanks :)

EDIT: If I hold down or mash Esc fast enough, the computer will beep at me once or twice, but nothing changes on screen

EDIT 2: Ok found out that holding SHIFT is the new way of doing things, reverted pam.d/gdm to the backup and things are back to normal!

Thanks anyway!

---

### Post by Doctor Mike on 2010-04-14
> **carn1x said:**
> Hi all,

Fairly new to this

Tried to make the /etc/pam.d/gdm mod to auto-auth keyring.

Now when I boot up it says "error initiating conversation with authentication system - general failure" preventing me from logging in.

So I read that I can enter recovery mode by pressing Esc on boot up to boot to a root shell.

However no amount of button mashing Esc on boot up seems to have any effect, always bringing me to the graphical login.

I guess I could boot to a liveUSB but this has all started when I got to work this morning, and don't have a USB key handy, and I'd like to get this sorted so I can do some work today!

Any ideas please? 

And why does the /etc/pam.d/gdm tweak seem to be causing so many issues (googling reveals the technique has a lot of other users finding the same problem as me, however they seem to be able to get to recovery mode)?

Thanks :)

EDIT: If I hold down or mash Esc fast enough, the computer will beep at me once or twice, but nothing changes on screen

EDIT 2: Ok found out that holding SHIFT is the new way of doing things, reverted pam.d/gdm to the backup and things are back to normal!

Thanks anyway!Don't forget to mark as solved...:)

---

### Post by carn1x on 2010-04-14
Oh yeh, ewps :)

I'm guessing I just change the topic?

EDIT: nvm :)

---

