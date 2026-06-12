---
title: "Moving folders with script"
date: 2010-02-08
forum: General Help
---

### Post by ghimakiran on 2010-02-08
Hi All,

I am a new guy to this forum, I need help in resolving below specified issue.

In my organization we are using Postfix as a mail server and i have been allocated to clean up the older mail boxes which are around 40,000+ folders in 1,00,000 folders.

Can any help me with the script moving folders with the list i have.

Regards,
Hima Kiran

---

### Post by hemimaniac on 2010-02-08
well there are a few commands you could try/read up on that may simplify your task, as your question is rather vague, one does not know if they are being moved, sorted then deleted (with respect to criteria, etc) but for large storage searching and manipulation, the 'find' command is one of the most customizable and powerful ones you can turn loose inside a *unix rig/box.

some examples;

find /path/to/files/* -type f -mtime +6 -exec rm {} \;
find /path/to/files/* -type d -mtime +144 | xargs mv /somewhere/you/want > /home/move.log

these are just a couple of literally endless uses of the find command, but it is truly customizable and very powerful, you SHOULD always use it with out exec or xargs first to see if it is finding all that apply

try man find

---

