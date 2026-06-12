---
title: "College Network."
date: 2009-08-04
forum: General Help
---

### Post by jacklinux on 2009-08-04
So, before i came on holiday i gave a mini-lecture to my college about letting the IT Development suite have ubuntu installed on there computers and they said ok to it.
However before they put it in they asked some questions;


[LIST]
[*]How would we connect to the SQL server for student and staff accounts
[*]How would we set the rights of different accounts
[*]Does the security match windows - Any security problems known
[*]Would this make the windows side of the PC run slower (Dual Boot)
[/LIST]
Thanks in advance.

---

### Post by pedro3005 on 2009-08-04
To set the rights of different accounts, just go to System, Administration, then User and Groups. Security in linux is generally looked as better than windows, although i don't know much. I do know it comes with a firewall called iptables, so run 'man iptables' on a terminal or search google for information on it.
No, it will not affect Windows performance on dual-boot.

---

### Post by jacklinux on 2009-08-04
That helped however, still didn't anwser the main question
How would we connect to the SQL server for student and staff accounts?

---

### Post by jacklinux on 2009-08-04
So, before i came on holiday i gave a mini-lecture to my college about letting the IT Development suite have ubuntu installed on there computers and they said ok to it.
However before they put it in they asked some questions;


[LIST]
[*]How would we connect to the SQL server for student and staff accounts
[*]How would we set the rights of different accounts
[*]Does the security match windows - Any security problems known
[*]Would this make the windows side of the PC run slower (Dual Boot)
[/LIST]
Thanks in advance.

PS - Sorry for repost, no replys on other forum.

---

### Post by jacklinux on 2009-08-04
Bump!

---

### Post by Paddy Landau on 2009-08-04
I don't know the answer, but it would help for you to tell us what type of machine stores the SQL server (i.e. what operating system), and whether the machines are connected through a simple router.

Connecting on a network is reasonably simple, but can be quite fiddly.

If I were you, I'd install Ubuntu on only one machine and do a full and thorough test, carefully documenting how you got around every problem. That way you'll iron out the problems before rolling it out.

Are you considering Hardy 8.04 (LTS) or 9.04?

---

### Post by jacklinux on 2009-08-04
There going to use 9.04 as a start. And the SQL server is on Windows base.
The SQL server only has to connected to 15 ubuntu machines for a project.
Thanks.

---

### Post by hwttdz on 2009-08-04
3) does the security of ubuntu match windows?/are there known issues

I'm sure there are known security problems, however fewer than in windows and they are patched faster.  

4) would installing ubuntu slow down a dual boot machine?

Only at bootup, and even then only a few seconds as you have to chose which operating system to boot into.  

Perhaps you should rephrase your other questions.

---

### Post by jacklinux on 2009-08-04
Bump again! need a anwser.

---

### Post by halitech on 2009-08-04
I know this is going to sound silly but how do they connect to the SQL server in windows? Connections to a database server generally work the same way in windows and linux so if its a connection through a webpage, the coding would be the same.

---

### Post by jacklinux on 2009-08-04
no it connectons via a 3rd party client.
However, they said that they would make a new SQL server just for the ubuntu machines without the 3rd party client, any programs you know of?

---

### Post by halitech on 2009-08-04
MySQL and phpmyadmin are included in the repos so very easy to install. I'm guessing the third party app is a windows only client?

---

### Post by jacklinux on 2009-08-04
> **halitech said:**
> MySQL and phpmyadmin are included in the repos so very easy to install. I'm guessing the third party app is a windows only client?
Yes is it. i try'd it at home with WINE and the connecton is rubbish. So there going to try MySQL, maybe you'll see some applications from us :).
Thanks.

---

### Post by halitech on 2009-08-04
> **jacklinux said:**
> Yes is it. i try'd it at home with WINE and the connecton is rubbish. So there going to try MySQL, maybe you'll see some applications from us :).
Thanks.

unfortunately WINE is getting better but its not foolproof to run every program. Hopefully MySQL will work the way you want it to.

---

### Post by FIONEX on 2009-08-04
* How would we connect to the SQL server for student and staff accounts

Simple.  The SQL daemon, which should be running on the College's main servers, are seperate from the workstations that users use.  They have their own access management built-in.  Any linux SQL client lets you specify a server address, a username, and a password.

    * How would we set the rights of different accounts
Depending on what kind of server/user rights they're running, there might be a way to have ubuntu login directly.  Theoretically, their servers should be running linux based account control anyways.  If not, they'll have to specify what they're using so you can find a solution.

    * Does the security match windows - Any security problems known
Security in linux is of the highest quality.  If they have to worry about security, it's windows.  Every system has security holes, but the ones in linux are usually minor and are repaired much more rapidly.

    * Would this make the windows side of the PC run slower (Dual Boot)
Dual booting has NO EFFECT on the windows or linux side.  They're separated by partition barriers.  Unless there's major space constraints, there should be no problem what so ever.

---

### Post by jacklinux on 2009-08-04
> **FIONEX said:**
> * How would we connect to the SQL server for student and staff accounts

Simple.  The SQL daemon, which should be running on the College's main servers, are seperate from the workstations that users use.  They have their own access management built-in.  Any linux SQL client lets you specify a server address, a username, and a password.

    * How would we set the rights of different accounts
Depending on what kind of server/user rights they're running, there might be a way to have ubuntu login directly.  Theoretically, their servers should be running linux based account control anyways.  If not, they'll have to specify what they're using so you can find a solution.

    * Does the security match windows - Any security problems known
Security in linux is of the highest quality.  If they have to worry about security, it's windows.  Every system has security holes, but the ones in linux are usually minor and are repaired much more rapidly.

    * Would this make the windows side of the PC run slower (Dual Boot)
Dual booting has NO EFFECT on the windows or linux side.  They're separated by partition barriers.  Unless there's major space constraints, there should be no problem what so ever.
Thankyou. College has made a new SQL server and are using MySQL to connect. They also removed the log on and made it free for all users as the only ones in there are the students.Thankyou.

---

### Post by Paddy Landau on 2009-08-04
> **jacklinux said:**
> Bump again! need a anwser.
You're jolly impatient. Your first post was only an hour or so ago, yet you've bumped twice.

---

