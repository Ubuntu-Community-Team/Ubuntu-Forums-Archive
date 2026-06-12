---
title: "Remove password"
date: 2009-09-02
forum: General Help
---

### Post by orangeLemon on 2009-09-02
For some reason Ubuntu forces you to choice a password when you're installing, something that I have no need for. I use a desktop in a very secure environment where I always back up the small amount of my important files to a USB drive. If by some off chance someone decides to get on my computer and mess it up the only thing I lose is about an hour having to set my system back up, the majority of that time I don't even have to be anyway near the computer. I'm not really worried about someone stealing my computer either, since it is a desktop, but if they do I really doubt a password is going to hinder them much. Is there any way that I can disable Ubuntu from prompting me to insert a password when I want to install software, change my settings, update my computer, etc? Did I miss something and there is a way to install without a password?

---

### Post by P4man on 2009-09-02
Just keep in mind that having to enter a passwords also protects you from the biggest threat of all: yourself :) if nothing else, it reminds you you are doing something potentially dangerous.

To answer the actual question: you probably can by running the system as root, but its not allowed to discuss on this forum how to do that. Dont have the link at hand, but im sure someone will supply it.

---

### Post by cariboo on 2009-09-02
The short answer is no. The reason you need a password is to be able to install programs. You can not install anything outside your home directory unless you do it as root. IF you don't want to enter a password on boot, you can enable automatic login by going to System-->Administration-->Login Window, you will have to enter your password, then click the Security tab, click the Enable Automatic Login check box, select your user, then click close.

The reason you need to enter a password is that you don't have permissino to change any files outside your home directory.

Remeber, Ubuntu is not Windows, most of what you know about Windows is of no use when running Ubuntu.

---

### Post by i.r.id10t on 2009-09-02
You can set GDM to automatically log you in, and then you can use visudo to change the sudoers file so that you don't need to enter your password for working with sudo.

---

### Post by orangeLemon on 2009-09-02
To P4Man - I've used Linux long enough to know how to not mess it up. Given the off chance that I'm doing something "dangerous" the password will only serve as an annoyance, not a reminder. If it's a reminder a simple "Allow, Don't Allow" box a la Windows XP would suffice. Once upon a time I got root to log in by default but it was extremely annoying to do, and didn't work right for some reason. Ubuntu has also taken steps against this. Also: Why can't you discuss how to log in as root?

To cariboo907 - I know Ubuntu is not Windows, which is why I use it. This is one of the few things that I fell Windows does a whole lot better. I have gotten my account to log in by default, that's not the problem. The problem is being prompted every time I want to do something to my system.

To i.r.id10t - As I said to caribooo I've already gotten my account to automatically log in. Would changing visudo mean that I wouldn't have to enter a password when doing something, or would it simply mean that I wouldn't have to enter a password in the terminal when doing "sudo ..."?

---

### Post by P4man on 2009-09-02
> **orangeLemon said:**
> To P4Man - I've used Linux long enough to know how to not mess it up. Given the off chance that I'm doing something "dangerous" the password will only serve as an annoyance, not a reminder. If it's a reminder a simple "Allow, Don't Allow" box a la Windows XP would suffice. Once upon a time I got root to log in by default but it was extremely annoying to do, and didn't work right for some reason. Ubuntu has also taken steps against this. Also: Why can't you discuss how to log in as root?

here is why:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by orangeLemon on 2009-09-02
> **P4man said:**
> here is why:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
I suppose that makes sense. In that case I'll just look elsewhere in order to log in as root, since that seems to be the only solution. Might just decide to leave it how it is if it is going to be that complicated though. Thanks for pointing me in the right direction anyway. :D

---

### Post by fluffman86 on 2009-09-02
How to use Root:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

standard disclaimers apply: this is dangerous, use sudo for a reason, yadda yadda yadda.

The information you want is uder "Remove Password Prompt For sudo" near the bottom.

---

### Post by bodhi.zazen on 2009-09-02
What you are asking to do is simply not supported here.

You may use the auto login feature if you wish in GDM.

Disabling passwords is a big security hole and there is a reason every modern OS requires a login. If you are connected to the internet you are not the only person with access to the computer. Passwords are the first line of defense and disabling them is simply not a good idea.

---

