---
title: "Run script from script"
date: 2011-10-31
forum: General Help
---

### Post by mybrain87 on 2011-10-31
I am running a script, lets call that ScriptA.
Now i want to start ScriptB from within that script so it runs when the first one finishes.

How can I do that?

---

### Post by Drenriza on 2011-10-31
> **mybrain87 said:**
> I am running a script, lets call that ScriptA.
Now i want to start ScriptB from within that script so it runs when the first one finishes.

How can I do that?

Cant you just at the end of scriptA place the fullpath to scriptB.

A question i have been wondering is as follows.
If i have scriptA which call another script, in the middle of it. How can i then

#1 Pause scriptA while scriptB runs.
#2 When scriptB finishes, return and continue scriptA.

Thread hijacking in progress.

---

### Post by JCM_Pico on 2011-10-31
> **mybrain87 said:**
> I am running a script, lets call that ScriptA.
Now i want to start ScriptB from within that script so it runs when the first one finishes.

How can I do that?

You can call scriptB at the middle of scriptA by just typing ```
sh scriptB.sh 
``` or ./pathtoscript/scriptB.sh

**and for the the thread hijacker:**
   
If you get the pid of the process os scriptB you can make ```
wait $pid
```
But for your description you can simply run scriptB at the end of scriptA, as I described before.

---

### Post by mybrain87 on 2011-10-31
> **Drenriza said:**
> Cant you just at the end of scriptA place the fullpath to scriptB.

A question i have been wondering is as follows.
If i have scriptA which call another script, in the middle of it. How can i then

#1 Pause scriptA while scriptB runs.
#2 When scriptB finishes, return and continue scriptA.

Thread hijacking in progress.

Tried that before but put the path wrong...stupid mistake...now i tried again and its working. Thanks.

And the Thread hijacking is okay, as i would like to know the answer to that one myself

---

### Post by mybrain87 on 2011-10-31
Is there also a way to start a perl script from within a shell script.

Tried doing 
perl ./pathtoscript/script.pl

but thats not working

---

### Post by Drenriza on 2011-11-10
> **JCM_Pico said:**
> You can call scriptB at the middle of scriptA by just typing ```
sh scriptB.sh 
``` or ./pathtoscript/scriptB.sh

**and for the the thread hijacker:**
   
If you get the pid of the process os scriptB you can make ```
wait $pid
```
But for your description you can simply run scriptB at the end of scriptA, as I described before.

What would be the best way to get a pid from a script, started by another script so that i can issue the
> wait $pid
command? And also so your sure you get the correct pid.

---

