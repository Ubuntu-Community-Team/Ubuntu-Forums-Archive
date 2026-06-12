---
title: "Problem with Terminal"
date: 2011-06-18
forum: General Help
---

### Post by Karthik1985 on 2011-06-18
Hi,

   I have been using Ubuntu for quite sometime and recently installed  the latest version on Dell Inspiron mini 1012. In terminal when I press  ´Tab´ for completion,  it behaves funnily.

mv Black <Tab> <Tab> completes as
mv Black Rose.mp3 instead of     mv Black\ Rose.mp3

This problem does not occur when I use ´cd´ but occurs for most other commands.
How do I fix this problem?

Thanks.

---

### Post by prodigy_ on 2011-06-18
Hmm. Just an idea: maybe you have a broken auto_completion script in /etc/bash_completion.d/. [Read this for more info](https://bugzilla.redhat.com/show_bug.cgi?id=677446).

---

### Post by Karthik1985 on 2011-06-18
That was great. Your suggestion worked. prodigy_

I did try to comment out the _filedir() in /etc/bash_completion.d/acroread.sh
but that did not work. I just deleted the file and now things are working fine. 

I just hope that deleting acroread.sh doesnt cause any strange behavior of acrobat products.

Thanks

---

