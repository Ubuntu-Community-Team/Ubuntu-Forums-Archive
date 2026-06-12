---
title: "Upgraded 8.04 -&gt; 8.10 Evolution is missing/loosing mail messages"
date: 2009-09-15
forum: General Help
---

### Post by mbtiago on 2009-09-15
Hello/Olá/Hola/Salut/Ciao

I have been searching for 2 hours in these forums and found no answer (but similar problems unanswered).

I have the impression this could be a setup question (though I didn't set anything up). For example, anytime I get new mail (though I don't see it), my /home/manuel/.evolution/mail/local/inbox file changes. 
Could it be some kind of Evolution reading an older folder/database?


After today upgrading from Ubuntu 8.04 to 8.10, in Evolution my last 2 weeks messages are missing. Currenty, new messages seem to be downloaded but I can't find them in my Inbox, neither in Junk, nor anywhere else...

Doesn't seem to be any filter question, neither a question of not viewing hidden messages.

I didn't backup before upgrading, so I cannot restore.

I have only POP accounts: 1 gmail, another similar (both keep copy in server) and another that when I download they're no longer at the server.

I don't use exchange or anything else apart from webmail.

When I check for messages, they seem to be downloaded but I cannot find them anywhere: inbox, junk, etc. I even get notification of receiving new mail!


When I start Evolution in terminal, this is what I get:

"
** (evolution:21916): DEBUG: mailto URL command: evolution %s
** (evolution:21916): DEBUG: mailto URL program: evolution

(evolution:21916): camel-CRITICAL **: camel_object_is: assertion `o != NULL' failed

(evolution:21916): camel-CRITICAL **: camel_store_get_folder: assertion `CAMEL_IS_STORE (store)' failed

(evolution:21916): camel-CRITICAL **: camel_object_is: assertion `o != NULL' failed

(evolution:21916): evolution-mail-CRITICAL **: mail_tools_folder_to_url: assertion `CAMEL_IS_FOLDER (folder)' failed

"


Anybody can help? Thanks!

Ubuntu 8.10 (intrepid)
Evolution Version: 2.24.3

---

### Post by kstan_79 on 2009-09-28
I have same issue, after download email it simply disappear. I'm use Ubuntu 9.04. Any solution?

---

