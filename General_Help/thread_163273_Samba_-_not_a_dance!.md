---
title: "Samba - not a dance?!"
date: 2006-04-20
forum: General Help
---

### Post by fredrik_human on 2006-04-20
Hi, i'm trying to set up filesharing between my xp- and ubuntu machines using Samba. I have come that far as when i search the network for other computers from my xp machine, i see my linux macine and the folder i shared there. When i try to open that folder it prompts me for a password stating me as \\"myComputer"\guest. I don't know why because in smb.conf i never stated "guest ok = yes". However i type in my user password for the ubuntu machine and get refused. I've tried all passwords i know :) but it just wont let me in. In configuring the smb.conf file i followed "rubrboots" advice to "joeartis" question on "Sharing folders or Drives" in the forum, only adding "security = share" and as one of my own ideas, a [files] entry stating the "path" and "writeable = yes". 

I would much appriciate if someone could give me any advice on this matter. 

//Fredrik, Sweden

---

### Post by cgjones on 2006-04-20
Do you have the setting public = yes for the folder you are trying to share?

---

### Post by fredrik_human on 2006-04-20
Thanks man, that one did it. 

I was curious though, is this safe, this i'm doing now? From an intruder perspektiv? Or can anyone hacker just go about in my shares, due to some safety issue i've forgotten or don't know about? I just wonder since i really have no idea of what i'm doing.

//Fredrik

---

### Post by cgjones on 2006-04-20
If this is on a local lan, behind a hardware firewall/router, you should be pretty safe. In smb.conf, you can set rules as to which IP addresses can connect. I forget the exact syntax, but I think it goes something like this:
```

hosts allow = 192.168.X.

```
X is most likely 0, though it might be different if you've changed it. You can set this in global or per share. Check out the following link for lots more info on Samba.
[http://us4.samba.org/samba/docs/using_samba/toc.html](http://us4.samba.org/samba/docs/using_samba/toc.html)

P.S. Don't forget to run testparm after you make changes to smb.conf. This will warn you of syntax errors.

---

### Post by fredrik_human on 2006-04-21
Thanks for the help, works like a charm. This is a good forum with competent users.

---

### Post by cgjones on 2006-04-21
No problem. It's always nice to be able to help out a fellow Ubuntu user.

---

