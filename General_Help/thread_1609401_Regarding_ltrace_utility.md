---
title: "Regarding ltrace utility"
date: 2010-10-30
forum: General Help
---

### Post by mantosh4u on 2010-10-30
Hello folks,

If we check the "man ltrace"  it provide the following information.

---------------------------------------------------------------------------------------------------------------------------------
OPTIONS
-a, --align column
 Align return values in a specific column (default column is 5/8 of screen width).

 -A maxelts
Maximum number of array elements to print before suppressing the rest with an ellipsis ("...")

--------------------------------------------------------------------------------------------------------------------------------

I am interested in the 2nd option (-A maxelts). My intention is to increase the maximum number of array elements to print, When i go with default ltrace setting i am getting output like this :

 mantosh@ubuntu:~/Desktop/practice$** ltrace ./ofile **
__libc_start_main(0x8048514, 1, 0xbfb55324, 0x8048650, 0x8048640 <unfinished ...>
fopen("/home/mantosh/Desktop/practice/i"..., "r")                     = 0x8f15008
fopen("/home/mantosh/Desktop/practice/o"..., "w")                     = 0x8f15170
malloc(51)                                                            = 0x08f152d8
malloc(51)                                                            = 0x08f15310
fgets("The UNIX operating system provid"..., 50, 0x8f15008)           = 0x08f152d8
strcpy(0x08f15310, "The UNIX operating system provid"...)             = 0x08f15310
fputs("The UNIX operating system provid"..., 0x8f15170)               = 1


Now when i am tryting like this 

mantosh@ubuntu:~/Desktop/practice$ **ltrace -a 90 -A 90 ./ofile **
__libc_start_main(0x8048514, 1, 0xbfd650e4, 0x8048650, 0x8048640 <unfinished ...>
fopen("/home/mantosh/Desktop/practice/i"..., "r")                                        = 0x9666008
fopen("/home/mantosh/Desktop/practice/o"..., "w")                                        = 0x9666170
malloc(51)                                                                               = 0x096662d8
malloc(51)                                                                               = 0x09666310
fgets("The UNIX operating system provid"..., 50, 0x9666008)                              = 0x096662d8
strcpy(0x09666310, "The UNIX operating system provid"...)                                = 0x09666310
fputs("The UNIX operating system provid"..., 0x9666170)                                  = 1



Though i increased the  value of A = 90 , still no change from default output. i mean i am still getting the same array length inside a ("---") on any line line.


Any thought on this ?


Regards,
Mantosh Kumar:guitar:

---

