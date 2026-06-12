---
title: "Can you change text based login message?"
date: 2010-05-16
forum: General Help
---

### Post by Alexander D. Gray on 2010-05-16
Hi all,

I'm currently running ubuntu 10.04 and having it boot to a text (non-graphical) login screen.

When it boots up it displays a line of text something along the lines of:

ubuntu 10.04 *name of computer *tty1

and then displays *name of computer *login: with the blinking cursor 

I was wondering if it's possible to change that first line of text, in particular I'd rather it not say which operating system is being used. Is it possible to edit what this line says?

In summary, my question is for ubuntu 10.04, on a text based login, how can you edit the line of text that appears *prior* to the login prompt?

Thanks for all your help.

Cheers.

---

### Post by dcstar on 2010-05-16
> **Alexander D. Gray said:**
> Hi all,

I'm currently running ubuntu 10.04 and having it boot to a text (non-graphical) login screen.

When it boots up it displays a line of text something along the lines of:

ubuntu 10.04 *name of computer *tty1

and then displays *name of computer *login: with the blinking cursor 

I was wondering if it's possible to change that first line of text, in particular I'd rather it not say which operating system is being used. Is it possible to edit what this line says?

In summary, my question is for ubuntu 10.04, on a text based login, how can you edit the line of text that appears *prior* to the login prompt?

Thanks for all your help.

Cheers.

Possibly in /etc/update-motd.d/00-header or /etc/issue

---

### Post by Alexander D. Gray on 2010-05-16
> **dcstar said:**
> Possibly in /etc/update-motd.d/00-header or /etc/issue

Thanks for the quick reply!

The motd file actually refers to the statement that comes up *after *you login. The /etc/issue file is exactly what I was looking for though and editing it solved what I wanted to do. Thanks!

I just had one quick question.....

The line prior to login originally states "Ubuntu 10.04 LTS *name of computer *tty1"

The single line in the file /etc/issue is "Ubuntu 10.04 LTS \n \l"

I first changed the line to "Test \n \l" which resulted in the login line saying "Test *name of computer *tty1"

in a stroke of daring, I removed the entire line of /etc/issue and changed it to say "Test"

This resulted in the login line saying "Test" which is exactly what I wanted!

My question is, in the original /etc/issue file, what do the terms \n and \l refer to? I would fathom a guess that \n would display the name of the computer, and on that logic \l would state "tty1". But what does tty1 refer to? 

I replaced the line so now it says exactly what I want it to, but I was wary of removing those \n and \l terms without fully knowing what they did. Could anyone explain?

Thanks for all the help,

Cheers.

---

### Post by VCoolio on 2010-05-16
[Here you go.]("http://www.linuxfromscratch.org/blfs/view/svn/postlfs/logon.html") Also 'man agetty'. For the lazy people: 
```
b   Insert the baudrate of the current line.
d   Insert the current date.
s   Insert the system name, the name of the operating system.
l   Insert the name of the current tty line.
m   Insert the architecture identifier of the machine, e.g., i686.
n   Insert the nodename of the machine, also known as the hostname.
o   Insert the domainname of the machine.
r   Insert the release number of the kernel, e.g., 2.6.11.12.
t   Insert the current time.
u   Insert the number of current users logged in.
U   Insert the string "1 user" or "<n> users" where <n> is the
    number of current users logged in.
v   Insert the version of the OS, e.g., the build-date etc.

```

Edit: to answer your question: it is not dangerous to remove or replace \n or \l, your pc won't die from it and your family is safe. Just leave the fancy first line with the [[/?? stuff alone.

---

### Post by Alexander D. Gray on 2010-05-16
Perfect!

Thanks for all your help, now for one final curiosity....

So I've figured out how to change the message prior to the login prompt with /etc/issue and figured out how to change the message after the login prompt with /etc/update/motd.d/10-help-text. Now as you may well guess, I'm curious to whether or not it's possible to change the text of the login prompt *itself.*

When my computer boots, it currently shows

[I]Line of text

Name of computer [/I]Login: _     (blinking cursor)

I'm wondering if I can change where it says the computer name and login to something like

[I]Line of text

Line of text[/I]:  _      (blinking cursor)

where I can still type in a username and login and so forth. Is this possible?

Cheers!

---

### Post by maddyuk on 2010-05-18
It is possible. Needs editing your .bashrc and change the PS1 value to

PS1="*Line of text*:"

For more help on customising the prompt, look at [http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html)

---

### Post by Alexander D. Gray on 2010-05-19
> **maddyuk said:**
> It is possible. Needs editing your .bashrc and change the PS1 value to

PS1="*Line of text*:"

For more help on customising the prompt, look at [http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html)



I took a look at this, but it appears to only change the prompt in a terminal after you've logged in, which isn't the particular line I'm looking to change. Still very cool though, and a useful thing to know how to do. Thanks for your help.

To try and clarify, let's suppose my computer's name/hostname is Alex. When I first boot up, I see a message displayed, and then the line:

Alex Login:         - this is where I would type my username and hit enter, be prompted for the password, and so forth.

I want to change this "Alex Login" line to say something else, is that possible?

Thanks for your help otherwise.

---

### Post by maddyuk on 2010-05-19
Not very sure about this but the pre-login prompt could be hardcoded in ***getty***. try ***mingetty***

---

### Post by Alexander D. Gray on 2010-05-19
> **maddyuk said:**
> Not very sure about this but the pre-login prompt could be hardcoded in ***getty***. try ***mingetty***


Hello,

My research has directed me toward looking into getty but I'm not very familiar with it. I've read that the login prompt may be hard coded into getty (which I imagine means it can't be changed?) and that mingetty may be a workaround. But I've also read that mingetty is most suitable for virtual environments, which I don't think I'm running. 

Any thoughts on how using getty/mingetty could make this work?

Thanks in advance.

---

