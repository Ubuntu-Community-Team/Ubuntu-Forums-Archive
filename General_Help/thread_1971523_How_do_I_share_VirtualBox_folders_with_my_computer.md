---
title: "How do I share VirtualBox folders with my computer?"
date: 2012-05-02
forum: General Help
---

### Post by CProgramming on 2012-05-02
hello everyone,

I'm running Ubuntu 11.10 (with gnome3) on my computer and I running on virtualBox windows XP.

Reason:

I learning at school Assembly and I'm using MOST IDE. I don't know about Linux's Assembly's Debbugers and compilers. I'll be glad for recommends.

--------------------------------------

When I creating files (for example, ASM source files) and I want to move them to my real desktop, I cant.

How can I make a shared folders that be used and accessible for Ubuntu and vBox both?

Thanks a lot!

---

### Post by CProgramming on 2012-05-08
Up

---

### Post by Sergius14 on 2012-05-08
Easily from the vbox interface...

You can choose which folders do you want to share from the host (Ubuntu) to the Guest (Windows).

THEN

On the guest os (WinXP) you have to create a new network drive from My Computer (Map a Network Drive) and then, if everything is ok, the Guest OS should find the shared folders.

---

### Post by motorcity909 on 2012-05-08
As Sergius14 said, you can share the Ubuntu folders via the Vbox settings for that virtual machine - see attached screengrab 1.

Meanwhile in the virtual Windows, just right-click the folder you want to share and go to 'sharing and security' - see screengrab2.  Once a folder is shared Ubuntu should show it in Nautilus>Network.

Alternatively, you could use a cloud service like Ubuntu One or Dropbox - install on both Ubuntu and Virtual Windows and simply drop files into that folder to sync between them both.

Good luck!

---

### Post by CProgramming on 2012-05-08
> **Sergius14 said:**
> Easily from the vbox interface...

You can choose which folders do you want to share from the host (Ubuntu) to the Guest (Windows).

THEN

On the guest os (WinXP) you have to create a new network drive from My Computer (Map a Network Drive) and then, if everything is ok, the Guest OS should find the shared folders.

> **motorcity909 said:**
> As Sergius14 said, you can share the Ubuntu folders via the Vbox settings for that virtual machine - see attached screengrab 1.

Meanwhile in the virtual Windows, just right-click the folder you want to share and go to 'sharing and security' - see screengrab2.  Once a folder is shared Ubuntu should show it in Nautilus>Network.

Alternatively, you could use a cloud service like Ubuntu One or Dropbox - install on both Ubuntu and Virtual Windows and simply drop files into that folder to sync between them both.

Good luck!

Thanks to both of you!!

But I have problem to create a Home network in windows XP :(

I didn't use Windows since I had 9 years old (now I 15 :P)

Could you help me create a home network?.. thanks!

---

### Post by Sergius14 on 2012-05-09
Have you already tried to Map a Network Drive from My Computer?

---

### Post by CProgramming on 2012-05-10
> **Sergius14 said:**
> Have you already tried to Map a Network Drive from My Computer?

Do you mean "My computer" of WinXP?

I tried do something like this, but I'm not sure I know to do that .. can you help me do it? thank you a lot!!

---

### Post by Sergius14 on 2012-05-10
Something like attached screeshot (it is a Win7, but on XP it is quite the same).

The browse button should display your previously configured shared folders from vbox.

---

### Post by |{urse on 2012-05-10
You mentioned needing an assembler ide for linux.

[http://webster.cs.ucr.edu/AsmTools/HLA/dnld.html](http://webster.cs.ucr.edu/AsmTools/HLA/dnld.html) <-- pretty nice.

Uses fasm. You can use GAS or whatever you'd like though.

[http://www.masm32.com/board/index.php?PHPSESSID=91437b306c961e724e6ec44d527bc6db&topic=7955.0](http://www.masm32.com/board/index.php?PHPSESSID=91437b306c961e724e6ec44d527bc6db&topic=7955.0)

More info on assembly language for linux

[http://homepage.mac.com/randyhyde/webster.cs.ucr.edu/LinuxAsm/index.html](http://homepage.mac.com/randyhyde/webster.cs.ucr.edu/LinuxAsm/index.html)

---

