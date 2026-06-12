---
title: "Sending mail from the command line"
date: 2010-01-23
forum: General Help
---

### Post by Neon612 on 2010-01-23
I've been trying to setup a bash script or pythin script that will allow me to backup all the files in a directory. Probably zip, tar (somthing like that) and email them to my Gmail account.

I started with the mail command but I never get a message in the specified gmail account.

I run:
```
mail -s "Subject" user@gmail.com < file.txt
```
but nothing happens. (The text file is the body of the email, right?)


Any help will be appreciated.

---

### Post by Neon612 on 2010-01-23
I've been trying to setup a bash script or pythin script that will allow me to backup all the files in a directory. Probably zip, tar (somthing like that) and email them to my Gmail account.

I started with the mail command but I never get a message in the specified gmail account.

I run:
```
mail -s "Subject" user@gmail.com < file.txt
```
but nothing happens. (The text file is the body of the email, right?)


Any help will be appreciated.

---

### Post by lovinglinux on 2010-01-23
I'm not sure, but I guess to use mail command you need to setup an [MTA](http://en.wikipedia.org/wiki/Mail_transfer_agent).

If you want simplicity, install sendemail and use a command like this:

```
sendEmail -f youremail@foo.com -t youremail@gmail.com -u "My Backup" -m "My backup file" -a file.txt -s smtp.foo.com:25 -xu username -xp password
```

---

### Post by iMisspell on 2010-01-23
I've never used a Bash command or Python, but heres what i use in Perl.

```

#!/usr/bin/perl -w
use strict; use warnings; use diagnostics;

use Mail::Sendmail;


		my %mail = (
				 from => 'me@email.com',
				 to => 'you@email.com',
				 subject => 'Title of email...',
				 'content-type' => 'text/html; charset="iso-8859-1"',
		);
		

$mail{body} = <<END_OF_BODY;
	<html>
	Info..<br>
	More info...
	</html>
END_OF_BODY


		sendmail(%mail) || print "Error: $Mail::Sendmail::error\n";


```

---

### Post by cariboo on 2010-01-23
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by Neon612 on 2010-01-23
lovinglinux: How do I set up the MTA? And when using the sendemail command I keep getting an "Authentication not supported by the remote SMTP server!" error

cariboo: Sorry about the double post, I thought I had deleted the one in General Help before posting the next one.

---

### Post by lovinglinux on 2010-01-23
> **Neon612 said:**
> lovinglinux: How do I set up the MTA?

I have no idea. I tried once without success, that's why I use sendemail :)

> **Neon612 said:**
> And when using the sendemail command I keep getting an "Authentication not supported by the remote SMTP server!" error.

The Authentication error is probably because your e-mail provider uses ssl instead of simple authentication through port 25. You need to install libio-socket-ssl-perl.

See [http://ubuntuforums.org/showthread.php?p=7084234](http://ubuntuforums.org/showthread.php?p=7084234)

---

### Post by dcstar on 2010-01-24
> **lovinglinux said:**
> I'm not sure, but I guess to use mail command you need to setup an [MTA](http://en.wikipedia.org/wiki/Mail_transfer_agent).

If you want simplicity, install sendemail and use a command like this:
.......

Please do not tell people to unnecessarily install packages. Postfix is already installed by default and works fine as an MTA.

Just set it up as an Internet SMTP server with:

```
sudo dpkg-reconfigure postfix
```

The **mailx** package provides a command line mail client that also functions perfectly without any more unnecessary scripting.

If things don't work you simply look at the mail log files using the Log File Viewer.

---

### Post by lovinglinux on 2010-01-24
> **dcstar said:**
> Please do not tell people to unnecessarily install packages. Postfix is already installed by default and works fine as an MTA.

Well, you are entitled to your opinion. IMO, sendemail is pretty easy to use and don't require to run a SMTP server just to send a simple backup message. I don't see a good reason to not use it. Besides, it is on the repositories and not available on some untrusted web site.

Perhaps you should consider that what works well for you might not be the best option for others.

---

### Post by dcstar on 2010-01-24
> **lovinglinux said:**
> Well, you are entitled to your opinion. IMO, sendemail is pretty easy to use and don't require to run a SMTP server just to send a simple backup message. I don't see a good reason to not use it. Besides, it is on the repositories and not available on some untrusted web site.

Perhaps you should consider that what works well for you might not be the best option for others.

Postfix is a Sendmail replacement **specifically** installed in the Ubuntu distro as the default MTA for very good reasons, so take up your argument with the Ubuntu developers before **you** tell someone to use something different.

Sendmail **is** a SMTP server, so if you don't really understand that then perhaps you should refrain from offering advice on the subject?

---

### Post by lovinglinux on 2010-01-24
> **dcstar said:**
> Postfix is a Sendmail replacement **specifically** installed in the Ubuntu distro as the default MTA for very good reasons, so take up your argument with the Ubuntu developers before **you** tell someone to use something different.

Sendmail **is** a SMTP server, so if you don't really understand that then perhaps you should refrain from offering advice on the subject?

I know Postfix is a Sendmail replacement and that Sendmail **is** an SMTP server but it is **NOT** the same as [send**E**mail](http://caspian.dotconf.net/menu/Software/SendEmail/).

> SendEmail is a lightweight, command line SMTP email client. If you have the need to send email from a command line, this free program is perfect: simple to use and feature rich. It was designed to be used in bash scripts, batch files, Perl programs and web sites, but is quite adaptable and will likely meet your requirements. SendEmail is written in Perl and is unique in that it requires NO MODULES. It has an intuitive and flexible set of command-line options, making it very easy to learn and use.

So perhaps **you** should **read my posts carefully**, before being impolite with someone who is just trying to offer a simpler solution to another user.

---

### Post by steve_dupuis on 2010-01-31
> **dcstar said:**
> Please do not tell people to unnecessarily install packages. Postfix is already installed by default and works fine as an MTA.

Just set it up as an Internet SMTP server with:

```
sudo dpkg-reconfigure postfix
```The **mailx** package provides a command line mail client that also functions perfectly without any more unnecessary scripting.

If things don't work you simply look at the mail log files using the Log File Viewer.

=========================================================
I don't wish to run an email server on one of my workstations. That's what postfix ends up doing. Its a very large and complex package. (I've been working with sendmail and similar software since 1979 and know how they work. sendEmail is not the same thing at all.)

I only want to send email via my ISP's SMTP gateway. The sendEmail utility is all I need when modifying shell scripts or other program code. It also allows sending attachments.

---

### Post by lovinglinux on 2010-01-31
> **steve_dupuis said:**
> I don't wish to run an email server on one of my workstations. That's what postfix ends up doing. Its a very large and complex package. (I've been working with sendmail and similar software since 1979 and know how they work. sendEmail is not the same thing at all.)

I only want to send email via my ISP's SMTP gateway. The sendEmail utility is all I need when modifying shell scripts or other program code. It also allows sending attachments.

Exactly.

---

### Post by Neon612 on 2010-02-02
Thanks for all the great help guys. But I just got a weird error message the last time I tried running this command:

```
ERROR => Connection attempt to smtp.gmail.com:25 failed: IO:Sodket::INET: connect: Connection refused
```

I had a script set up to email myself a set of files for backup daily. When I moved the script over to another comp and ran it, it still worked fine. That is until I took the other comp to school with me and logged onto their Wireless network. Thats when I got the above error.

A litle help will go a long way. Thank you.

---

### Post by lovinglinux on 2010-02-02
> **Neon612 said:**
> Thanks for all the great help guys. But I just got a weird error message the last time I tried running this command:

```
ERROR => Connection attempt to smtp.gmail.com:25 failed: IO:Sodket::INET: connect: Connection refused
```

I had a script set up to email myself a set of files for backup daily. When I moved the script over to another comp and ran it, it still worked fine. That is until I took the other comp to school with me and logged onto their Wireless network. Thats when I got the above error.

A litle help will go a long way. Thank you.

Your school is probably blocking connections on port 25. Try using port 465.

---

### Post by Neon612 on 2010-02-12
Thanks for the help but that port didn't seem to fix it. I tried a couple different ones, but still nothing. The school does have a list of available ports:

```
none - ICMP/Ping/Traceroute
none - GRE
20/21 &#8211; ftp
22 - secure login (SSH)
23 - telnet
37 - time (NTP)
53 - Domain Name Service (DNS) TCP/UDP
69 - Trivial File Transfer Protocol (TFTP)
80 - web (HTTP)
109 - POP2 email download, older
110 - POP3 email download
143 - IMAP
194 - Internet Relay Chat (IRC)
322 - Real Media
402 &#8211; Altiris Client
407 &#8211; Timbuktu
443 - secure web (HTTPS)
515 - Line Printer remote printing (LPD)
545 - Quicktime
548 - AppleTalk File Access
554 - Real Time Streaming Protocol (RTSP)
587 - SMTP Submission
591 - Filemaker
993 - S-IMAP
995 - S-POP
1352 - Lotus Notes client
1521 - Oracle Client at PKI
1533 &#8211; Lotus Notes Sametime Client
1723 - Point to Point Tunneling Protocol (PPTP) TCP/UDP
1755 - Windows Media
1863 - Microsoft MSNP
2000 - MBSC Bookstore Scanners
3219 - MSN Instant Messenger
3283 - TCP/UDP
3389 - Microsoft terminal services
4000 - ICQ
5050 - Yahoo Messenger
5190 - AOL Instant Messenger (AIM)
5222 - Jabber Messenging Server
5900 - TCP/UDP
6891-6900 - MSN Extras
6970-6999 - Quick Time 4 (Tcp/Udp)
8010 - myBlackboard Virtual Classroom (137.48.1.X only)
8011 - myBlackboard Virtual Classroom (137.48.1.X only)
8080 - web testing (HTTP)
8090 - web testing (HTTP)
8443 - web testing (HTTPS)
8444 - web testing (HTTPS)
9100 - remote printing (pdl datastream)
10000 - UNMC VPN
16384-16403 &#8211; Applec iChat
28203 &#8211; MavCard Wireless Printing
xxxx - Multiple ports to VPN system at CSN
```

---

### Post by lovinglinux on 2010-02-12
Try port 587. Who knows, it might work.

---

### Post by Neon612 on 2010-02-15
Thank you, it worked perfectly.

---

