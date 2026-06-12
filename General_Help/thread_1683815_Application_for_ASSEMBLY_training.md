---
title: "Application for ASSEMBLY training???"
date: 2011-02-08
forum: General Help
---

### Post by 71GA on 2011-02-08
Hello i am new to programming world and am trying to understand ARM core. I need an application to help me understand / **train** assembly language. 

If anyone knows a good application for this i would appreciate a link or something. 


Thank you.

---

### Post by sanderd17 on 2011-02-08
For the mips language I used QTspim, I don't know about something like that for ARM.

---

### Post by tredegar on 2011-02-08
Just put **arm assembler code** into google.

[This]("http://www.heyrick.co.uk/assembler/") is the first link and it looks quite good.

---

### Post by Habitual on 2011-02-08
[http://lmgtfy.com/?q=learning+assembly+%2BARM](http://lmgtfy.com/?q=learning+assembly+%2BARM)

...was that so hard?

---

### Post by 71GA on 2011-02-08
Maybe if you would actually **read** my post you would post a useful post. Instead you write nonsense. I asked for application not literature... I have a good book about assembly language, but i need to test my examples in a simulation program or something...

---

### Post by Habitual on 2011-02-08
Linux is a self-serve environment.
No one is here to wait on you.

---

### Post by 71GA on 2011-02-08
> **Habitual said:**
> Linux is a self-serve environment.
No one is here to wait on you.
Stop posting nonsense in my topic :). Post me a link to any application that i seek here or choose a different topic to spam.

---

### Post by tredegar on 2011-02-08
71GA

You don't seem to be in a very good mood, but please understand that most of us are _trying_ to help, and perhaps you did not pose your question very well.

> I have a good book about assembly language, but i need to test my examples in a simulation program or something...
OK.

Now I understand your problem better. Try [this]("http://simit-arm.sourceforge.net/") for an ARM simulator that runs on linux.

---

### Post by 71GA on 2011-02-08
I apologize to anyone if i offended them. My problem wasn't written as clearly as i thought it was and then i got mad for people saying i cant google it. Well i think this is something what i have been looking for.

Thank you.

---

### Post by tredegar on 2011-02-08
> I apologize to anyone if i offended them. My problem wasn't written as clearly as i thought it was and then i got mad for people saying i cant google it.
Your apology is accepted. Perhaps you have learnt something.

Good luck with the ARM coding and simulation.

Best wishes.

---

### Post by 71GA on 2011-02-09
> **tredegar said:**
> Your apology is accepted. Perhaps you have learnt something.

Good luck with the ARM coding and simulation.

Best wishes.
That program unfortunately wont install on my ubuntu 10.10. ... When i use command make i get error 1...

---

### Post by davesmith2288 on 2011-02-09
This site is very informative.  You have shared us great topic.  I'm happy I come up with this site.  Thanks!

[south florida mortgage](http://homefinancingcenter.com/)

---

### Post by tredegar on 2011-02-09
> When i use command make i get error 1...
That doesn't tell me much, but maybe the package is just too old now.

Did you look at **skyeye** and **softgun** that are in the ubuntu repositories?

---

### Post by 71GA on 2011-02-09
> **tredegar said:**
> That doesn't tell me much, but maybe the package is just too old now.

Did you look at **skyeye** and **softgun** that are in the ubuntu repositories?

I installed those 2 packages, but i still get an error 2. Here it is 
```
make[1]: Entering directory `/home/ziga/projects/simlt-arm'
Making all in emulator
make[2]: Entering directory `/home/ziga/projects/simlt-arm/emulator'
if g++ -DHAVE_CONFIG_H -I. -I. -I..     -O3 -finline-limit=5000 -fomit-frame-pointer -MT armemul.o -MD -MP -MF ".deps/armemul.Tpo" -c -o armemul.o armemul.cpp; \
    then mv -f ".deps/armemul.Tpo" ".deps/armemul.Po"; else rm -f ".deps/armemul.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..     -O3 -finline-limit=5000 -fomit-frame-pointer -MT emumem.o -MD -MP -MF ".deps/emumem.Tpo" -c -o emumem.o emumem.cpp; \
    then mv -f ".deps/emumem.Tpo" ".deps/emumem.Po"; else rm -f ".deps/emumem.Tpo"; exit 1; fi
emumem.cpp:498: error: explicit template specialization cannot have a storage class
emumem.cpp:499: error: explicit template specialization cannot have a storage class
emumem.cpp:500: error: explicit template specialization cannot have a storage class
emumem.cpp:501: error: explicit template specialization cannot have a storage class
emumem.cpp:520: error: explicit template specialization cannot have a storage class
emumem.cpp:521: error: explicit template specialization cannot have a storage class
emumem.cpp:522: error: explicit template specialization cannot have a storage class
emumem.cpp:523: error: explicit template specialization cannot have a storage class
make[2]: *** [emumem.o] Error 1
```

---

### Post by tredegar on 2011-02-09
I don't know what is going wrong with your **make**, but **skyeye** and **softgun** seem to be ARM simulators themselves, not packages to help you compile the (last-updated-in-2007) simlt-arm.

See [here]("http://sourceforge.net/apps/trac/skyeye/wiki/ProcessorList") and [here]("http://sourceforge.net/projects/softgun/")

---

