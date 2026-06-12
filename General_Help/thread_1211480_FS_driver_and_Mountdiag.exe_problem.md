---
title: "FS driver and Mountdiag.exe problem"
date: 2009-07-12
forum: General Help
---

### Post by windy81 on 2009-07-12
Hello ladies and gentlemen.

I hope you will be kind to me and give some of your time to help a brethren out.;)

I have posted quite a lot of problems in succession and thanks to you all, i have sorted them out all out, but  i keep getting into muddy waters :(

i tried searching but no luck in finding anything relevant.

My problem is trying to get FS-Driver to Read and Write on my EX3 drives from WINDOWS XP.

Ubuntu is loaded on my external hard drive named dev/sdb 1

The *_EX3 partitions_* appear in My Computer as "_*drive T*_ (extended,swap)" and "_*drive U (primary,root)*_" that i manually chose in the installer. All is good so far.

However, when i try to access it says :-
"*The disk in drive U: is not formatted. Do you want to format it now*?"
"*The disk in drive T: is not formatted. Do you want to format it now*?"

so as per troubleshooting guide I download *mountdiag.exe* and try to run it.

This is where i cannot go any further.
_I type "*C:mountdiag :T*" in window and all i get is a black command screen flash up briefly and nothing else_. 
_I type "*C:mountdiag :U*" in window and all i get is a black command screen flash up briefly and nothing else_. 

i do not get a diagnostic screen come up with any suggestion as to the route of my problem.

what can i do to get *mountdiag.exe *working properly in windows ?
or
do you know what the problem is with accessing the partitions is without using it ?

any help appreciated.

thanks

windy81

---

### Post by windy81 on 2009-07-12
ok... .. someone must know, cmon' you experts where are you tonight ?? :P

---

### Post by windy81 on 2009-07-12
looks like everyone left the building.

---

### Post by chriskin on 2009-07-12
> **windy81 said:**
> ok... .. someone must know, cmon' you experts where are you tonight ?? :P


you posted this like 3 minutes after your first post, please don't bump before 24 or more hours have passed, or about 12 if it is urgent

as for the disks, there are other tools as well
check here [http://tombuntu.com/index.php/2008/03/19/four-applications-for-accessing-ext3-partitions-from-windows/](http://tombuntu.com/index.php/2008/03/19/four-applications-for-accessing-ext3-partitions-from-windows/)


first, though, try reinstalling fs-driver
it seems to be the best, are you sure you installed it ok?

---

### Post by windy81 on 2009-07-12
hey thanks, sry i kinda forget how large this forum is.

im gonna give you suggestion a try, see what happens

re install  and that alternative tool.

---

### Post by windy81 on 2009-07-14
so i installed Ex2fsd to see my EX3 partitions. it worked, a bit, but i didn't like it at all, its just a confusing little program.

But like evrything in ubuntu for me, at least, nothing is simple.

after un-installing ex2fsd, the drives are still there, but i cannot access them or anyhing in XP. they dont appear in Device manager..

All i see are 2 icons with a big red question mark assigned X and Z that i cannot get rid of.

can someone help me find a way to get rid of them ?

---

