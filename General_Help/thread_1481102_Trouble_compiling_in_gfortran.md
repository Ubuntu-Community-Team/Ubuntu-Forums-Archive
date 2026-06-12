---
title: "Trouble compiling in gfortran"
date: 2010-05-12
forum: General Help
---

### Post by jwenorthpark on 2010-05-12
I'm hoping someone can give me a little bit of help. I'm trying to compile a scientific code written in Fortran 77, and I don't know enough to troubleshoot effectively. I suspect "library pollution" from previous codes installed on my machine, but think forum users here will know better than I do. I would happily go about tracking down previous installations of gfortran and/or gcc, but I'm not sure what they were...

here's the error: 

> $gfortran foo.f 

Undefined symbols:
  "_time_", referenced from:
      _clock1_ in ccBwwyzx.o
ld: symbol(s) not found
collect2: ld returned 1 exit status
make: *** [codes] Error 1


suspecting library pollution, I wrote a simple fortran program (hello world style). 

helloworld.f is as follows:

      write(*,*) "Salutations, Earth."
      end

and it compiles and runs fine for me. 

I appreciate anyone's time sincerely.

---

### Post by jwenorthpark on 2010-05-13
An update to the previous post. Have now installed the latest version of Ubuntu and used Synaptic to acquire the listed gfortran package (4.4?) and at least one associated library (which was automatically selected). This is a totally fresh install on a wiped machine, ergo no library or linking issues should be present...

gfortran appears to operate without difficulty on my simple programs. however, when attempting to compile my code, the following results: 

> jwe@jwe:~/GNASH/current/general$ gfortran gnash.rsic04.f 
gnash.rsic04.f:392.51:

      data ki,kl,k7,ihole,iholm,inpgrd/5,9,7,1he,1hm,1/                 
                                                   1
Warning: Extension: Hollerith constant at (1)
gnash.rsic04.f:392.47:

      data ki,kl,k7,ihole,iholm,inpgrd/5,9,7,1he,1hm,1/                 
                                               1
Warning: Extension: Conversion from HOLLERITH to INTEGER(4) at (1)
gnash.rsic04.f:392.51:

      data ki,kl,k7,ihole,iholm,inpgrd/5,9,7,1he,1hm,1/                 
                                                   1
... 

many repetitions of this same essential warning message 

... 


Warning: Extension: Conversion from HOLLERITH to REAL(4) at (1)

/tmp/cciTgx6G.o: In function `clock1_':
gnash.rsic04.f:(.text+0xa4d4): undefined reference to `time_'
collect2: ld returned 1 exit status
jwe@jwe:~/GNASH/current/general$ 

as before, any help would be greatly appreciated.

---

### Post by jwenorthpark on 2010-05-13
or ....

should i post this somewhere else (this is not the most appropriate forum)?

---

### Post by anglican on 2010-05-13
> **jwenorthpark said:**
> /tmp/cciTgx6G.o: In function `clock1_':
gnash.rsic04.f:sad:.text+0xa4d4): undefined  reference to `time_'
collect2: ld returned 1 exit status
jwe@jwe:~/GNASH/current/general$                      
I don't think you can resolve this. It's a portability issue. If you install an older Ubuntu e.g. Jaunty or Hardy, you could then use gfortran-3.4 with libg2c to compile the code. Otherwise, re-write in "proper" fortran/C.

H

---

### Post by jwenorthpark on 2010-05-13
wow. that's ummm ... incredibly discouraging. 

thank you for the help though.

---

### Post by anglican on 2010-05-14
> **jwenorthpark said:**
> wow. that's ummm ... incredibly discouraging. 

thank you for the help though.
Provided your hardware is reasonably powerful, and you have a fair bit of disk space, why not try installing a virtual copy of Hardy. Virtualbox is easy to install (it's in the repos) and set-up so all you need is a Hardy install CD.

H

---

### Post by jwenorthpark on 2010-05-24
Went back to OS X and compiled twice successfully using evaluation versions of pgf77 and ifort. Thanks again for all the help.

---

### Post by anglican on 2010-05-24
> **jwenorthpark said:**
> Went back to OS X and compiled twice successfully using evaluation versions of pgf77 and ifort. Thanks again for all the help.
You're welcome - I'm sorry there didn't seem to be a linux solution to this problem.
H

---

