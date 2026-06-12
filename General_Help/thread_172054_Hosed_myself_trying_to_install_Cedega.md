---
title: "Hosed myself trying to install Cedega"
date: 2006-05-07
forum: General Help
---

### Post by TeeAhr1 on 2006-05-07
I downloaded and ran the Cedega Demo binary, but it hung up after the registration screen.  Now whenever I try to log in to Gnome, it goes through my startup programs, then immediately boots me back out to the login screen.  (I'm typing this in failsafe mode).

I tried the uninstall script in the transgaming folder, but got "could not find a suitable uninstall program.  aborting."  Then I tried removing the folder manually and restarting Gnome.  Same thing.  Then I tried reinstalling Cedega, but now when it gets to the end of the installation, the program crashes and I get this in the terminal:
```
X Error of failed request:  180
  Major opcode of failed request:  155 (RENDER)
  Minor opcode of failed request:  4 (RenderCreatePicture)
  Serial number of failed request:  281
  Current serial number in output stream:  282
```
I don't even know what I did here, let alone how to start fixing it.  I'll never mess with powers beyond my understanding again, honest!  Can anybody help me out here?

---

### Post by nanotube on 2006-05-08
well, given your description, i suspect that something is placed in your startup programs in your session that relates to cedega... try editing your session file (located in ~/.gnome2/session-manual [~ stands for your home dir]), and try deleting anything cedega related. 

oh and by the way, after you tried installation again, have you tried booting up gnome again, to see if it works this time?

---

### Post by TeeAhr1 on 2006-05-08
[QUOTE=nanotube]well, given your description, i suspect that something is placed in your startup programs in your session that relates to cedega... try editing your session file (located in ~/.gnome2/session-manual [~ stands for your home dir]), and try deleting anything cedega related.[/QUOTE]
Thx, I'll give that a shot when I get home from work today!

[QUOTE=nanotube]oh and by the way, after you tried installation again, have you tried booting up gnome again, to see if it works this time?[/QUOTE]
Yeah, no dice.  Another bit of oddity: When I boot to default session, it kicks me back out to the login immediately.  But when I go into failsafe mode, it still kicks me out, but after about ten minutes!  How weird is that?!

---

### Post by nanotube on 2006-05-08
[QUOTE=TeeAhr1] Another bit of oddity: When I boot to default session, it kicks me back out to the login immediately.  But when I go into failsafe mode, it still kicks me out, but after about ten minutes!  How weird is that?![/QUOTE]
very. :)

---

### Post by TeeAhr1 on 2006-05-08
Negative.  Here's the file:
```
[Default]
num_clients=3
0,RestartStyleHint=3
0,Priority=50
0,RestartCommand=liferea
0,Program=liferea
1,RestartStyleHint=3
1,Priority=55
1,RestartCommand=gdesklets shell
1,Program=gdesklets
2,RestartStyleHint=3
2,Priority=65
2,RestartCommand=3ddeskd --acquire=100
2,Program=3ddeskd
```

To my knowledge, I have deleted every trace of Cedega.

Is there an error log(s) I can look at here?  Thx, anyone who can help...

-p.

---

### Post by TeeAhr1 on 2006-05-09
Another clue!  It kicks me out when the screen "refreshes" (I don't know if that's the right word).  I went through my startup programs one by one, and it boots me when I run the 3ddesk daemon (when it cycles through my desktops).  Also, when the screensaver turns on.

I checked my xorg.conf file to see if it had changed during the Cedega installation, but it's the same.

So, that's a clue, I guess, but now I'm *really* confused.  I don't even know where to look for the problem.  Can anyone throw me a bone here?

---

### Post by TeeAhr1 on 2006-05-09
*bumpin' it up, cuz I got no shame :p  *

---

### Post by Monster_user on 2006-05-09
I was going to post, but I know nothing about Cadega. I'm too cheap to spring for the few bucks they charge. More importantly, I do not trust internet based transactions.

You might want to review '/var/log/dmesg', and '/var/log/Xorg.0.log' - '/var/log/Xorg.2.log'. Sometimes when you type 'dmesg' at a terminal, it does not have room for the entire list. Since this problem seems to be GLX related, review the Xorg logs may reveal more information.

**It sounds like some part of Cadega might be hanging, or crashing your GLX drivers. They may have gotten corrupted.**

You could mark the GLX driver package for complete removal in Synaptic. Then reinstall.

Come to think of it. If you installed a Cadega package, it could have "depended" on another GLX driver. If it installed it, then it could be conflicting with your original driver.

Did you have Hardware 3D before installing Cadega? (were the 3D/OpenGL screensavers slow?)

---

### Post by TeeAhr1 on 2006-05-10
Reinstalled the Nvidia blob, and that did it.  Thx, everyone!

---

