---
title: "HELP please - using gfortran to compile f77"
date: 2010-09-19
forum: General Help
---

### Post by freddyc on 2010-09-19
Hi everyone,

I am new to the ubuntu/linux community. Hope I can get some help here. Thanks a lot first.

I need to compile some pretty old fortran 77 files. The compiler I have is gfortran. But I got something like the following warning:

Warning: Deleted feature: ASSIGN statement at (1)
linp.f:386.19:

   20    GO TO NEXT,(30, 50, 70, 110)                                   
                   1
Warning: Deleted feature: Assigned GOTO statement at (1)
linp.f:388.72:

      ASSIGN 50 TO NEXT                                                 
                                          
I did a little search and found that the ASSIGN statement was deleted in Fortran 90/95. I wonder is there any way to modify the old code a little bit to meet the current standard. Or say, what's the f90/95's equivalent expression for ASSIGN in f77. Thanks.

---

### Post by anglican on 2010-09-20
As you've discovered, assigned goto is deprecated in f90 (and deleted from f95 I believe - not quite sure on that). To fix the code to avoid           using deprecated assigned gotos, you can perform the following           steps:           
                        
            (a) change each of the ASSIGN N TO NEXT (where N is             some number) statement to a simple NEXT = N statement             (where N is the same number), and             
            
            (b) replace each of the GO TO NEXT, (x, y, z, ...)             statement with the following *computed goto*             statement             
            
            GO TO (1,2,3,4,5,6,7,8,9,10,11) NEXT

H

---

