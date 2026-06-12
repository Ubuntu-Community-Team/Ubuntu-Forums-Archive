---
title: "Linux to Win7 network password problem"
date: 2010-08-29
forum: General Help
---

### Post by iamsickofschool on 2010-08-29
I am trying to share files between my Win 7 machine and Linux. I already  did all the stuff needed with Samba. My problem is that when I try to  connect Linux to Win7 it asks for a password. I put in my account name  and password for Win7 but it keeps saying its wrong. I then disabled  password protection on Win7... still didnt work. Then I disabled  Homegroup... Still didnt work. Any ideas?

 Sorry if this has been posted but i just cant seem to find it!!!

I posted this on networking forum but I got no replies/answers.

---

### Post by cburner on 2010-08-29
Are the username and password the same on both machines?

If not, on Windows 7 machine trying to access samba share you need to use the samba username and password.

---

### Post by iamsickofschool on 2010-08-29
i used the samba account name and password too and it re-asks after a few seconds.

---

### Post by Morbius1 on 2010-08-29
You by any chance have Windows Live Sign-in Assistant installed on Win7.

You might want to remote that: [http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527)

---

### Post by iamsickofschool on 2010-08-29
ill try that and get back to you thx

---

### Post by Wacky Dan on 2010-12-14
Just a quick update, I had Windows Live Essentials 2011 installed on my Windows 7 box, I uninstalled Windows Live Sign-in Assistant but SMB was still broken. In an act of desperation I uninstalled the whole Windows Live Essentials 2011 suite, this resolved the issue :P. And thanks again to the Morbius1 for the link I was convinced that upgrading to 10.10 had broken my shares.

---

### Post by Magzime on 2010-12-19
> **Morbius1 said:**
> You by any chance have Windows Live Sign-in Assistant installed on Win7.

You might want to remote that: [http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527)
Ooohhh I've been trying stuff for almost an hour, and then found your solution. I KNEW the problem was the Windows box, not the wonderful and lovely Ubuntu PC! Thanks and here's a beer! ;)

---

### Post by snakerdlk on 2010-12-23
does not work all the time.

with cifs it works, the problem is smbfs. Unfortunately.
(actually with windows...)

---

