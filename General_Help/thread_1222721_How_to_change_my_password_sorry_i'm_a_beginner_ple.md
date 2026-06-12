---
title: "How to change my password? sorry i'm a beginner please help me"
date: 2009-07-25
forum: General Help
---

### Post by kart168 on 2009-07-25
hi

i have just installed ubuntu 9.04 version using the wubi installer. During installation i gave one password. Now if i wish to change my password what should i do? please do help me. Being a beginner i need assistance regarding this issue.

thank you,

---

### Post by SuperSonic4 on 2009-07-25
Open a terminal (System -> Accessories -> Terminal or wherever gnome keeps it's terminal) and type in

```
passwd <user>
``` ------------

 so for me it would be ```
passwd sonic
``` and I'd get prompted for my current password and then my new one and finally to retype the new one. Bear in mind it won't show you typing but it is recognising it.

-------

Of course as a user you can only change your own password. If you wanted to change someone else's password then you'd have to type in ```
sudo passwd <user>
``` to become root in order to change another's password.

---

### Post by sisco311 on 2009-07-25
Go to *System -> Preferences -> About Me* and click the *Change Password...* button.

---

### Post by howlingmadhowie on 2009-07-25
> **kart168 said:**
> hi

i have just installed ubuntu 9.04 version using the wubi installer. During installation i gave one password. Now if i wish to change my password what should i do? please do help me. Being a beginner i need assistance regarding this issue.

thank you,

there's a graphical way of doing this too:

click on system at the top left then go to the second menu point (whatever it's called in your language, in german it's "systemverwaltung" (system management)) and find an entry called "Users and groups" (or something that translates as that). then you can change your password in the window that opens.

this really shows the power of the terminal, though. using the terminal to do something like this is quicker and easier to explain :)

---

### Post by kart168 on 2009-07-25
thank you ppl for the help. now i got the new password
thank you:D

---

