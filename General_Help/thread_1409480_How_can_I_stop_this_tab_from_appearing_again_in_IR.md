---
title: "How can I stop this tab from appearing again in IRC via Pidgin?"
date: 2010-02-17
forum: General Help
---

### Post by Rytron on 2010-02-17
Hi.
I use Pidgin as my IRC client. I set it to remember my passwords for the #linuxjournal and #ubuntu channels.
As you can see in the picture, there is a tab titled Frigg. I don't know if Frigg is a user or bot or channel! How do I prevent it from appearing every time I start Pidgin? I closed it before but then it keeps coming back when I restart Pidgin!
Thank you.

---

### Post by howefield on 2010-02-18
> **Rytron said:**
> I don't know if Frigg is a user or bot or channel!

Do a /whois on it ?

> [frigg28] 30(~frigg@freenode/utility-bot/frigg30): freenode utility bot, replaces freenode-connect
[frigg28] niven.freenode.net :Corvallis, OR, USA
[frigg28] is logged in as27 frigg
[frigg28] End of WHOIS list.

---

### Post by Rytron on 2010-02-18
```
/whois frigg
```

Result

```
Nick: frigg
Username: ~frigg@freenode/utility-bot/frigg
Real name: freenode utility bot, replaces freenode-connect
Server: niven.freenode.net (Corvallis, OR, USA)
```

---

### Post by howefield on 2010-02-18
So it's a server/channel bot, you can try putting it on ignore, but this might give you issues connecting.  

Easily enough reversed if this is the case though.

---

### Post by Rytron on 2010-02-18
Hi howefield. Do you mean 'block'?

---

### Post by howefield on 2010-02-18
> **Rytron said:**
> Hi howefield. Do you mean 'block'?

No, I mean ignore, an IRC command.

[http://www.ircbeginner.com/ircinfo/ircc-commands.html](http://www.ircbeginner.com/ircinfo/ircc-commands.html)

I don't use Pidgin, well not now anyway, and never used it for IRC.

---

### Post by Rytron on 2010-02-18
No luck with ignore command.

I decided to block frigg and now all seems fine.

---

### Post by Rytron on 2010-02-21
If I ever needed to unblock frigg; how would I do so?

---

### Post by howefield on 2010-02-22
Seems a long time since I used Pidgin and never for IRC, have you tried the "Privacy" option under the "Tools" menu in the Buddy List.

---

### Post by Rytron on 2010-02-22
> **howefield said:**
> Seems a long time since I used Pidgin and never for IRC, have you tried the "Privacy" option under the "Tools" menu in the Buddy List.

Thank you howefield. I went to the Privacy option before and overlooked that I forgot to change 'Set Privacy for' user to my IRC account instead of my Google Talk account. After checking your post I spotted my mistake. All is not sorted and noted for future reference.:D

---

