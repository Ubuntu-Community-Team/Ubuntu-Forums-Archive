---
title: "how to connect IRC client?"
date: 2009-07-13
forum: General Help
---

### Post by mytechguru on 2009-07-13
Hi . @ pidgin client i tried to connect irc but it didnt...

i want to connect [*irc.freenode.net/slicehost*]("irc://irc.freenode.net/slicehost")

@ seting i configured for irc n server name n user name

[COLOR=#cc0000][SIZE=2](11:32:08  IST) [/SIZE][/COLOR][COLOR=#CC0000]**[SIZE=3]freenode-connect: [/SIZE]**[/COLOR][SIZE=3]Received CTCP 'VERSION' (to slicehost1) from freenode-connect[/SIZE]

---

### Post by hibliss on 2009-07-13
I use Xchat, available in the repo.

The command would be:

```
/server irc.freenode.net
```

Then:

```
/join #slicehost
```

You can set a nick in the channel with the command:

```
/nick (name you want here)
```

---

### Post by bab1 on 2009-07-13
For Pidgin you do the following:
Buddy List >> Buddies >> Add Chat >> select the IRC account and use Channel for: #slice host >.> then click the add button.

---

### Post by mytechguru on 2009-07-13
sorry we dont get channel option, only user name n server n alias ....then where is the channel option as you mentioned

---

### Post by bab1 on 2009-07-13
> **mytechguru said:**
> sorry we dont get channel option, only user name n server n alias ....then where is the channel option as you mentioned

I'm gunna guess here that you are creating the account.  Is that correct?  After you create the account and it is up and running, go back to the "Buddy List" and follow my instructions.

It is confusing.  This is a 2 step process.  First you create the **account** on the server at irc.ubuntu.com.  Then you create the **chat** on the Buddy List

---

