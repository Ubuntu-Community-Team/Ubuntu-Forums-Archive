---
title: "Another scripting question-"
date: 2010-03-02
forum: General Help
---

### Post by blur xc on 2010-03-02
I have a simple bash script, and a simple if then statement.  My question is regarding what to do if I want to show no output if a command completes successfully, and only give a message to the user if the command fails.  

Example-

```
if [command] ;then
    *do nothing if command is successful*
else
   echo There was a problem with the command
fi
```If I don't put anything between the "then" and "else" I get a syntax error.  If I have it do something, it does it for every time it goes through the while loop block it is in, which is annoying.

Thanks,
BM

---

### Post by StuartN on 2010-03-02
> **blur xc said:**
> I have a simple bash script, and a simple if then statement.  My question is regarding what to do if I want to show no output if a command completes successfully, and only give a message to the user if the command fails.

You can reverse the test, **if ! test ; then command ; fi**, or you can use the null command ":", **if test ; then : ; else command ; fi**.

---

### Post by blur xc on 2010-03-02
> **StuartN said:**
> You can reverse the test, **if ! test ; then command ; fi**, or you can use the null command ":", **if test ; then : ; else command ; fi**.

I knew there had to be reverse to that command - just couldn't find it in my shell scripting book...  Thanks!

BM

---

