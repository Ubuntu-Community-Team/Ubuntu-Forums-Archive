---
title: "[F11] Installing NVIDIA"
date: 2009-08-14
forum: General Help
---

### Post by Couto on 2009-08-14
Hey, I just switched from Ubuntu to Fedora, but I'm so used to .deb files now I'm stuck on installing the NVIDIA package I downloaded.

Could you guys give me the commands to run the install?

The package is on my desktop and it's named "NVIDIA-Linux-x86_64-190.18-pkg2.run"

Thank you for the help.

---

### Post by soapBAR2 on 2009-08-14
*ahem* Isn't this better suited for the fedora forums?

Anyway, it's a bash script. Just open your terminal, and type out the program as if it were a program. You'll probably need sudo.

---

### Post by starcraft.man on 2009-08-14
I don't mind, all one big family. Lucky I got a guide already prepared, not mine authored though I did modify it a bit.

[http://pastebin.ca/1530070](http://pastebin.ca/1530070)

Please print it out, it's well explained. I removed a few steps unnecessary. If you never installed any other nVidia drivers, ignore 7b. If you've any questions, ask me before you drop to a console.

Edit: soapBAR2, a lil more involved than that. Your correct it's a script though that needs executing. Oh and nice to see another Canadian Couto, see ya around.

---

### Post by Couto on 2009-08-14
Yes, Fedora Forums are no help, and whenever I need help and I come here, I get it. I'll stick to here..

Edit: Oh and thanks for the guide, I'll try it out.

Edit2: [sudo] password for Chris: 
Chris is not in the sudoers file.  This incident will be reported.

On step 3, lol.

---

### Post by starcraft.man on 2009-08-14
Uh.... darn. [This]("http://www.psychocats.net/ubuntu/fixsudo") is how to do it on Ubuntu, I'm not a fedora user though, I assume it's about same. Good luck. If not, post back and I'll try and give more specific advice or find a fedora user.

I assume fedora is actually using Sudo, do you want to try su instead just to be sure?

---

### Post by Couto on 2009-08-14
> **starcraft.man said:**
> Uh.... darn. [This]("http://www.psychocats.net/ubuntu/fixsudo") is how to do it on Ubuntu, I'm not a fedora user though, I assume it's about same. Good luck. If not, post back and I'll try and give more specific advice or find a fedora user.

I assume fedora is actually using Sudo, do you want to try su instead just to be sure?

Okay thanks for your help anyways.

---

### Post by Couto on 2009-08-14
Does anybody else know? :(

---

### Post by starcraft.man on 2009-08-14
> **Couto said:**
> Does anybody else know? :(

I think this is it friend. [http://fedorasolved.org/post-install-solutions/sudo](http://fedorasolved.org/post-install-solutions/sudo)

Tell me if works on fedora.

---

### Post by Couto on 2009-08-14
```
## Allow root to run any commands anywhere
root    ALL=(ALL)       ALL
chris    ALL=(ALL) ALL
## Allows members of the 'sys' group to run networking, software,
## service management apps and more.
# %sys ALL = NETWORKING, SOFTWARE, SERVICES, STORAGE, DELEGATING, PROCESSES, LOCATE, DRIVERS

## Allows people in group wheel to run all commands
# %wheel        ALL=(ALL)       ALL

## Same thing without a password
%wheel  ALL=(ALL)       NOPASSWD: ALL
```


Did I do this right? Lol. :(

---

### Post by starcraft.man on 2009-08-14
Good news, got a Fedora mate of mine ya can talk to on IRC (i'm there too :) ). Please go to Applications and open Xchat. Set it to connect to Freenode (see [here]("https://help.ubuntu.com/community/XChatHowto") if not there). In favourite channel (or separately once connected) join **#ubuntu-beginners-help** to join our channel. We'll be there, use same username as ya have on forums.

---

### Post by Couto on 2009-08-14
> **starcraft.man said:**
> Good news, got a Fedora mate of mine ya can talk to on IRC (i'm there too :) ). Please go to Applications and open Xchat. Set it to connect to Freenode (see [here]("https://help.ubuntu.com/community/XChatHowto") if not there). In favourite channel (or separately once connected) join **#ubuntu-beginners-help** to join our channel. We'll be there, use same username as ya have on forums.

I'm installing now (Xchat)

---

