---
title: "does ubuntu keep track of actions?"
date: 2010-11-26
forum: General Help
---

### Post by flyingsliverfin on 2010-11-26
does ubuntu have something like a firefox history except for the entire system? does it keep track of what u do?

Something that i noticed that is that every time i open an open office file an text doc appears called .~lock.The_Name.odt# and it contains the user who opened it, the date, the time, and the program that opened it (in this case file:///home/meeeee/.openoffice.org/3;)

---

### Post by wilee-nilee on 2010-11-26
Shh don't tell anybody but didn't you hear about the NSA backdoor. ;)

Seriously look on the web. You will not get complete answers here or anywhere really. A specific question is needed here; to generalized for consumption then spit out in your general direction to try and figure out.

---

### Post by efflandt on 2010-11-26
Some programs may use a lock file so that more than one person does not open the same file for editing at the same time.  Others may create a backup file periodically in case you forget to save what you are doing.

Anything you do in a text terminal or console (bash) is recorded in **~/.bash_history**, primarily for recalling previously used commands with the up cursor (even from a previous login session).  However, I am not sure what order they end up in if you have more than one terminal open at a time.  That is one reason why it is not a good idea to put plain text passwords in command lines (another reason is because other users could see command lines of any currently running programs with **ps aux**).

But there is nothing that generally records that you opened this program or that program with a click of the mouse or what you did in that program, unless something generates an error that ends up in /var/log/, or you install something to specifically monitor that.

---

### Post by ivarn on 2010-11-26
This is an interesting thread actually.
I know the police are using history trackers for windows, but I really don't know what the linux alternatives are.

---

### Post by wilee-nilee on 2010-11-26
> **ivarn said:**
> This is an interesting thread actually.
I know the police are using history trackers for windows, but I really don't know what the linux alternatives are.

It was a joke.

---

### Post by oldos2er on 2010-11-26
Zeitgeist: "Description: event logging framework

 Zeitgeist is a service which logs the user's activities and events (files
 opened, websites visited, conversations hold with other people, etc.) and
 makes the relevant information available to other applications.
 .
 It serves as a comprehensive activity log and also makes it possible to
 determine relationships between items based on usage patterns."

---

### Post by ivarn on 2010-11-27
> **wilee-nilee said:**
> It was a joke.
The message wasn't a reply to you.
But ok, what was a joke? I read your message but I can't find any jokes there.
Nothing about that message made me giggle.
Or was it a pc joke? you know, a joke that no-one gets but the guy who made it.
A pc joke is a joke you brainstormed around for more than 2 minutes, posted it and then you felt like a hero. JK :D

---

### Post by oleink on 2010-11-27
> **flyingsliverfin said:**
> does ubuntu have something like a firefox history except for the entire system? does it keep track of what u do?

Something that i noticed that is that every time i open an open office file an text doc appears called .~lock.The_Name.odt# and it contains the user who opened it, the date, the time, and the program that opened it (in this case file:///home/meeeee/.openoffice.org/3;)

There is a history log thing under system (?)  Sorry I could tell you exactly but I'm not on ubuntu right now.  My Ubuntu computer broke (fried motherboard) and I have to build a computer before I get Ubuntu again (my signature is my new build)

---

### Post by oleink on 2010-12-29
Just got my install back:

Places -> Recent Documents

You can clear this section apparantly

---

