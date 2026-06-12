---
title: "Message Popup Question"
date: 2010-09-12
forum: General Help
---

### Post by Crizzie on 2010-09-12
Hi,

I'm still very new to Ubuntu and I'm trying to figure out what this is called that's able to display these messages. Is this from a certain lib or something? I don't know how to program in C or C++, but I'm pretty decent with python ( I've only used this on Windows ) and I was wondering if there was a way I can display my notifications like that as well. If you could just tell me what causes these messages to display like this I'm sure I could do some investigating of my own.

---

### Post by Rubi1200 on 2010-09-12
This is a message from a program called FileZilla:
[http://filezilla-project.org/](http://filezilla-project.org/)

I assume you installed it?

---

### Post by sikander3786 on 2010-09-12
> **Rubi1200 said:**
> This is a message from a program called FileZilla:
[http://filezilla-project.org/](http://filezilla-project.org/)

I assume you installed it?
I think he wants to learn how to pop up custom messages. Am I right?

---

### Post by Crizzie on 2010-09-12
> **Rubi1200 said:**
> This is a message from a program called FileZilla:
[http://filezilla-project.org/](http://filezilla-project.org/)

I assume you installed it?

I kind of knew that much already.. yeah I installed it. What I wanted to ask though, is how would I be able to replicate that message. I've seen other applications display messages in the same fashion and I was wondering if there is a name for messages that display like that.

---

### Post by sikander3786 on 2010-09-12
> **Crizzie said:**
> I kind of knew that much already.. yeah I installed it. What I wanted to ask though, is how would I be able to replicate that message. I've seen other applications display messages in the same fashion and I was wondering if there is a name for messages that display like that.
Seen this?

[https://wiki.ubuntu.com/NotifyOSD](https://wiki.ubuntu.com/NotifyOSD)

---

### Post by morgan_greywolf on 2011-01-21
You've probably already found the answer to your question, but in case others are searching, the easiest way to this from, say, a shell script is the 'notify-send' command in the 'libnotify-bin' package.

---

