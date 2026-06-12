---
title: "rc.local doesn't work as advertised"
date: 2010-08-17
forum: General Help
---

### Post by jinglisparrish on 2010-08-17
Hi I am running 
8.04 on a Lippert PC104, no xwindows.  This is a little computer intended to just run one program headless in an instrument i am developing.  I would like to run this one program from boot.

The obvious answer is to add the program to rc.local followed by an &.  This doesn't work.  

I have tried adding all sorts of things to rc.local including mkdir, touch, echo etc etc.  the only utility that works is 'touch' which tells me that rc.local is getting executed.

I tried creating a new service called local and putting that in rc2.d as priority 80 using rc-update.d.  again, only touch worked.  

so i tried adding sleep 10 and running the utilities as daemons and still they won't run (except touch /var/lock/local).

Does anyone know of anything else to try?

Thank you

---

### Post by john newbuntu on 2010-08-17
Did you add the full path to your program in /etc/rc.local?  Also, can you redirect the stderr and stdout of this program to a file and check for anything odd?
Normally when you want services, you add a 'nohup' to the beginning of the program to prevent the program from getting killed when the parent script ends.  Was that done?
Are you using other methods like start-stop-daemon to kick off your program?

---

### Post by jinglisparrish on 2010-08-17
You make an excellent point and I will be sure to employ something like that when i run my program.   I am still curious as to why my tests didn't work.

I would love to figure out why something as simple as

mkdir ~/testdir

or 

echo "test" > ~/testfile.txt

doesn't work in local or rc.local  when touch does.  These utilities definitely finish before the sleep 10  that i put at the end of the service ends.



> **john newbuntu said:**
> Did you add the full path to your program in /etc/rc.local?  Also, can you redirect the stderr and stdout of this program to a file and check for anything odd?
Normally when you want services, you add a 'nohup' to the beginning of the program to prevent the program from getting killed when the parent script ends.  Was that done?
Are you using other methods like start-stop-daemon to kick off your program?

---

### Post by john newbuntu on 2010-08-17
Well, what does "~" refer to in this case when SysV style init scripts run? Is'nt that root?

---

### Post by jinglisparrish on 2010-08-17
hmmmm, another good point.  I took it for granted that it would end up in my /home/username account, but that probably doesn't make sense since the scripts must be running as root.  let me see if i can track it down.

---

### Post by jinglisparrish on 2010-08-17
john - 
you were right about ~, i was just saving things to the wrong  directory.  So that explains why the simplified service appeared not to  be working (doh!).  

nohup allowed me to run my script  in rc.local

Thank you so much for your help, that worked well
Cheers

---

