---
title: "shutdows should wait on process"
date: 2011-08-24
forum: General Help
---

### Post by theklaas on 2011-08-24
Hello,

I have a small question.

We use a backup program, that start an sepparat process with the name SIDB.
When the server get an shutdown command. The normale back-up process is stoped. But the SIDB is not stopped correctly.  

But the shutdown proces should wait till the SIDB proces is stoped, and then proced with the shutdown process.

can you help me with a script.

thank,
Peter

---

### Post by dcstar on 2011-08-25
> **theklaas said:**
> Hello,

I have a small question.

We use a backup program, that start an sepparat process with the name SIDB.
When the server get an shutdown command. The normale back-up process is stoped. But the SIDB is not stopped correctly.  

But the shutdown proces should wait till the SIDB proces is stoped, and then proced with the shutdown process.

can you help me with a script.

thank,
Peter

You may have to set that up with Upstart:

[http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/)

---

### Post by theklaas on 2011-08-25
Hello Dcstare,

Thanks for your reply. 
I will read the infomation, and let you know if this is the answer for me.

thanks

---

