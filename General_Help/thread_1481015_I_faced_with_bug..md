---
title: "I faced with bug."
date: 2010-05-12
forum: General Help
---

### Post by jungwook on 2010-05-12
Hello, everyone.

I ran programs in ubuntu 9.04.
The machine has 4  cores which frequency is 1Ghz. 
The memory size is 4Gbyte.


I ran 4 programs and then the message appeared.



[ 2192.584002] BUG: soft lockup - CPU#0 stuck for 61s! [pdflush:47]
 [ 2226.941502] BUG: soft lockup - CPU#3 stuck for 61s! [hald-addon-acpi:2246]
[ 2229.089002] BUG: soft lockup - CPU#2 stuck for 61s! [console-kit-dae:2124]
[ 2258.080021] BUG: soft lockup - CPU#0 stuck for 61s! [pdflush:47]

I wander the meaning of  [ 2258.080021].
And what is soft lockup?? Is it lock the core hold?? 
Lastly, in 61s! , s means second??

And is there any method to avoid this problems?

---

### Post by Jazzy_Jeff on 2010-05-12
This is a testimonials thread. If you want help with that you might want to post in absolute beginners or General Help.

---

### Post by jungwook on 2010-05-12
Hello, everyone.

I ran programs in ubuntu 9.04.
The machine has 4  cores which frequency is 1Ghz. 
The memory size is 4Gbyte.


I ran 4 programs and then the message appeared.



[ 2192.584002] BUG: soft lockup - CPU#0 stuck for 61s! [pdflush:47]
 [ 2226.941502] BUG: soft lockup - CPU#3 stuck for 61s! [hald-addon-acpi:2246]
[ 2229.089002] BUG: soft lockup - CPU#2 stuck for 61s! [console-kit-dae:2124]
[ 2258.080021] BUG: soft lockup - CPU#0 stuck for 61s! [pdflush:47]

I wander the meaning of  [ 2258.080021].
And what is soft lockup?? Is it lock the core hold?? 
Lastly, in 61s! , s means second??

---

### Post by iponeverything on 2010-05-12
> 
I wander the meaning of  [ 2258.080021].

Its a timestamp, converted by small perl script or just paste it in here [http://www.epochconverter.com/](http://www.epochconverter.com/)
> 
And what is soft lockup?? Is it lock the core hold?? 
Lastly, in 61s! , s means second??

No idea about the soft lockups. but the 61s is 61 seconds.

---

### Post by jungwook on 2010-05-12
Thank you for your reply.

> **iponeverything said:**
> Its a timestamp, converted by small perl script or just paste it in here [http://www.epochconverter.com/](http://www.epochconverter.com/)/ 


I visited [http://www.epochconverter.com/](http://www.epochconverter.com/) and then I inserted the numbers.
However the result is so weird.

Input is 2192.583999.

The output is **GMT**: Thu, 01 Jan 1970 00:36:32 GMT.

However I command "date" in the system.
The system said  2006. 04. 18. (&#54868;) 09:36:52 KST.

Is it right??

Does timestamp means the time when the bug appeared ?


> **iponeverything said:**
>  No idea about the soft lockups. but the 61s is 61 seconds.

Does the 61 second means the time when the bug maintain ??

I would be really happy if you give me more information.

Thank you in advance.

---

### Post by Ms_Angel_D on 2010-05-12
Not a Testimonial or Experience, Moved to General Support.

---

### Post by iponeverything on 2010-05-12
remove the .

2192583999 converts to 

GMT: Wed, 12 May 2010 17:32:15 GMT

> **jungwook said:**
> Thank you for your reply.




I visited [http://www.epochconverter.com/](http://www.epochconverter.com/) and then I inserted the numbers.
However the result is so weird.

Input is 2192.583999.

The output is **GMT**: Thu, 01 Jan 1970 00:36:32 GMT.

However I command "date" in the system.
The system said  2006. 04. 18. (&#54868;) 09:36:52 KST.

Is it right??

Does timestamp means the time when the bug appeared ?


That is when your system encountered the bug.

> 
Does the 61 second means the time when the bug maintain ??


That is probably how long the process was blocked in a waiting state. 
> 
I would be really happy if you give me more information.

Thank you in advance.

This is bug, I have no idea what is causing it. Might be MB chipset compatibility issues, bad hardware or anything.  What I would do test with 9.10 or 10.04. Also test your memory to make sure its good.

---

### Post by bodhi.zazen on 2010-05-12
I merged your two threads.

Please do not start multiple threads on the same topic as it results in duplication of effort and confusion.

---

