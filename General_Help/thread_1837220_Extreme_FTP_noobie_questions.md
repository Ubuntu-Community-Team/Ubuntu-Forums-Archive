---
title: "Extreme FTP noobie questions"
date: 2011-09-01
forum: General Help
---

### Post by mpones on 2011-09-01
I recently set up our first Linux box (go me).

I need to configure an FTP server on the linux box, so that a few other machines can periodically connect and backup pertinent financial data.  

I am basically BRAND new to ubuntu, and I spent all night last night researching and googling for a decent walk through that I understand, until I fell face first onto my desk asleep at 2:30am.

I understand the basic concept of sudo (root admin) and apt-get (simple command for getting packages), as well as install command.  I am still learning the file system hierarchy.

Where I get lost is finding out how to allocate very specific areas for FTP users, as well as simply access the FTP site from the outside once it is allegedly running.

I'm using Ubuntu desktop 11.04, I have a static IP, as well as a domain name (with the A record set to the static IP), as well as a router that is successfully forwarding as a DMZ host to the UBU box.

I've tried vsftpd, and proftpd, and I'm sure with both, I did something wrong.  I just need help getting a secure login w/ password, and the ability to access it from elsewhere.

Thanks in advance!

---

### Post by haqking on 2011-09-01
> **mpones said:**
> I recently set up our first Linux box (go me).

I need to configure an FTP server on the linux box, so that a few other machines can periodically connect and backup pertinent financial data.  

I am basically BRAND new to ubuntu, and I spent all night last night researching and googling for a decent walk through that I understand, until I fell face first onto my desk asleep at 2:30am.

I understand the basic concept of sudo (root admin) and apt-get (simple command for getting packages), as well as install command.  I am still learning the file system hierarchy.

Where I get lost is finding out how to allocate very specific areas for FTP users, as well as simply access the FTP site from the outside once it is allegedly running.

I'm using Ubuntu desktop 11.04, I have a static IP, as well as a domain name (with the A record set to the static IP), as well as a router that is successfully forwarding as a DMZ host to the UBU box.

I've tried vsftpd, and proftpd, and I'm sure with both, I did something wrong.  I just need help getting a secure login w/ password, and the ability to access it from elsewhere.

Thanks in advance!


see here for a good guide [http://www.jonathanmoeller.com/screed/?p=2981](http://www.jonathanmoeller.com/screed/?p=2981)

or here [http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html](http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html)

---

### Post by mpones on 2011-09-01
> **haqking said:**
> see here for a good guide [http://www.jonathanmoeller.com/screed/?p=2981](http://www.jonathanmoeller.com/screed/?p=2981)

or here [http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html](http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html)

I tried the first guide, but after saving the conf file (I went with sudo gedit /etc/vsftpd.conf instead), I tried restarting the service, and I got "unknown instance:"  I figured the service wasn't running, so I typed "sudo service vsftpd start", it looked like it started, and when I typed "ftp 127.0.0.1" to test it, it said "ftp: connect: connection refused", but it still comes back with "ftp>" afterwards...

I read the comments on that link you gave me, no one seemed to have the same issues...

---

### Post by haqking on 2011-09-01
> **mpones said:**
> I tried the first guide, but after saving the conf file (I went with sudo gedit /etc/vsftpd.conf instead), I tried restarting the service, and I got "unknown instance:"  I figured the service wasn't running, so I typed "sudo service vsftpd start", it looked like it started, and when I typed "ftp 127.0.0.1" to test it, it said "ftp: connect: connection refused"

I read the comments on that link you gave me, no one seemed to have the same issues...

mmm well first thing is, when using gedit as it is a graphical app then use gksudo not sudo.

If you dont it can often result in various issues.

so when you say it looked like it started was it or not ? did you check to see ?

---

### Post by mpones on 2011-09-01
> **haqking said:**
> mmm well first thing is, when using gedit as it is a graphical app then use gksudo not sudo.

If you dont it can often result in various issues.

so when you say it looked like it started was it or not ? did you check to see ?
"vsftpd start/pre-start, process 1711"

That is what made me think it started...

---

