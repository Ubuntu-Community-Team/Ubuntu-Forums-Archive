---
title: "Log in with the enviroment Graphic"
date: 2011-09-24
forum: General Help
---

### Post by mbm1234 on 2011-09-24
Hello, I'm new user on Linux and I want to know if I can Log in with the enviroment Graphic as a root?, I feel very unconfortable everytime I try to setup or install a program or do something else because the Linux Ubuntu ask me for password root, please if somebody can help me, thanks in advance.

---

### Post by TeoBigusGeekus on 2011-09-24
AFAIK, the root account is disabled in ubuntu.
I'd also advise you to ask in the resolution centre to change your username, unless you wanna be spammed mercilessly.

---

### Post by Blasphemist on 2011-09-24
Please take a look at this and see if this answers your question. If not post back your specific question.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by haqking on 2011-09-24
> **mbm12341@yahoo.com said:**
> Hello, I'm new user on Linux and I want to know if I can Log in with the enviroment Graphic as a root?, I feel very unconfortable everytime I try to setup or install a program or do something else because the Linux Ubuntu ask me for password root, please if somebody can help me, thanks in advance.

Root is locked by default in Ubuntu, everything is done using **sudo** or **gksudo** (for graphical apps)

Please read [**ROOTSUDO**]("https://help.ubuntu.com/community/RootSudo")

everytime you are asked for your password it is YOUR password it requires as long as you as in the sudoers file, which you should be if you installed the system.

Cheers

---

### Post by patryk77 on 2011-09-24
> **mbm12341@yahoo.com said:**
> Hello, I'm new user on Linux [...]

Don't take this as if I was being condescending, but that is an excellent reason **NOT** to login as root.

The root account gives you all the tools you need to fubar your system, which is why it is designed to work with the sudo/gksudo model.

---

### Post by mbm1234 on 2011-09-24
Thank you all you for replying, I'm going to try.

---

### Post by mbm1234 on 2011-09-24
It's not working, I can not Log in with the enviroment Graphic, can somebody post the command how do I have to enter in the console?, thanks in advance.

---

### Post by haqking on 2011-09-24
> **mbm12341@yahoo.com said:**
> It's not working, I can not Log in with the enviroment Graphic, can somebody post the command how do I have to enter in the console?, thanks in advance.

are you saying you dont have a GUI ?

Are you on a server by any chance ? or did you install Ubuntu Server ?

So you boot and you never get a login screen just the Command line ?

If this is the case then server is not meant to have a Gui though you can add it.

Which would be:

```
sudo apt-get install ubuntu-desktop
```

However i dont recommend this.

If it is a desktop system already then as asked, do you always boot to the CLI ? or have you dropped to console ?

if so press ctrl + alt + f7 to switch back

and anything that requires admin privelege means YOUR password. or place sudo before a command to authorise and again it will ask you for YOUR password

---

### Post by Blasphemist on 2011-09-24
I'm not sure what you mean but look at this threads first 3 posts if you are not getting a graphic environment. [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Is that what you are saying? That you are not getting a graphic environment but rather a command shell?

---

### Post by mbm1234 on 2011-09-24
I'm getting a graphic environment but I want to Log in with the enviroment Graphic as a root.

---

### Post by haqking on 2011-09-24
> **mbm12341@yahoo.com said:**
> I'm getting a graphic environment but I want to Log in with the enviroment Graphic as a root.

as already said...ROOT is locked by default in Ubuntu.

admin priveleges are gained by using **sudo** or **gksudo** as mentioned already.

please read [**ROOTSUDO**]("https://help.ubuntu.com/community/RootSudo")

Log in as your usual account and whenever you need to carry out a admin task supply your password or prefix the command with **sudo** or **gksudo** and again supply YOUR password.

I presume you are an admin correct ?

---

### Post by mbm1234 on 2011-09-24
How can I setup to Log in with the enviroment Graphic as a root?, thank in advance.

---

### Post by coffeecat on 2011-09-24
> **mbm12341@yahoo.com said:**
> How can I setup to Log in with the enviroment Graphic as a root?, thank in advance.

You have been advised repeatedly that this is not advisable. You have been linked to the Rootsudo link repeatedly. You seem to be ignoring both pieces of good advice.

It is against forum policy to show people how to log into a graphical environment as root. This explains:

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

I am now going to close this thread.

---

