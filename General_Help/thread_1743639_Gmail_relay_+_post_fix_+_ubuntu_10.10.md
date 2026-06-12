---
title: "Gmail relay + post fix + ubuntu 10.10"
date: 2011-04-29
forum: General Help
---

### Post by sobibobi on 2011-04-29
Hi,
I'm stuck and can't move forward,
I have used a lot of information from this forum till now but i can't find something similar to my problem.
I guess i missed something on the way (even that i tried several ways and several times)

My issue is that i'm trying to send emails with postfix and gmail as the mail relay,
i'm trying to send emails to my self by sendmail -bv [email]user@gmail.com[/email]

In the logs, i can understand that it been delivered to the destination, 
taken from: /var/log/mail.log:
Apr 30 00:05:23 moni postfix/pickup[10490]: 9C7552170C: uid=0 from=<root>
Apr 30 00:05:23 moni postfix/cleanup[10495]: 9C7552170C: message-id=<20110429210523.9C7552170C@moni.localdomain>
Apr 30 00:05:23 moni postfix/qmgr[10491]: 9C7552170C: from=<root@moni.localdomain>, size=283, nrcpt=1 (queue active)
Apr 30 00:05:31 moni postfix/smtp[10497]: 9C7552170C: to=<soxxxxxx@gmail.com>, relay=gmail-smtp-in.l.google.com[209.85.227.2$
Apr 30 00:05:32 moni postfix/cleanup[10495]: E00122170D: message-id=<20110429210532.E00122170D@moni.localdomain>
Apr 30 00:05:32 moni postfix/bounce[10499]: 9C7552170C: sender delivery status notification: E00122170D
Apr 30 00:05:32 moni postfix/qmgr[10491]: 9C7552170C: removed
Apr 30 00:05:32 moni postfix/qmgr[10491]: E00122170D: from=<>, size=1891, nrcpt=1 (queue active)
Apr 30 00:05:32 moni postfix/local[10500]: E00122170D: to=<root@moni.localdomain>, relay=local, delay=0.01, delays=0/0/0/0, $
Apr 30 00:05:32 moni postfix/qmgr[10491]: E00122170D: removed


But, the only place i'm getting this email is my local machine,
taken from /val/mail/root:

--2E6622170C.1304110562/moni.localdomain--       

From MAILER-DAEMON  Sat Apr 30 00:05:32 2011            
Return-Path: <>
X-Original-To: [email]root@moni.locald[/email]omain
Delivered-To: [email]root@moni.locald[/email]omain
Received: by moni.localdomain (Postfix)
        id E00122170D; Sat, 30 Apr 2011 00:05:32 +0300 (IDT)  
Date: Sat, 30 Apr 2011 00:05:32 +0300 (IDT)
From: [email]MAILER-DAEMON@moni.locald[/email]omain (Mail Delivery System)
Subject: Mail Delivery Status Report    
To: [email]root@moni.locald[/email]omain           
Auto-Submitted: auto-replied         
MIME-Version: 1.0
Content-Type: multipart/report; report-type=delivery-status;
        boundary="9C7552170C.1304111132/moni.localdomain"
Message-Id: <20110429210532.E00122170D@moni.localdomain>

This is a MIME-encapsulated message.


--9C7552170C.1304111132/moni.localdomain
Content-Description: Notification
Content-Type: text/plain; charset=us-ascii 

This is the mail system at host moni.localdomain.

Enclosed is the mail delivery report that you requested.

                   The mail system  

<soXXXXXX@gmail.com>: delivery via     
    gmail-smtp-in.l.google.com[209.85.227.27]:25: 250 2.1.5 OK
    l8si9043175wbg.36

--9C7552170C.1304111132/moni.localdomain
Content-Description: Delivery report
Content-Type: message/delivery-status

Reporting-MTA: dns; moni.localdomain
X-Postfix-Queue-ID: 9C7552170C
X-Postfix-Sender: rfc822; [email]root@moni.locald[/email]omain         
Arrival-Date: Sat, 30 Apr 2011 00:05:23 +0300 (IDT)

Final-Recipient: rfc822; [email]soXXXXX@gmail.com[/email]
Action: deliverable
Status: 2.1.5
Remote-MTA: dns; gmail-smtp-in.l.google.com
Diagnostic-Code: smtp; 250 2.1.5 OK l8si9043175wbg.36

--9C7552170C.1304111132/moni.localdomain
Content-Description: Message Headers
Content-Type: text/rfc822-headers

Return-Path: <root@moni.localdomain>
Received: by moni.localdomain (Postfix, from userid 0)
        id 9C7552170C; Sat, 30 Apr 2011 00:05:23 +0300 (IDT)  
From: [email]root@moni.locald[/email]omain
Subject: probe
To:     [email]soXXXXXXX@gmail.com[/email]              
Message-Id: <20110429210523.9C7552170C@moni.localdomain>
Date: Sat, 30 Apr 2011 00:05:23 +0300 (IDT)



my postconf -n:
root@moni:~# postconf -n
alias_maps = hash:/etc/aliases
command_directory = /usr/sbin
config_directory = /etc/postfix
daemon_directory = /usr/lib/postfix
data_directory = /var/lib/postfix
debug_peer_level = 3
debug_peer_list = 127.0.0.1
mynetworks = 127.0.0.0/8
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_sasl_tls_security_options = noanonymous
smtp_tls_CAfile = /etc/postfix/cacert.pem
smtp_tls_cert_file = /etc/postfix/FOO-cert.pem
smtp_tls_key_file = /etc/postfix/FOO-key.pem
smtp_tls_session_cache_database = btree:/var/lib/postfix/smtp_tls_session_cache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_mynetworks reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = $myhostname
smtpd_tls_CAfile = /etc/postfix/cacert.pem
smtpd_tls_cert_file = /etc/postfix/FOO-cert.pem
smtpd_tls_key_file = /etc/postfix/FOO-key.pem
smtpd_tls_received_header = yes
smtpd_tls_security_level = encrypt
smtpd_tls_session_cache_database = btree:/var/lib/postfix/smtpd_tls_session_cache
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
unknown_local_recipient_reject_code = 550


When login in my gmail account i can't see nothing under the sent / inbox / spam folder.

it's seems like the mail are been sent.. but nothing is happening.

I hope some will help me, i tried everything i can think about till now :(((((

---

### Post by sobibobi on 2011-04-30
anyone? please? :(

---

