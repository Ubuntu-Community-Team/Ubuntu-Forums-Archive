---
title: "After updating to 10.10 Empathy went crazy"
date: 2010-10-17
forum: General Help
---

### Post by ilya222 on 2010-10-17
When i open up empathy it tries to connect and then displays all accounts in red and says "no reason specified"
Empathy itself refuses to connect, most of the time, it did connect once or twice for a few seconds and disconnected again,
and when it did connect, only the facebook chat was online, the gmail was still red.
help is welcome! :)

---

### Post by bvanaerde on 2010-10-20
Same problem here in 10.04. Not sure what is happening.
Only MSN seems to be a problem.

---

### Post by aust_paul on 2010-10-20
Me too! Any ideas?

---

### Post by bvanaerde on 2010-10-21
In [another thread]("http://ubuntuforums.org/showthread.php?t=905455#5") a temporary solution was proposed.
> killall telepathy-butterfly 
I haven't tried it myself yet, though.

---

### Post by psypher on 2010-10-21
killall telepathy-butterfly 
telepathy-butterfly: no process found
tried re-instaling telepathy-butterfly as well. no diff

---

### Post by howefield on 2010-10-21
Not a direct solution to the Empathy issue, but Pidgin seems to be connecting to the different protocols just fine. You might be able to use that till Empathy sorts out the problem.

Edit:
This appears to work.

[http://ubuntuforums.org/showpost.php?p=10003289&postcount=17](http://ubuntuforums.org/showpost.php?p=10003289&postcount=17)

---

### Post by Patiz on 2010-10-21
Hi all guys...

I googled alot for it... (actually solved it)

What i did:

1. Empathy (MSN) Worked yesterday.
2. sudo apt-get upgrad + update today
3. Empathy with Facebook worked, MSN stucked at "Connecting..." no further specific Message.
4. I searched some forums and tried alot... 

The only thing that helped me was THE LAST Post in this thread: 
[http://ubuntuforums.org/showthread.php?t=1307261&highlight=empathy](http://ubuntuforums.org/showthread.php?t=1307261&highlight=empathy) 
Quote: "sudo apt-get remove telepathy-butterfly" 

> Then disable and enable the account made it work again.
So far i didn't remark sg. unusual.


bb and happy communicating!

EDIT:  Audio and Video calls (outgoing) disconnects MSN in empathy. Didn't test incoming. I think it's corresponding with the uninstalled butterfly. Are there alternatives?

---

### Post by myboct on 2010-10-21
> **Patiz said:**
> Hi all guys...

I googled alot for it... (actually solved it)

What i did:

1. Empathy (MSN) Worked yesterday.
2. sudo apt-get upgrad + update today
3. Empathy with Facebook worked, MSN stucked at "Connecting..." no further specific Message.
4. I searched some forums and tried alot... 

The only thing that helped me was THE LAST Post in this thread: 
[http://ubuntuforums.org/showthread.php?t=1307261&highlight=empathy](http://ubuntuforums.org/showthread.php?t=1307261&highlight=empathy) 
Quote: "sudo apt-get remove telepathy-butterfly" 

> Then disable and enable the account made it work again.
So far i didn't remark sg. unusual.


bb and happy communicating!

EDIT:  Audio and Video calls (outgoing) disconnects MSN in empathy. Didn't test incoming. I think it's corresponding with the uninstalled butterfly. Are there alternatives?

I am using 10.4 currently. My MSN issue resolved after following your advice! Thanks a lot!! :)

---

### Post by Shadow15991 on 2010-10-23
The fix about changin the line of contacts worked excellent for me. the connected icon of my contacts changed, well. just use the fix it works like a charm!

---

### Post by Shadow15991 on 2010-10-23
> **Shadow15991 said:**
> The fix about changin the line of contacts worked excellent for me. the connected icon of my contacts changed, well. just use the fix it works like a charm!

howefield              **Re: After updating to 10.10 Empathy went crazy**
         Not a direct solution to the Empathy issue, but Pidgin seems to be  connecting to the different protocols just fine. You might be able to  use that till Empathy sorts out the problem.

Edit:
This appears to work.

[http://ubuntuforums.org/showpost.php...9&postcount=17]("http://ubuntuforums.org/showpost.php?p=10003289&postcount=17")

It WORKS.

---

