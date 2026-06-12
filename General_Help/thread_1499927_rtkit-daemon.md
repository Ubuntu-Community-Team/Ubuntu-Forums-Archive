---
title: "rtkit-daemon"
date: 2010-06-02
forum: General Help
---

### Post by Rumpletumbler on 2010-06-02
Can someone tell me why the real time daemon is showing two users when I only have one user on the system? 

Thanks.

Jun  2 11:18:14  rtkit-daemon[967]: Sucessfully made thread 1210 of process 1210 (n/a) owned by '1000' high priority at nice level -11.
Jun  2 11:18:14 rtkit-daemon[967]: Supervising 4 threads of 2 processes of 2 users.
Jun  2 11:18:15 rtkit-daemon[967]: Sucessfully made thread 1212 of process 1210 (n/a) owned by '1000' RT at priority 5.
Jun  2 11:18:15 rtkit-daemon[967]: Supervising 5 threads of 2 processes of 2 users.
Jun  2 11:18:15 rtkit-daemon[967]: Sucessfully made thread 1213 of process 1210 (n/a) owned by '1000' RT at priority 5.
Jun  2 11:18:15 rtkit-daemon[967]: Supervising 6 threads of 2 processes of 2 users.
Jun  2 11:18:16 rtkit-daemon[967]: Sucessfully made thread 1219 of process 1219 (n/a) owned by '1000' high priority at nice level -11.
Jun  2 11:18:16 rtkit-daemon[967]: Supervising 7 threads of 3 processes of 2 users.

---

### Post by cariboo on 2010-06-02
Most services run as a separate user, just check /etc/passwd to see a list of users.

---

### Post by bodhi.zazen on 2010-06-02
Moved to general help as I am not sure why you posted in the security section.

If you are wondering about users, you have many many more then one user, as cariboo907 indicated look at the contents of /etc/passwd.

This is completely normal.

Generally each service (mail, apache, etc), in your case rtkit-daemon, is assigned an account. This improves security by keeping such system processes isolated.

I am not aware of a "standard" set of users one could expect nor am I aware of a web page that explains all the default users.

---

