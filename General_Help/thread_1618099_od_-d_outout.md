---
title: "od -d outout"
date: 2010-11-10
forum: General Help
---

### Post by Nikolazigic on 2010-11-10
I get this:
0000000  1202     0     0     0     0     0     0     0
0000020   141    89    63    89   141     0     0     0
0000040     0     0     0     0     0     0     0     0
*
0002260     0     0     0     0     0  1202     0     0
0002300     0  1202     0     0     0     0     0     0
0002320     0   122    61     0    61   122     0     0
0002340     0     0     0     0     0     0     0     0
*
0004560     0     0     0     0     0     0  1202     0
0004600     0     0  1202     0     0     0     0     0
0004620     0     0   132    83    59    83   132     0
0004640     0     0     0     0     0     0     0     0
*
0007060     0     0     0     0     0     0     0  1202
0007100     0     0     0  1202     0     0     0     0
0007120     0     0     0   167   132   118   132   167
0007140     0     0     0     0     0     0     0     0
*
0011400  1202     0     0     0  1202     0     0     0
0011420     0     0     0     0     0     0     0     0
*
0013700     0  1202     0     0     0  1202     0     0
0013720     0     0     0     0     0     0     0     0
*
0016200     0     0  1202     0     0     0  1202     0
0016220     0     0     0     0     0     0     0     0
*
0020500     0     0     0  1202     0     0     0  1202
0020520     0     0     0     0     0     0     0     0
*
0023000     0     0     0     0  1202     0     0     0
0023020  1202     0     0     0     0     0     0     0
0023040     0     0     0     0     0     0     0     0
*
0025300     0     0     0     0     0  1202     0     0
0025320     0  1202     0     0     0     0     0     0
0025340     0     0     0     0     0     0     0     0
*
0027600     0     0     0     0     0     0  1202     0
0027620     0     0  1202     0     0     0     0     0
0027640     0     0     0     0     0     0     0     0
*
How to go from decimal to numerical values?

---

### Post by Hippytaff on 2010-11-10
What are you trying to do? Need more info :-)

---

### Post by Nikolazigic on 2010-11-10
This is the output of the code I am using.In order to go further I am trying to btain ASCII from binary.The code is FORTRAN 77,it writes this way:
if(istype.ne.1) then
             open(36, file=tfile, form='unformatted') 
           end if
c
           do 131 k=1,nz
              do 131 j=1,ny
                 do 171 i=1,nx
                    if(time(i,j,k).gt.1.e9) time(i,j,k)=0.
171                 itime(i)=time(i,j,k)*tmult
131              write(36) (itime(i),i=1,nx)
           close(36)
         end if

---

### Post by Nikolazigic on 2010-11-10
I also do not get what this values 0000000,0000020,000040 represent?

---

### Post by Hippytaff on 2010-11-10
Way beyond me I'm afraid :-)

---

