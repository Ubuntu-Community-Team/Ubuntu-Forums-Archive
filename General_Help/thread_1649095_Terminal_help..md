---
title: "Terminal help."
date: 2010-12-19
forum: General Help
---

### Post by Tarkko on 2010-12-19
Hey guys, I got Ubuntu a week ago and realized that I have to install some software via the terminal. The one I tried to install was a .rar archiver and there's something that keeps happening to me. 

I have to enter this into the terminal:

```
sudo apt-get install rar
```

But when I do enter that, I get a prompt for a password

```
[sudo]enter password for <user>
```

I tried using my password that I use to log into my computer with, but it says I have the wrong one.

Just a question on how I find out what the password I need is? 

Much appreciated.

---

### Post by WorMzy on 2010-12-19
You don't have to use the terminal to install any software. You can use the Software Centre or Synaptic Package Manager.

Using the terminal is the fastest method (so long as you know what package you want to install), but the other methods are perfectly fine too.

However, you will need the same password that the terminal was asking for. If the password that you use to log in isn't working, then there are two possibilities:

1) You're not entering it correctly. Passwords are case-sensitive, so check that caps-lock isn't on.

2) Your password contains characters which are causing problems, try changing it to something else. (I'm not convinced that there are "illegal" characters, but I've seen topics that seem to suggest that there are)

---

### Post by Ceiber Boy on 2010-12-19
when you install ubuntu you create an account, that password is also the sudo password. if it is not you've changed it!

it sounds like you've just installed it so i'm assuming its a clean system, so just re-install it. if you don't want to re-install it reboot into recovery mode and chasnge the sudo password from their,
[http://www.debuntu.org/recover-root-password-single-user-mode-and-grub](http://www.debuntu.org/recover-root-password-single-user-mode-and-grub)

good luck

---

### Post by WorMzy on 2010-12-19
I would advise against using the link that Ceiber boy posted, that isn't relevant to Ubuntu as the root user is not used.

---

### Post by Joeb454 on 2010-12-19
The password you need to enter is the same password you used to login :)

---

