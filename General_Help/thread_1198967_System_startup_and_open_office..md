---
title: "System startup and open office."
date: 2009-06-28
forum: General Help
---

### Post by marticc on 2009-06-28
Hi, I' ve got a little problem that you might help me to fix.

Everytime I start my Ubuntu 9.04, the writer OPenoffice 3.1 starts automatically (so it takes longer to start my UBuntu).

I have tried using the system startup tool to prevent OpenOffice from starting everytime I start my PC, but despite the fact that I unchecked the OPen Office box, i still have the same problem.

I would be grateful if you could help me.

Thx.

---

### Post by swisstone198 on 2009-06-28
Is there an entry for openoffice in either /etc/init.d/ or /etc/rc2.d/?

---

### Post by marticc on 2009-06-28
hi, Thank you for your answer.

I don't have any entry for open office neither in /etc/init.d nor in /etc/rc2.d

---

### Post by marticc on 2009-07-04
Hi,

Doesn't anyone have any solution for this problem?. I would really appreciate any help you can give me.

Thanks

---

### Post by michy99 on 2009-07-04
1. System->Administration->Startup Applications

2. Options tab, Make sure 'Automatically remember' box is checked.

3. Close all applications and log out.

4. Log in. Uncheck the box you checked above.

---

### Post by marticc on 2009-07-05
Hi, thanks for your answer, it solved the problem!!

Thanks for your help.

---

