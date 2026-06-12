---
title: "MATLAB 7.3 overflow in R_X86_64_PC32 relocation"
date: 2010-03-18
forum: General Help
---

### Post by fabiosa on 2010-03-18
Hi All
I have installed ubuntu 9.10 64-bit and MATLAB 7.3 _x86-64.
When I run matlab launching script I get this error message and the program freezes:
/usr/local/matlab7.3/bin/glnxa64/MATLAB: Symbol `__kmp_test_then_add_real32' causes overflow in R_X86_64_PC32 relocation
/usr/local/matlab7.3/bin/glnxa64/MATLAB: Symbol `__kmp_test_then_add_real64' causes overflow in R_X86_64_PC32 relocation.

I tried to run "matlab -nojvm" and I get the same error as above but the program starts and seems to work smoothly. The problem is that I cannot run the editor and debug scripts and functions
Can you please help me in solving this issue?
thanks
Fabio

---

### Post by mark_a_kessler on 2010-06-03
Hi Fabio,
I use the same matlab version and I get the same error, but it started in 8lts and I still get it in 10lts; however, my matlab still runs fine even with all the graphical user interface turned on (jvm and desktop).

I'd be glad to answer any questions you have about my system.

-Mark

---

### Post by eag123123 on 2010-08-10
Try to set the environment variable MATLAB_JAVA to a correct path. 

E.g. (in my case I did this) in a terminal: export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.20/jre  and then try to start matlab as usual. 

That solved the same problem for me.

---

### Post by mark_a_kessler on 2010-08-12
I think the problem lies somewhere in Gnome.  I recently started not being able to run the gui also.  This isn't really a problem for me, so I just ignored it; however, I just switched from Gnome to Openbox, and now I can run the gui again.

-mark

p.s.
the MATLAB_JAVA environment variable didn't seem to help me

---

### Post by inaho on 2010-09-03
Hi eag123123,
could you please tell me in which file you add the path line 
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.20/jre
or did you just run it in a terminal?

thanks
barbara

---

