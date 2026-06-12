---
title: "Adding new users"
date: 2009-06-29
forum: General Help
---

### Post by stevie1989 on 2009-06-29
l've setted up new accounts for my mom, girlfriend and little brother too use Kubuntu (Want them to slowly stop using windows, so far less time fixing the computer :P)
Anyways, so l install FireFox, but now l need too install Flash, pdf reader, etc using Adept and it needs admin password, which l assumed was my password, but no theirs nor mine works. There's is unkown too sudo, while mine doesn't say it is, just says it's incorrect password. Any ideas? l also want them not too be able too change anything too dramtic but be able too use Adept, etc... Don't think it can be been told Linux is all about freedom and very customisable so that would be great :)

---

### Post by decoherence on 2009-06-29
> **stevie1989 said:**
> l've setted up new accounts for my mom, girlfriend and little brother too use Kubuntu (Want them to slowly stop using windows, so far less time fixing the computer :P)
Anyways, so l install FireFox, but now l need too install Flash, pdf reader, etc using Adept and it needs admin password, which l assumed was my password, but no theirs nor mine works. There's is unkown too sudo, while mine doesn't say it is, just says it's incorrect password. Any ideas? l also want them not too be able too change anything too dramtic but be able too use Adept, etc... Don't think it can be been told Linux is all about freedom and very customisable so that would be great :)

The admin password is the one you set when you installed Ubuntu. 

If you've forgotten it, see [here]("http://www.psychocats.net/ubuntu/resetpassword").

PS the grammar police have put out an APB on you ;)

---

### Post by stevie1989 on 2009-06-29
Ya l've never been good with grammar lol. Raised with French, English, and German languages screwed my grammar up. l'm going to give it a try.

Nope. Your username is unkown to KdeSudo.
Works for my user but l'm logged into a different account trying it.
How do l add a user too KdeSudo?

---

### Post by stevie1989 on 2009-06-29
l figured it out.
But is there a wiki too simplify the different group meanings in Kuser?

---

### Post by t0p on 2009-06-29
Are you adding your mother, girlfriend and brother to the sudoers group?  Are you sure you want to do that?  If you give them admin privileges, they will be able to do *anything* on the computer.  Including the ability to utterly destroy the system.

---

### Post by stevie1989 on 2009-06-29
l don't know how to explain it, but l just want them too be able to use Adept for random plugins, etc... since l'm bound too miss one or two, and l don't want too have too have to login each Acct. and install one by one.

Forgot too mention, allowing them too access the Windows drive for random files they have. My partition is not huge (9.96 GB) and they'll easily fill it with rubbish.

---

### Post by stevie1989 on 2009-06-30
bump.

---

### Post by stevie1989 on 2009-07-04
Fixed it. Had too edit User Groups under Kuser.

---

