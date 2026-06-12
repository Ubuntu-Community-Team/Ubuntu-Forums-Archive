---
title: "VMWare Player install on 11.04 (For the love of god, please help me)"
date: 2011-05-07
forum: General Help
---

### Post by dannbunting on 2011-05-07
I have been using ubuntu since 8.04 and have also been using VMware player for over a year on ubuntu. I did a clean install of 11.04 and have been trying to install VMware player, but have been getting the following message in terminal: 

dann@Aries:~$ sudo sh '/home/dann/Downloads/VMware-Player-3.1.3-324285.x86_64.bundle' 
/home/dann/Downloads/VMware-Player-3.1.3-324285.x86_64.bundle: 110: Syntax error: newline unexpected
dann@Aries:~$ 

Can someone please help me? I need to get this running by the end of the weekend...:confused:

---

### Post by ayates on 2011-05-07
You'll need a newer version to run on 11-04(VMware-Player-3.1.4-385536).

---

### Post by reliablepankaj on 2011-05-07
same problem here..

---

### Post by dannbunting on 2011-05-07
> **ayates said:**
> You'll need a newer version to run on 11-04(VMware-Player-3.1.4-385536).

getting the same problem with the newer version:

dann@Aries:~$ sudo bash /home/dann/Downloads/VMware-Player-3.1.4-385536.x86_64.bundle
/home/dann/Downloads/VMware-Player-3.1.4-385536.x86_64.bundle: line 110: syntax error near unexpected token `newline'
/home/dann/Downloads/VMware-Player-3.1.4-385536.x86_64.bundle: line 110: `<html>'
dann@Aries:~$ 

any help would be appreciated.:confused:

---

### Post by dannbunting on 2011-05-07
Found the solution!

When I downloaded the file, I used the download manager on the VMWare site. It only downloaded 19.9K. I tried download manually, and it downloaded the entire file 98.9MB It is now installing properly.

:guitar:

---

### Post by Sam Rose on 2011-05-18
> **dannbunting said:**
> Found the solution!

When I downloaded the file, I used the download manager on the VMWare site. It only downloaded 19.9K. I tried download manually, and it downloaded the entire file 98.9MB It is now installing properly.

:guitar:


I can confirm the same thing. Use "manual download" option, then install with

(sudo) sh VMware-Player-3.1.4-385536.x86_64.bundle

---

### Post by JadeMoonlight on 2011-06-04
Psst... Should you mark this a solved?

P.S. I also found this helpful just now.

---

### Post by GlammaGeek on 2011-08-01
Worked for me.  Thanks!

---

