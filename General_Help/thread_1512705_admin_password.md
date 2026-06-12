---
title: "admin password"
date: 2010-06-18
forum: General Help
---

### Post by tnevin on 2010-06-18
I have a dell inspiron mini 10 and I have never set a administration password.  It asks for one everytime I try to update software or install software.  I have tried the esc shift esc and not get a menu to select anything all I get is MBR 2FA prompt but I can not enter anything.  Any suggestions please.

---

### Post by stoneage on 2010-06-18
It is asking for your user password - the one you set when installing.

---

### Post by tnevin on 2010-06-18
did not set one thats the problem

---

### Post by jerome1232 on 2010-06-18
You did, you had to have to install.

---

### Post by arunkrishnan on 2010-06-18
how did u installed without entering password???
u must set a password i think......

---

### Post by tnevin on 2010-06-18
I don't believe I did but lets say I did.  I have tried all my passwords and none work so how do I get around it

---

### Post by jerome1232 on 2010-06-18
If you reboot and hold shift while booting up. You should get a list of booting options, one of them says recovery mode select that. Some text should fly by and eventually land you at a menu, select drop to a root shell.


You should end up at a command prompt. type the below replace the part in blue with your real user name, then enter a new password (will ask twice).

```
passwd [COLOR="RoyalBlue"]foo[/COLOR]
```

After that, just type reboot and hit enter.

---

### Post by Chame_Wizard on 2010-06-18
Before you even install *buntu,you have to set your main password,otherwise you can't become the ROOT/SUDO to change everything.

---

### Post by tnevin on 2010-06-18
As I mentioned I don't get a list of boot options I get MBR 2FA prompt but I can not enter anything.

---

### Post by rbroom on 2010-06-18
From a little reading this looks like the system is asking which drive to boot from.  Press "2" and let us know what happens.  If that doesn't work, get back to the same prompt and press ENTER and ESC very fast one after the other.  You should then see the GRUB menu. Using the up and down arrows, highlight the second option and press ENTER to boot into recovery mode.

Let us know how it goes.

---

### Post by jerome1232 on 2010-06-18
> **tnevin said:**
> As I mentioned I don't get a list of boot options I get MBR 2FA prompt but I can not enter anything.

Did not realize you were referring to a message you get when you boot (The way you said it makes it seem like your are pressing escape when prompted for your password when attempting to update software)

I have no idea what the mbr 2fa prompt is, could be your bios (does it have a menu that's triggered by shift?) Are you using some other boot manager besides grub? I can't really help much in either case sorry.

I do have a hard time getting my grub menu though (If i press shift too early bios thinks it's a stuck key and ignore's it, if I press it to late I miss grub) So far I'm 1 for 5 boots of actually getting my grub menu lol. So it's possible you are just missing the window of time in which you have to hit shift.

---

### Post by tnevin on 2010-06-18
Nothing happened when entered 2 just started up as usual.  Did enter esc quickly just started up as usual

---

