---
title: "nabi, nasty window"
date: 2011-05-23
forum: General Help
---

### Post by mkornig on 2011-05-23
Hello,

I've experienced a nasty, small, white window apparently stemming from an application called *nabi*. See attached file for a screenshot. I call it nasty because:

[LIST]
[*]It would always stay in the foreground (and hide other windows/stuff beneath).
[*]I couldn't close it. It was hard to get rid of.
[*]I didn't ask for it.
[/LIST]
This window finally disapeared after I uninstalled *nabi*.

**Questions**

[LIST=1]
[*]What is *nabi* used for? Who has made it?
[*]Why was it installed on my computer? (I didn't do it myself!) Is it a standard application?
[*]Can uninstalling cause any harm?
[/LIST]

---

### Post by hulkman on 2011-05-23
Nabi is for Korean text input authored by Choe Hwanjin.

------------------
[http://www.dotdeb.com](http://www.dotdeb.com) is a great place to get deb packages.

---

### Post by Frogs Hair on 2011-05-23
Hi and Welcome 

Nabi is not installed by default on my 11.04 installation. Remove the package via the Synaptic Package Manager or the terminal.
```
sudo apt-get remove nabi
```

---

### Post by mkornig on 2011-05-23
Thanks hulkman.

That answers question 1.

I've never been to Korea. I'm sure people speak a nice language there. Probably Korean? But I don't speak that language...

I will probably never have to write a Korean text in all my life. So I won't need *nabi* on my computer? And uninstalling was the right thing to do?

Apparently *nabi*

[LIST]
[*]was included in my French Ubuntu 11.04 distribution
[*]it has been installed on my computer
[*]and it was launched whenever I connected to my account.
[/LIST]
I believe none of this should have happened.

How do I report this error to the people who make Ubuntu?

---

### Post by Frogs Hair on 2011-05-23
You can file a bug report or ask a question about your issue at the link. I don't what programs you have installed so I am wondering if nabi was included with the installation of another program . Open the software center and check history to find out when it was installed.  [https://launchpad.net/](https://launchpad.net/)

---

### Post by mkornig on 2011-05-23
I've reported this bug. To me it seems there are several problems:

[LIST=1]
[*]Nabi opens a window that is hard to close.
[*]This window always stays in the foreground.
[*]Nabi is installed on non Korean systems by default.
[*]Nabi is lauched automatically when connecting to a user account.
[/LIST]
Thanks for all those who tried to help/clarify the situation.

---

