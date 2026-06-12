---
title: "GetSystemTime in Ubuntu"
date: 2011-02-10
forum: General Help
---

### Post by akuleta on 2011-02-10
Hi,
i am looking for a function which does the same as in Win.
For example: Win->
                              SystemTime time_1;
                              GetSystemTime(&time_1); 
we can get the time.

In Ubuntun i incluade the header "time.h"
and then i have the following code:
   
                            CString writeString;
                            time_t time_1;
                            struct *tm tmss;
                            time_1 = Time(NULL);
                            /*Get the current time*/
                            tmss = locate(&time_1);
                             /* Format and print the tim*e/    
            strftime(writeString, sizeof(writeString),"%a %Y-%m-%d %H:%M:%S %Z",tmss); 

This gives me the date plus the time. I need also the Millisecond value. But the above function does not formate it.
Please Hlep

---

### Post by gmargo on 2011-02-10
The **time(2)** system call returns the time in seconds.  If you want a finer grain time value, use the **gettimeofday(2)** system call, which will give you the time in seconds plus microseconds.  Since **strftime(3)** operates on a "struct tm", derived from the seconds time value, you'll have to string together your own time representation to include milliseconds.

---

