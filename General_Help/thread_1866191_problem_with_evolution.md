---
title: "problem with evolution"
date: 2011-10-21
forum: General Help
---

### Post by iacoposk8 on 2011-10-21
Hello everyone! excuse my English.
 I recently installed Ubuntu 11.10 I have a problem with evolution (which I had with ubuntu 10.10)
 In my account I have specified the option to leave messages on the server.
 Under this option, I can say how many days to leave messages on the server.
 How can I specify that the messages they want to leave forever (unless for me to delete them)

 Second, because now I have downloaded the messages from the server, there is no way to put them back on? by evolution to server?

 Thanks:)

[IMG]http://www.siti-sottocosto.it/esempio9/ricezione.png[/IMG]

[IMG]http://www.siti-sottocosto.it/esempio9/opzioni.png[/IMG]

[IMG]http://www.siti-sottocosto.it/esempio9/invio.png[/IMG]

---

### Post by dcstar on 2011-10-21
> **iacoposk8 said:**
> Hello everyone! excuse my English.

 I recently installed Ubuntu 11.10 I have a problem with evolution (which I had with ubuntu 10.10)

 In my account I have specified the option to leave messages on the server.
 Under this option, I can say how many days to leave messages on the server.
 How can I specify that the messages they want to leave forever (unless for me to delete them)

 Second, because now I have downloaded the messages from the server, there is no way to put them back on? by evolution to server?


[LIST=1]
[*]Your English is good, well done.
[*]Set the "Days" to 9999, that should ensure that they are virtually left forever.
[*]E-mail the messages to your POP account, then they will be back on the server.
[/LIST]
You may also want to consider using IMAP, that may be more flexible and useful to you.

Just out of interest, this change to Evolution seems to have happened since version 3.1, my 2.28 version keeps the "Days" field as a separate option (like most other POP clients). I have put this in as a bug, feel free to add yourself to the "Affects Me" list:

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/879305](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/879305)

---

### Post by iacoposk8 on 2011-10-21
> **dcstar said:**
> 
Your English is good, well done.

you're too kind :D

> **dcstar said:**
> 
Set the "Days" to 9999, that should ensure that they are virtually left forever.

I'll do that, as a solution is not elegant, but functional! :)

> **dcstar said:**
> 
E-mail the messages to your POP account, then they will be back on the server.

so I have set in "receive mail" IMAP instead of POP? right?

> **dcstar said:**
> 
You may also want to consider using IMAP, that may be more flexible and useful to you.

Just out of interest, this change to Evolution seems to have happened since version 3.1, my 2.28 version keeps the "Days" field as a separate option (like most other POP clients). I may try to put this in as a bug.

you, report it as a bug that I think is more correct.
 Tonight I try to do everything!
 Thank you you have been very kind:)

---

### Post by iacoposk8 on 2011-10-21
nooooooooooooooooooo I did damage!
 there were only the mail on the server last week, the older ones have downloaded, my computer had all the mail ...
 I put imap and evolution has now updated correctly, but with the mail this week, now the old ones are lost!
 Tell me there's no way to recover them, which are somewhere in the evolution

---

### Post by iacoposk8 on 2011-10-22
and then I would have another problem ...
 when he asks for the password, I enter the store and then tell him.
 But every time I open evolution requires him to me, why?

---

### Post by dcstar on 2011-10-22
> **iacoposk8 said:**
> nooooooooooooooooooo I did damage!
 there were only the mail on the server last week, the older ones have downloaded, my computer had all the mail ...
 I put imap and evolution has now updated correctly, but with the mail this week, now the old ones are lost!
 Tell me there's no way to recover them, which are somewhere in the evolution

When you use IMAP you get an extra Inbox. The "old" e-mails will be in the original Evolution Inbox, which should still be there (this may have changed in version 3, I'm not sure).

---

### Post by iacoposk8 on 2011-10-24
you're right! I had not noticed! everything now works! thanks:)

---

### Post by dcstar on 2011-10-24
> **iacoposk8 said:**
> you're right! I had not noticed! everything now works! thanks:)

If you need to, you can "Drag and Drop" any/all the e-mails in the old Inbox to the IMAP Inbox. That way they will again be in the mail server.

PS, Mark the thread (read below).

---

### Post by iacoposk8 on 2011-10-24
Perfect! problem solved 100%

---

### Post by dcstar on 2011-10-25
> **iacoposk8 said:**
> Perfect! problem solved 100%

The Evolution developers have acknowledged the issue you raised as a priority bug, so **you** are responsible for starting the process of making Evolution better for all users.

Try doing that with a problem in Windows......

---

### Post by iacoposk8 on 2011-10-25
ubuntu for life :popcorn:

---

### Post by dcstar on 2011-11-28
There is now a fix for this in the Oneric "Proposed" repository, so someone might like to test it and then report back to the maintainers if it is fixed:

[https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/879305](https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/879305)

---

