---
title: "email to my apache server"
date: 2011-04-10
forum: General Help
---

### Post by vivek.pandey on 2011-04-10
hey everyone
    i have an apache server on my ubuntu 10.10... is it possible that whenever i connect my system to internet new emails on my id automatically are uploaded to my apache server and that i could read them later when i am offline,,, here by automatically i mean without me being logging in my email account .?

thanx to all

---

### Post by vivek.pandey on 2011-04-11
bump?

---

### Post by SeijiSensei on 2011-04-11
I'm not sure how you "read" the messages, but you could write a script that uses fetchmail that runs when Apache starts.

---

### Post by vivek.pandey on 2011-04-11
> **SeijiSensei said:**
> I'm not sure how you "read" the messages, but you could write a script that uses fetchmail that runs when Apache starts.
i am not asking you to write me a code, i will d it myself but can you please suggest a way how to start and go about writing one..

---

### Post by SeijiSensei on 2011-04-13
Well, I'd start by installing fetchmail and reading the documentation.  Then try to retrieve your mail from the server by running fetchmail from the command prompt.  

Thunderbird has an offline mode.  You could use that to get your mail and read it at your leisure.

---

