---
title: "Simple Mail Server For Testing IMAP"
date: 2009-12-22
forum: General Help
---

### Post by opticyclic on 2009-12-22
I'm testing some code that adds/deletes folders using IMAP.
Is there a simple mail server that I can run on localhost?

I want to create a dummy email account e.g. test@localhost
Then be able to connect to that account via IMAP.
First with Thunderbird, then with my code.
I don't own a domain or have a static ip so all of it has to be local.

I say simple as I don't want to be pasting 5 pages of command lines to get it going.
A mock/simulated mail server is OK as well, as long as I can connect to it with IMAP and Thunderbird.

---

### Post by dcstar on 2009-12-22
> **opticyclic said:**
> I'm testing some code that adds/deletes folders using IMAP.
Is there a simple mail server that I can run on localhost?

I want to create a dummy email account e.g. test@localhost
Then be able to connect to that account via IMAP.
First with Thunderbird, then with my code.
I don't own a domain or have a static ip so all of it has to be local.

I say simple as I don't want to be pasting 5 pages of command lines to get it going.
A mock/simulated mail server is OK as well, as long as I can connect to it with IMAP and Thunderbird.

postfix is already installed by default.

---

### Post by opticyclic on 2009-12-23
Thanks for the reply.
Its a bit embryonic though.

How do I do the rest of the stuff
i.e. 
How would I use it to create a dummy email account @localhost
What IMAP settings would I use to connect to it?

---

