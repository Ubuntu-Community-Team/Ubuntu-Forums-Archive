---
title: "Moving local files to network share via terminal?"
date: 2009-12-26
forum: General Help
---

### Post by delata3 on 2009-12-26
Hi there.

I'm having a bit of trouble. Let me explain:

What I want to accomplish is to move a locally-stored .txt file to a (Windows) network share via terminal.

I can access the network share no problem. But to do so, I have to use smbclient. Normally, when I'm moving files, I would do the following:

```
mv ~/test.txt ~/Destination
```But now that I have to use smbclient, this method doesn't work. For example, I can't do this:

```
mv ~/test.txt smbclient \\\\shareBox\\share
```mv just doesn't work that way. So how would I go about doing this?


I could easily do this through the GUI with drag and drop, but I really want to get to know the command line well.

Thanks in advance!
[B][COLOR=Red]
EDIT: Solved it. I just used the cifs method instead. Basically mounted the share. See [here]("http://www.cyberciti.biz/faq/linux-mount-cifs-windows-share/").[/COLOR][/B]

---

### Post by QrK0 on 2009-12-28
If this issue is solved, please change the title adding [SOLVED] at the begining

---

### Post by lisati on 2009-12-28
+1 with the suggestion to mark things solved

---

### Post by delata3 on 2009-12-28
> **QrK0 said:**
> If this issue is solved, please change the title adding [SOLVED] at the begining
I marked it as solved the second I figured it out.

---

