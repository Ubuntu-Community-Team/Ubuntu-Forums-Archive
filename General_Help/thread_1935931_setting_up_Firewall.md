---
title: "setting up Firewall"
date: 2012-03-05
forum: General Help
---

### Post by johntd on 2012-03-05
Being new to Linux I would like to know how to set up my Firewall, I have GUFW running but only have it set to block incoming, is this okay or do I need more, as a silver surfer a lot of the techy stuff is a bit to much so if any one as the time to put things in easy to understand terms I would be much appreciated.(I am running Linux Ubuntu 11.10)

---

### Post by Bucky Ball on 2012-03-05
Many of us have never used one because no real need. Are you wanting to prevent infecting files you may pass on to a Windows machine? Are you using your machine for confidential/sensitive work purposes (a production machine attached to a work network)?

This link is not too techy and may help:

[https://help.ubuntu.com/community/Firewall#Introduction](https://help.ubuntu.com/community/Firewall#Introduction)

---

### Post by haqking on 2012-03-05
> **johntd said:**
> Being new to Linux I would like to know how to set up my Firewall, I have GUFW running but only have it set to block incoming, is this okay or do I need more, as a silver surfer a lot of the techy stuff is a bit to much so if any one as the time to put things in easy to understand terms I would be much appreciated.(I am running Linux Ubuntu 11.10)

[Dangertux do i need a firewall]("http://ubuntuforums.org/showthread.php?t=1871177")

[Dangertux guide on how to setup a firewall]("http://ubuntuforums.org/showthread.php?t=1876124")

[Basic Ubuntu Security Wiki]("https://wiki.ubuntu.com/BasicSecurity")

Yes you need more than inbound rules which alot of people dont understand.  You need good outbound rules also

Enjoy

Peace

---

### Post by haqking on 2012-03-05
> **Bucky Ball said:**
> Many of us have never used one because no real need. Are you wanting to prevent infecting files you may pass on to a Windows machine?

I think you are referring to AV/Malware and the OP asked about a firewall

---

### Post by johntd on 2012-03-05
I have done that and most seems to be okay all but my email, I cannot receive or send, what have I done wrong?

---

### Post by haqking on 2012-03-05
> **johntd said:**
> I have done that and most seems to be okay all but my email, I cannot receive or send, what have I done wrong?


Have you opened the correct ports for your email then ?

---

### Post by johntd on 2012-03-06
many thanks to all, I used the link to Dangertux guide to setting up firewall works great now.

---

### Post by haqking on 2012-03-06
> **johntd said:**
> many thanks to all, I used the link to Dangertux guide to setting up firewall works great now.

cool.

Glad you got it sorted.

remember to use the thread tools menu to mark the thread as solved.

Cheers

---

### Post by 3rdalbum on 2012-03-06
I don't bother with a firewall. My computer is not running any server services, and I'm not aware of any drive-by download Linux malware that could get onto my computer from the web browser. I doubt I would fall for an e-mailed ".sh" script either.

Too much work to set outbound rules and keep revising them with every new program. Computers should make things more efficient, not create tasks for us to waste our time. The payoff is not high enough.

If Linux ever develops a malware problem, THEN I might reconsider.

---

