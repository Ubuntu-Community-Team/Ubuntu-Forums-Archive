---
title: "double input into terminal"
date: 2010-10-05
forum: General Help
---

### Post by Kodpoet on 2010-10-05
Hi,

I run an irssi screen on a server and would like to use a single command from my terminal to access the irc.

At present I have put:

```
screen -dr
```

in my bashrc at the server so that is run every time I log in and defined an alias "irc" in the bashrc on my local computer such as:

```
ssh foo@bar.com -p 1337
```

which means the only thing I have to do now is enter my password.

What I'd like to know is how I can first give the "irc" command and then wait, or check if the server has connected, and lastly enter my password automatically.

Any ideas? ^^

---

