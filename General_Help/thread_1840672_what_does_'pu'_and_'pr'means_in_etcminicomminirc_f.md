---
title: "what does 'pu' and 'pr'means in /etc/minicom/minirc file ?"
date: 2011-09-08
forum: General Help
---

### Post by dskonnur on 2011-09-08
Hi All , 
 
I have a file called as /etc/minicom/minirc file . In this file i see :-
 
pr port /dev/ttys0
pu baudrate 115200
pu bits 8
pu parity N
 
and so on ...
 
Please let me know , what does 'pu' and 'pr' mean . 
 
Regards,
Deepak Konnur

---

### Post by Grenage on 2011-09-08
> **dskonnur said:**
> Hi All , 
 
I have a file called as /etc/minicom/minirc file . In this file i see :-
 
pr port /dev/ttys0
pu baudrate 115200
pu bits 8
pu parity N
 
and so on ...
 
Please let me know , what does 'pu' and 'pr' mean . 
 
Regards,
Deepak Konnur

I've pondered the same, but I never managed to find out.  It's oviously used as a reference so that it knows if it's a port reference/address (pr) or a port option (pu), but I have no idea what it stands for.

---

### Post by haqking on 2011-09-08
> **dskonnur said:**
> Hi All , 
 
I have a file called as /etc/minicom/minirc file . In this file i see :-
 
pr port /dev/ttys0
pu baudrate 115200
pu bits 8
pu parity N
 
and so on ...
 
Please let me know , what does 'pu' and 'pr' mean . 
 
Regards,
Deepak Konnur

> **Grenage said:**
> I've pondered the same, but I never managed to find out.  It's oviously used as a reference so that it knows if it's a port reference/address (pr) or a port option (pu), but I have no idea what it stands for.

pu = public
pr = private

From the days long ago where minicom was suid-root and users could only change some options. Basically obsolete nowadays.

---

### Post by Grenage on 2011-09-08
> **haqking said:**
> pu = public
pr = private

From the days long ago where minicom was suid-root and users could only change some options. Basically obsolete nowadays.

Great! Cheers for that; I remember looking high and low for an explanation at the time.

---

### Post by haqking on 2011-09-08
> **Grenage said:**
> Great! Cheers for that; I remember looking high and low for an explanation at the time.

 i know me too, i eventually emailed the minicom project and got the answer a while ago ;-)

---

### Post by dskonnur on 2011-09-09
Hi All . 
 
Thanks for the your answers . It cleared my doubts . 
 
Regards,
Deepak Konnur

---

### Post by haqking on 2011-09-09
> **dskonnur said:**
> Hi All . 
 
Thanks for the your answers . It cleared my doubts . 
 
Regards,
Deepak Konnur


NO problem, glad to help.

Remember to mark your thread as solved using thread tools menu to assist others when searching for solutions.

cheers

---

### Post by raja.genupula on 2011-09-09
> **haqking said:**
> pu = public
pr = private

From the days long ago where minicom was suid-root and users could only change some options. Basically obsolete nowadays.


Hye haqking , thank for this . i am also searched for this one but i didnt get it . 
thanks man .

---

### Post by haqking on 2011-09-09
> **raja.genupula said:**
> Hye haqking , thank for this . i am also searched for this one but i didnt get it . 
thanks man .


you are welcome, no worries.

---

