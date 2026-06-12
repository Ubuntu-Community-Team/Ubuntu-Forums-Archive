---
title: "A bit of xchat IRC help needed..."
date: 2006-05-20
forum: General Help
---

### Post by djsroknrol on 2006-05-20
I have xchat IRC set up and working, but have a problem that I hope someone can help with..

In preferences>File Transfers, I have "auto accept file transfers" enabled, so I don't have to be there to accept manually, but it doesn't seem to work....is there something wrong with the install or am I missing something?

Any help would be great...

---

### Post by unnes on 2006-05-20
In the XChat input box, type the following:

```
/set dcc_auto_send 1
```

---

### Post by djsroknrol on 2006-05-20
And what does that do? You mean type that in the box in the bottom?

---

### Post by unnes on 2006-05-20
Yeah, type it in where you'd normally type in chat text. It'll automatically accept DCC sends. Perfect when you queue up several downloads from an XDCC bot and leave the computer.

---

### Post by djsroknrol on 2006-05-20
Thanks unnes...I'll try that...

---

### Post by pedalwrench on 2007-04-24
> **unnes said:**
> In the XChat input box, type the following:

```
/set dcc_auto_send 1
```

thx, that worked for me.  i edited the .xchat2/xchat.conf to make it permanent.

---

### Post by HeinekenPissr on 2007-08-03
what exactly did you edit in the .xchat2/xchat.conf file to change this permanently?

---

### Post by Rog-Mahal on 2007-08-23
Hmm, I have set my client up the way you suggested and I am still unable to receive any transfers. Any other advice? Could there be a firewall issue?

---

