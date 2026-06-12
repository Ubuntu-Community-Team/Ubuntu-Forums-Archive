---
title: "Shell scripting help"
date: 2010-10-04
forum: General Help
---

### Post by taimaishu88 on 2010-10-04
I need to write a script to show how many days are left til a certain date and im not sure where to start. I already wrote one to greet me with a good morning etc...any suggestions?

---

### Post by dcstar on 2010-10-04
Yet another request for basic shell script help - is it that time of the year for assignments already?

Do people really expect to learn anything if they get others to do their work for them?

---

### Post by taimaishu88 on 2010-10-04
> **dcstar said:**
> Yet another request for basic shell script help - is it that time of the year for assignments already?

Do people really expect to learn anything if they get others to do their work for them?

As I said I'm not sure where to start. I did a "man date" and could not find the information I need. Not asking you to do any of my work for me. Competent enough to do my own if I can get a step in the right direction.

---

### Post by luvshines on 2010-10-04
Don't know if this is the best way, but it's very crude:

date -d "dd/mm/yyyy" +%s

This gives seconds since epoch to that date

Differece between 2 such dates will give you difference of seconds between dates.
Manipulate them accordingly

---

### Post by sisco311 on 2010-10-04
> **taimaishu88 said:**
> As I said I'm not sure where to start. I did a "man date" and could not find the information I need. Not asking you to do any of my work for me. Competent enough to do my own if I can get a step in the right direction.

I don't want to sound rude, but dcstar is right, the solution is trivial (just one line) and the right direction is **man date** and optionally **man bc**, but you can avoid bc.

If you can't find the solution yourself, then maybe you should drop the class and try something else.

---

### Post by cariboo on 2010-10-04
From the forum Code of Conduct:

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

This thread is closed

---

