---
title: "Empathy IRC"
date: 2009-11-03
forum: General Help
---

### Post by HDave on 2009-11-03
Does anyone know how to add an IRC account to Empathy?  

Please tell me I am just stupid and that Ubuntu didn't actually switch from Pidgin to a new IM program that doesn't support IRC...:confused:

---

### Post by mac9416 on 2009-11-03
I assume you are running Jaunty, not Karmic? I believe Karmic comes with IRC support for Empathy built-in. If you're in Jaunty, I believe this command will get IRC support for you...

```
$ sudo apt-get install telepathy-idle
```

Hope that gets it!

---

### Post by HDave on 2009-11-03
Thanks for the help.  I am using Karmic and that package is already installed.  However, no joy.  Seems to be no way to get to freenode IRC rooms.

---

### Post by egyn on 2009-11-07
> **HDave said:**
> Thanks for the help.  I am using Karmic and that package is already installed.  However, no joy.  Seems to be no way to get to freenode IRC rooms.

It has been reported in Launchpad that commonly used commands such as "/msg" are not functional in Karmaic so someone might hopefully work on adding support shortly.

---

### Post by Kitsune on 2009-11-20
I'm connecting to freenode just fine with Empathy
Edit/Accounts/Add
Select irc in the drop down box, and select irc.freenode.net as server.

---

### Post by QwUo173Hy on 2009-11-30
This doesn't work for me either. Could someone explain more clearly what I'm supposed to do in the dialog? (attached)

---

### Post by QwUo173Hy on 2009-11-30
No, I have a new dialog. I have no idea why - but it's working.

---

### Post by MaikoID on 2010-07-14
I'm using Ubuntu 10.04 and have no idea how to use the freenode server.

Bye

---

### Post by philinux on 2010-07-14
> **HDave said:**
> Does anyone know how to add an IRC account to Empathy?  

Please tell me I am just stupid and that Ubuntu didn't actually switch from Pidgin to a new IM program that doesn't support IRC...:confused:

I tried and re tried with irc and empathy. Finally got it sorted. I installed xchat.

---

### Post by MaikoID on 2010-07-14
> **philinux said:**
> I tried and re tried with irc and empathy. Finally got it sorted. I installed xchat.

me too =)

---

### Post by Haylz on 2010-07-14
KVIrc and Konversation are good IRC clients for Linux. 

To join a channel go to "Room" then "join", change the account to the one you created, and then type in the channel name... Then click "join"

If that doesn't work, try connecting to "chat.freenode.net" instead.

---

### Post by ParadoxBlue on 2010-08-11
> **MaikoID said:**
> me too =)

Wow...first time I've ever goofed around with Empathy. Tried to connect to IRC and all I can say is I believe Empathy is one large p.o.s. Got to add it to my un-install list.

---

### Post by jrandall1968 on 2010-09-09
I was originally having a problem finding IRC in Empathy.
 
But after I added my AIM account on the initial account create, IRC became an available option when I went to add addtional accounts.

---

### Post by rogerano on 2010-09-16
Wow. Same here. I added a completely bogus AIM account and the option to add IRC appeared in the dropdown list after that. Ubuntu 10.04 64-bit.

How can the absence of an IRC option go unnoticed during testing?

---

### Post by liruqi on 2011-05-16
> **MaikoID said:**
> me too =)
is tricky, you need to add '#' before room name. for example: "#mongodb", 
"mongodb" does not work

---

