---
title: "Ctrl+C to kill process in Terminal, Ubuntu-9.10"
date: 2009-12-03
forum: General Help
---

### Post by sushilsc on 2009-12-03
Hi,

  I just want to use combination Ctrl+c to kill the process running my terminal. I changed the Edit->Keyboard (in terminal) shortcuts for "Copy" to  Shift+Ctrl+C but still the killing of process with Ctrl+C does not work.

thanks in advance.

With best regards,
sushil

---

### Post by sushilsc on 2009-12-03
Does anyone have solution for this?????

---

### Post by sushilsc on 2009-12-03
I am surprise that no one knows about it or everyone knows except me :)

---

### Post by wojox on 2009-12-03
Ctrl+C does kill process in Terminal, Ubuntu-9.10. "Copy" is already  Shift+Ctrl+C, so it's rather confusing.

---

### Post by sushilsc on 2009-12-03
Thanks.

  My mistake, I was trying Ctrl+c instead of Ctrl+C.

  But I want to use a small c instead of C. How I can change that??

 Thanks a lot for you reply.

WIth best regards,
sushil

---

### Post by wojox on 2009-12-03
It is the small c. You could also use kill -9 <application> or pid from ps ux. Also the top command. You could try **reset** and see if it returns things back to normal.

---

### Post by doas777 on 2009-12-03
the behaviour you say you want, is the default. the terminal comes configured that way already. 
try going to Terminal -> Reset and Clear, and see if that puts you back to defaults.

---

### Post by sushilsc on 2009-12-03
No, I just realized that when I do Ctrl+c it does nothing!!!!

and When I do Ctrl+C then it seems that it gives following??  Seem I am missting something.... could you please help me to put it in order...Thanks

------------------------------------

Processing run.C...
Error in <TTree::SetBranchStatus>: unknown branch -> pat_phot_isoEcalRecHitR4
Error in <TTree::SetBranchStatus>: unknown branch -> pat_phot_isoHcalRecHitR4
Error in <TTree::SetBranchStatus>: unknown branch -> pat_phot_isohollowtrkconeR4
Events analysed till now  --->  0
^C
 *** Break *** keyboard interrupt run.C:7:

[sushil-laptop@Analysis_Code] Events analysed till now  --->  100000
Error in <TTree::SetBranchStatus>: unknown branch -> pat_phot_isoEcalRecHitR4
Error in <TTree::SetBranchStatus>: unknown branch -> pat_phot_isoHcalRecHitR4
Error in <TTree::SetBranchStatus>: unknown branch -> pat_phot_isohollowtrkconeR4
Events analysed till now  --->  200000

[sushil-laptop@Analysis_Code] Events analysed till now  --->  300000
Error in <TTree::SetBranchStatus>: unknown branch -> pat_phot_isoEcalRecHitR4
Error in <TTree::SetBranchStatus>: unknown branch -> pat_phot_isoHcalRecHitR4
Error in <TTree::SetBranchStatus>: unknown branch -> pat_phot_isohollowtrkconeR4
Events analysed till now  --->  400000

---

### Post by doas777 on 2009-12-03
do you have a background process running out of that terminal? ctrl  c will only kill a foreground process, and that looks like non-interactive output. a debugger perhaps?

could you paste in the entire terminal output from the line where you invoked the command, to the return to the prompt?

---

### Post by wojox on 2009-12-03
How do you do Ctrl+C, do you turn on caps lock ? When you invoke Ctrl+c it shows up as ^C.

---

### Post by sushilsc on 2009-12-03
I just check with other process and the Ctrl+c do the expected thing.....but giving problem with a particular job which I pasted......(I am running this job in foreground)....

Seems it has nothing to do with Ctrl+c but with the package I am using in this job...Let me check with the guys who wrote this package...then will come back to you....it may take some time!!!

But thanks a lot for your help and reply.

with best regards,
sushil

---

### Post by ibuclaw on 2009-12-03
> **sushilsc said:**
> No, I just realized that when I do Ctrl+c it does nothing!!!!

and When I do Ctrl+C then it seems that it gives following??  Seem I am missting something.... could you please help me to put it in order...Thanks

------------------------------------

Processing run.C...
Error in <TTree::SetBranchStatus>: unknown branch -> pat_phot_isoEcalRecHitR4
Error in <TTree::SetBranchStatus>: unknown branch -> pat_phot_isoHcalRecHitR4
Error in <TTree::SetBranchStatus>: unknown branch -> pat_phot_isohollowtrkconeR4
Events analysed till now  --->  0
^C
 *** Break *** keyboard interrupt run.C:7:

[sushil-laptop@Analysis_Code] Events analysed till now  --->  100000
Error in <TTree::SetBranchStatus>: unknown branch -> pat_phot_isoEcalRecHitR4
Error in <TTree::SetBranchStatus>: unknown branch -> pat_phot_isoHcalRecHitR4
Error in <TTree::SetBranchStatus>: unknown branch -> pat_phot_isohollowtrkconeR4
Events analysed till now  --->  200000

[sushil-laptop@Analysis_Code] Events analysed till now  --->  300000
Error in <TTree::SetBranchStatus>: unknown branch -> pat_phot_isoEcalRecHitR4
Error in <TTree::SetBranchStatus>: unknown branch -> pat_phot_isoHcalRecHitR4
Error in <TTree::SetBranchStatus>: unknown branch -> pat_phot_isohollowtrkconeR4
Events analysed till now  --->  400000

Looks to me that the application you are using **catches** Ctrl+C and continues on with the operation regardless.

Try instead **Ctrl+Z**, as that - I believe - is a an untrappable interrupt.


Regards
Iain

---

### Post by sushilsc on 2009-12-03
I believe Ctrl+Z suspend the job.....
 I wrote to the package guysand  waiting their response....

With best regards,
sushil

---

### Post by efflandt on 2009-12-03
Ctrl-c only kills a process that is running live in your terminal at the time.  It might not work if the process is within a loop.  If you see a regular shell prompt, there is no process to stop with Ctrl-c.

If you are trying to kill a background process, see **man kill**, then type **ps aux** to get the PID of the process you are trying to stop.

---

