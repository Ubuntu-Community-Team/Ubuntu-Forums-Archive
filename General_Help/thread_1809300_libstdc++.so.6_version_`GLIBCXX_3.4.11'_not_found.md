---
title: "libstdc++.so.6: version `GLIBCXX_3.4.11' not found"
date: 2011-07-21
forum: General Help
---

### Post by noobinabox on 2011-07-21
I am currently building a MEX file with the use of a Makefile.

Everything works great until I try to run the program.

When I do ldd xpass.mexa64, everything looks great except for this error at the top:

./xpass.mexa64: /usr/local/MATLAB/R2011a/sys/os/glnxa64/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by ./xpass.mexa64)

Can anyone shed some light as to how I can rectify this error?
I tried doing "aptitude search glibcxx" to see what I could find to no avail, and I've done a lot of googling.

Respectfully,
Noobinabox

---

### Post by karlson on 2011-07-21
> **noobinabox said:**
> I am currently building a MEX file with the use of a Makefile.

Everything works great until I try to run the program.

When I do ldd xpass.mexa64, everything looks great except for this error at the top:

./xpass.mexa64: /usr/local/MATLAB/R2011a/sys/os/glnxa64/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by ./xpass.mexa64)

Can anyone shed some light as to how I can rectify this error?
I tried doing "aptitude search glibcxx" to see what I could find to no avail, and I've done a lot of googling.

Respectfully,
Noobinabox

You would need to install the compiler that built that library.

---

### Post by tommpogg on 2011-07-21
Take a look to [this thread]("http://ubuntuforums.org/showthread.php?t=808045"), it helped me to solve a similar problem.

---

### Post by noobinabox on 2011-07-21
Also, the reason I did ldd xpass.mexa64 was because on runtime it would spit the following error out:

??? Invalid MEX-file '/[path to the program]/xpassv3/xpass.mexa64': /[path to the program]/xpassv3/xpass.mexa64:
cannot dynamically load executable

I'm not sure if the GLIBCXX error is the cause of this runtime error. Also, thanks for that link tommpogg. I'm looking into that right now.

OK, the solution found at the thread linked by tommpogg worked great. I no longer see the GLIBCXX error when I do !ldd xpass.mexa64.

For those of you who stumbled on this thread looking for answers:

I removed both the symlink libstdc++.so.6 and its linked partner libstdc++.so.6*  in /$MATLAB/sys/os/glnxa64
and replaced both of them with their counterparts of similar names in found in /usr/lib. (i.e. ln -s /usr/lib/libstdc++.so.6*)

Then I repeated the process for libgcc_s.so.1, the only difference being that the replacement libgcc_s.so.1 was found in /lib for me.

---

### Post by tommpogg on 2011-07-22
Great!

Please, mark the thread solved

---

### Post by swissz on 2012-04-10
> **tommpogg said:**
> Take a look to [this thread]("http://ubuntuforums.org/showthread.php?t=808045"), it helped me to solve a similar problem.

Thanks tommpogg for the great link, it helped to solve my MATLAB problem!

---

