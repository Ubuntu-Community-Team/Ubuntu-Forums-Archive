---
title: "password trouble"
date: 2012-03-08
forum: General Help
---

### Post by johntd on 2012-03-08
why will my pass word only work sometime, it work okay for things like adding software but not in the terminal

---

### Post by Sergius14 on 2012-03-08
You should provide more info or details, an some concrete examples.... but is very likely that is a typo mistake by different keyboard distribution (specially if you use special characters).

Over Terminal, remember that it is not the same to paste with right click than copy/paste with ctrl shift c/v.

---

### Post by lisati on 2012-03-08
When typing your password at the terminal, it is common for it to appear that nothing is happening when you type and that your password is not being accepted. This is normal and can be thought of as a security precaution to help prevent someone reading your password over your shoulder. Remember to type your password as normal, and it should be accpeted.

---

### Post by acimi66 on 2012-03-08
moved...

---

### Post by johntd on 2012-03-09
all I get is command not found

---

### Post by lisati on 2012-03-09
> **johntd said:**
> all I get is command not found

Please post the command you are trying.

---

### Post by johntd on 2012-03-09
it is the same no matter what command I use

---

### Post by yetiman64 on 2012-03-09
> **johntd said:**
> all I get is command not found**That means the password was accepted** but that you've put in the command wrongly.

Drag a selection over the terminal output, right click and select copy, post your ouput into the message editor here. Please put the terminal output here between [noparse]```
 and 
```[/noparse] tags for clarity. The simplest way of doing this is to highlight the output and then click on the [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] button in the message toolbar.

This way we can actually see what is going wrong and not have to guess, thus hopefully we may then be able to help you. :)

---

### Post by johntd on 2012-03-09
john@john-desktop:~$ iptables --list
iptables v1.4.10: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
john@john-desktop:~$ 
Hope this is what you mean

---

### Post by nothingspecial on 2012-03-09
> **johntd said:**
> Permission denied (you must be root)


You need to do it with sudo

```
sudo iptables --list
```

---

### Post by johntd on 2012-03-09
Yes I see that now from your other message, the trouble was I was using commands as they where given to me, like taking things as read not realizing  that there was something to go in front, many thanks for your time and bearing with me, after windows this takes a bit of leaning.

---

