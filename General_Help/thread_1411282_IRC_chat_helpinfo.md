---
title: "IRC chat help/info"
date: 2010-02-19
forum: General Help
---

### Post by KegHead on 2010-02-19
Hi!

Is there a source to find out what channels are available?

a data base or site?

I only know one: #ubuntu.

Thanks!

KegHead

---

### Post by AudioDef on 2010-02-19
What chat program are you using? Many programs have a list built-in to get you started.

---

### Post by howefield on 2010-02-19
Which IRC application are you using ? 

If it's xchat, go to the Server > List of Channels menu.

Or type /list channels on the client command line.

---

### Post by KegHead on 2010-02-19
Hi!

It's empathy.

I'm new to IRC-so I'm feeling my way around.

KegHead

---

### Post by KegHead on 2010-02-19
Hi!

I just tried xchat!

It Rocks!

KegHead

---

### Post by howefield on 2010-02-19
Empathy has limited support for IRC, not sure if it is suitable for searching and obtaining channel lists.

xchat might be a better bet.

Edit: you got it already :)

---

### Post by 26venger on 2010-02-19
i use konversation. if i were you i would install it instead. 

if you want you need to get the medibuntu repository

here is how (i got the command from the medibuntu website)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

then all that you need to do is **sudo apt-get install konversation**

to get the channel list for konversation you need to go to window> channel list  and then you click the refresh list button.

i hope this helps

---

### Post by howefield on 2010-02-19
> **26venger said:**
> you need to get the medibuntu repository

No, you don't.

It is installable with the Ubuntu repositories. No "need" to get an additional repository. Also, worth pointing out that being a KDE application means that it would pull in KDE dependancies, which isn't a problem if you don't mind that, but some do.

---

### Post by 26venger on 2010-02-19
> It is installable with the Ubuntu repositories.

i wasnt able to install it with the regular repositories
 
i had to add the medibuntu

---

### Post by howefield on 2010-02-19
> **26venger said:**
> i had to add the medibuntu

You may well have added Medibuntu, that doesn't mean you had to.

[http://packages.ubuntu.com/karmic/konversation](http://packages.ubuntu.com/karmic/konversation)

Can you point me to the package on Medibuntu ?

[http://packages.medibuntu.org/karmic/index.html](http://packages.medibuntu.org/karmic/index.html)

---

### Post by 26venger on 2010-02-19
lol, i guess i typed sudo apt-get install konversation in wrong or something and then i got the medibuntu repository.

---

### Post by andrew.46 on 2010-02-19
Hi KegHead,

> **KegHead said:**
> Is there a source to find out what channels are available?

If you are interested in some *Ubuntu* channels, as well as an article on irc in Ubuntu in general, have a look here:

Internet Relay Chat
[https://help.ubuntu.com/community/InternetRelayChat](https://help.ubuntu.com/community/InternetRelayChat)

All the best,

Andrew

---

### Post by KegHead on 2010-02-20
Hi!

Thanks Andrew!

KegHead

---

### Post by aaronchall on 2010-03-05
I've had mega trouble with empathy, so I installed xchat, and it works great.  I also installed irssa, which I connected once, but a second time it didn't have the first time notes and I forgot how to connect again with irssa...

---

### Post by andrew.46 on 2010-03-05
Hi aaronchall,

> **aaronchall said:**
> I also installed irssa, which I connected once, but a second time it didn't have the first time notes and I forgot how to connect again with irssa...

Perhaps this guide will prompt your memory:

Howto] Setup irssi and join #ubuntu on Freenode
[http://ubuntuforums.org/showthread.php?t=1010780](http://ubuntuforums.org/showthread.php?t=1010780)

All the best,

Andrew

---

### Post by aaronchall on 2010-03-06
> **andrew.46 said:**
> hi aaronchall,



perhaps this guide will prompt your memory:

Howto] setup irssi and join #ubuntu on freenode
[http://ubuntuforums.org/showthread.php?t=1010780](http://ubuntuforums.org/showthread.php?t=1010780)

all the best,

andrew

ty, tyvm!!!!!

A

---

