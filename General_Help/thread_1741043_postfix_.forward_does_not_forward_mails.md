---
title: "postfix .forward does not forward mails"
date: 2011-04-27
forum: General Help
---

### Post by sgoetz on 2011-04-27
Dear All. 
I set up postfix and everything is working. I can receive mails, send mails, I can use imap and pop. All just fine. 
The only problem i have is that when trying to use .forward file in /home/user/ with an external email (e.g. [email]me@gmail.com[/email]) this mail seems to get forwarded correcly but never reaches :-((. (btw I tried allready with several mail accounts/addresses - no luck). 

Even /var/log/mail.log look just fine with: 

Apr 27 23:34:42 vs postfix/local[9588]: 89DA397E01AA: to=<me@mydomain.com>, relay=local, delay=0.24, delays=0.2/0.01/0/0.03, dsn=2.0.0, status=sent (forwarded as B571297E01AB)
Apr 27 23:34:42 vs postfix/qmgr[24327]: 89DA397E01AA: removed
Apr 27 23:34:43 vs postfix/smtp[9589]: B571297E01AB: to=<me@gmail.com>, orig_to=<me@mydomain.com>, relay=**********.com[***.***.***.***]:25, delay=0.57, delays=0.03/0.01/0.36/0.17, dsn=2.0.0, status=sent (250 ok:  Message 204931658 accepted)
Apr 27 23:34:43 vs postfix/qmgr[24327]: B571297E01AB: removed


So how can I get a "status=sent", "250 ok" and a "Message  accepted" but with no mail at the other side? As I said already if i use "mail" from the command line everything works fine. And if i do not use forward I have the email in my mail folder -also ok. 

Just the stupid .forward thing does not work but without any error message!
Your help is so appreciated since I'm realy running out of ideas on this.
Thanks. 
Stef.

---

### Post by Doug S on 2011-04-27
I don't think I will be much help, but am replying anyhow.
I had not tried a .forward file yet, on my new server. I just had not got around to it.
So I tried it when I saw your posting. It worked fine. My postfix installation is completely default. I did notice my forward line in mail.log was just a little different than yours (but maybe that is just MTA specific stuff):
>  
Apr 27 15:38:24 doug-64 postfix/local[14723]: 2D894DC097E: to=<me@myserver.com>, relay=local, delay=0.21, delays=0.16/0.01/0/0.04, dsn=2.0.0, status=sent (forwarded as 46983DC0B35)
Apr 27 15:38:24 doug-64 postfix/qmgr[1057]: 2D894DC097E: removed
Apr 27 15:38:27 doug-64 postfix/smtp[14724]: 46983DC0B35: to=<me@my_isp_account.net>, orig_to=<me@myserver.com>, relay=my_isp_MTA.net[xxx.xxx.xxx.xxx]:25, delay=3.1, delays=0.04/0.03/0.15/2.9, dsn=2.0.0, status=sent (250 2.0.0 cmez1g02248hjER01mf0Np **mail accepted for delivery**)
Apr 27 15:38:27 doug-64 postfix/qmgr[1057]: 46983DC0B35: removed


---

### Post by sgoetz on 2011-04-29
Thanks for this!
I searched for a hint on why I get this differences but no luck. 
So my problem is still unsolved.
Any further comments and ideas are most appreciated.
S.

---

### Post by sgoetz on 2011-04-29
Here is what I get in the log file. 
Can anyone see anything unusual???
Thanks again.
S.


Apr 29 13:16:19 myhost postfix/smtpd[32240]: connection established
Apr 29 13:16:19 myhost postfix/smtpd[32240]: master_notify: status 0
Apr 29 13:16:19 myhost postfix/smtpd[32240]: name_mask: resource
Apr 29 13:16:19 myhost postfix/smtpd[32240]: name_mask: software
Apr 29 13:16:19 myhost postfix/smtpd[32240]: connect from mail-bw0-f51.google.com[209.85.214.51]
Apr 29 13:16:19 myhost postfix/smtpd[32240]: match_list_match: mail-bw0-f51.google.com: no match
Apr 29 13:16:19 myhost postfix/smtpd[32240]: match_list_match: 209.85.214.51: no match
Apr 29 13:16:19 myhost postfix/smtpd[32240]: match_list_match: mail-bw0-f51.google.com: no match
Apr 29 13:16:19 myhost postfix/smtpd[32240]: match_list_match: 209.85.214.51: no match
Apr 29 13:16:19 myhost postfix/smtpd[32240]: match_hostname: mail-bw0-f51.google.com ~? 127.0.0.0/8
Apr 29 13:16:19 myhost postfix/smtpd[32240]: match_hostaddr: 209.85.214.51 ~? 127.0.0.0/8
Apr 29 13:16:19 myhost postfix/smtpd[32240]: match_hostname: mail-bw0-f51.google.com ~? 62.75.158.5/32
Apr 29 13:16:19 myhost postfix/smtpd[32240]: match_hostaddr: 209.85.214.51 ~? 62.75.158.5/32
Apr 29 13:16:19 myhost postfix/smtpd[32240]: match_list_match: mail-bw0-f51.google.com: no match
Apr 29 13:16:19 myhost postfix/smtpd[32240]: match_list_match: 209.85.214.51: no match
Apr 29 13:16:19 myhost postfix/smtpd[32240]: send attr request = connect
Apr 29 13:16:19 myhost postfix/smtpd[32240]: send attr ident = smtp:209.85.214.51
Apr 29 13:16:19 myhost postfix/smtpd[32240]: private/anvil: wanted attribute: status
Apr 29 13:16:19 myhost postfix/smtpd[32240]: input attribute name: status
Apr 29 13:16:19 myhost postfix/smtpd[32240]: input attribute value: 0
Apr 29 13:16:19 myhost postfix/smtpd[32240]: private/anvil: wanted attribute: count
Apr 29 13:16:19 myhost postfix/smtpd[32240]: input attribute name: count
Apr 29 13:16:19 myhost postfix/smtpd[32240]: input attribute value: 1
Apr 29 13:16:19 myhost postfix/smtpd[32240]: private/anvil: wanted attribute: rate
Apr 29 13:16:19 myhost postfix/smtpd[32240]: input attribute name: rate
Apr 29 13:16:19 myhost postfix/smtpd[32240]: input attribute value: 2
Apr 29 13:16:19 myhost postfix/smtpd[32240]: private/anvil: wanted attribute: (list terminator)
Apr 29 13:16:19 myhost postfix/smtpd[32240]: input attribute name: (end)
Apr 29 13:16:19 myhost postfix/smtpd[32240]: > mail-bw0-f51.google.com[209.85.214.51]: 220 mydomain.com ESMTP Postfix (Debian/GNU)
Apr 29 13:16:19 myhost postfix/smtpd[32240]: < mail-bw0-f51.google.com[209.85.214.51]: EHLO mail-bw0-f51.google.com
Apr 29 13:16:19 myhost postfix/smtpd[32240]: > mail-bw0-f51.google.com[209.85.214.51]: 250-mydomain.com
Apr 29 13:16:19 myhost postfix/smtpd[32240]: > mail-bw0-f51.google.com[209.85.214.51]: 250-PIPELINING
Apr 29 13:16:19 myhost postfix/smtpd[32240]: > mail-bw0-f51.google.com[209.85.214.51]: 250-SIZE 10240000
Apr 29 13:16:19 myhost postfix/smtpd[32240]: > mail-bw0-f51.google.com[209.85.214.51]: 250-VRFY
Apr 29 13:16:19 myhost postfix/smtpd[32240]: > mail-bw0-f51.google.com[209.85.214.51]: 250-ETRN
Apr 29 13:16:19 myhost postfix/smtpd[32240]: match_list_match: mail-bw0-f51.google.com: no match
Apr 29 13:16:19 myhost postfix/smtpd[32240]: match_list_match: 209.85.214.51: no match
Apr 29 13:16:19 myhost postfix/smtpd[32240]: > mail-bw0-f51.google.com[209.85.214.51]: 250-STARTTLS
Apr 29 13:16:19 myhost postfix/smtpd[32240]: > mail-bw0-f51.google.com[209.85.214.51]: 250-ENHANCEDSTATUSCODES
Apr 29 13:16:19 myhost postfix/smtpd[32240]: > mail-bw0-f51.google.com[209.85.214.51]: 250-8BITMIME
Apr 29 13:16:19 myhost postfix/smtpd[32240]: > mail-bw0-f51.google.com[209.85.214.51]: 250 DSN
Apr 29 13:16:19 myhost postfix/smtpd[32240]: < mail-bw0-f51.google.com[209.85.214.51]: STARTTLS
Apr 29 13:16:19 myhost postfix/smtpd[32240]: > mail-bw0-f51.google.com[209.85.214.51]: 220 2.0.0 Ready to start TLS
Apr 29 13:16:19 myhost postfix/smtpd[32240]: auto_clnt_open: connected to private/tlsmgr
Apr 29 13:16:19 myhost postfix/smtpd[32240]: send attr request = seed
Apr 29 13:16:19 myhost postfix/smtpd[32240]: send attr size = 32
Apr 29 13:16:19 myhost postfix/smtpd[32240]: private/tlsmgr: wanted attribute: status
Apr 29 13:16:19 myhost postfix/smtpd[32240]: input attribute name: status
Apr 29 13:16:19 myhost postfix/smtpd[32240]: input attribute value: 0
Apr 29 13:16:19 myhost postfix/smtpd[32240]: private/tlsmgr: wanted attribute: seed
Apr 29 13:16:19 myhost postfix/smtpd[32240]: input attribute name: seed
Apr 29 13:16:19 myhost postfix/smtpd[32240]: input attribute value: gYVWAgT6EYEZC5fL4sxNxzvr7F1RNYMzwwQNvM6CnQs=
Apr 29 13:16:19 myhost postfix/smtpd[32240]: private/tlsmgr: wanted attribute: (list terminator)
Apr 29 13:16:19 myhost postfix/smtpd[32240]: input attribute name: (end)
Apr 29 13:16:19 myhost postfix/smtpd[32240]: send attr request = update
Apr 29 13:16:19 myhost postfix/smtpd[32240]: send attr cache_type = smtpd
Apr 29 13:16:19 myhost postfix/smtpd[32240]: send attr cache_id = BAA108FAF07DEF9339BFCA57281ED786258A564719A86ED1DEB1EE0283E60DF5&s=smtp
Apr 29 13:16:19 myhost postfix/smtpd[32240]: send attr session = [data 127 bytes]
Apr 29 13:16:19 myhost postfix/smtpd[32240]: private/tlsmgr: wanted attribute: status
Apr 29 13:16:19 myhost postfix/smtpd[32240]: input attribute name: status
Apr 29 13:16:19 myhost postfix/smtpd[32240]: input attribute value: 0
Apr 29 13:16:19 myhost postfix/smtpd[32240]: private/tlsmgr: wanted attribute: (list terminator)
Apr 29 13:16:19 myhost postfix/smtpd[32240]: input attribute name: (end)
Apr 29 13:16:19 myhost postfix/smtpd[32240]: < mail-bw0-f51.google.com[209.85.214.51]: EHLO mail-bw0-f51.google.com
Apr 29 13:16:19 myhost postfix/smtpd[32240]: > mail-bw0-f51.google.com[209.85.214.51]: 250-mydomain.com
Apr 29 13:16:19 myhost postfix/smtpd[32240]: > mail-bw0-f51.google.com[209.85.214.51]: 250-PIPELINING
Apr 29 13:16:19 myhost postfix/smtpd[32240]: > mail-bw0-f51.google.com[209.85.214.51]: 250-SIZE 10240000
Apr 29 13:16:19 myhost postfix/smtpd[32240]: > mail-bw0-f51.google.com[209.85.214.51]: 250-VRFY
Apr 29 13:16:19 myhost postfix/smtpd[32240]: match_list_match: mail-bw0-f51.google.com: no match
Apr 29 13:16:19 myhost postfix/smtpd[32240]: match_list_match: 209.85.214.51: no match
Apr 29 13:16:19 myhost postfix/smtpd[32240]: > mail-bw0-f51.google.com[209.85.214.51]: 250-ETRN
Apr 29 13:16:19 myhost postfix/smtpd[32240]: > mail-bw0-f51.google.com[209.85.214.51]: 250-ENHANCEDSTATUSCODES
Apr 29 13:16:19 myhost postfix/smtpd[32240]: > mail-bw0-f51.google.com[209.85.214.51]: 250-8BITMIME
Apr 29 13:16:19 myhost postfix/smtpd[32240]: > mail-bw0-f51.google.com[209.85.214.51]: 250 DSN
Apr 29 13:16:19 myhost postfix/smtpd[32240]: < mail-bw0-f51.google.com[209.85.214.51]: MAIL FROM:<myname@gmail.com>
Apr 29 13:16:19 myhost postfix/smtpd[32240]: extract_addr: input: <myname@gmail.com>
Apr 29 13:16:19 myhost postfix/smtpd[32240]: smtpd_check_addr: addr=myname@gmail.com
Apr 29 13:16:19 myhost postfix/smtpd[32240]: ctable_locate: move existing entry key [email]myname@gmail.com[/email]
Apr 29 13:16:19 myhost postfix/smtpd[32240]: extract_addr: in: <myname@gmail.com>, result: [email]myname@gmail.com[/email]
Apr 29 13:16:19 myhost postfix/smtpd[32240]: fsspace: .: block size 4096, blocks free 4252002
Apr 29 13:16:19 myhost postfix/smtpd[32240]: smtpd_check_queue: blocks 4096 avail 4252002 min_free 0 msg_size_limit 10240000
Apr 29 13:16:19 myhost postfix/smtpd[32240]: > mail-bw0-f51.google.com[209.85.214.51]: 250 2.1.0 Ok
Apr 29 13:16:19 myhost postfix/smtpd[32240]: < mail-bw0-f51.google.com[209.85.214.51]: RCPT TO:<support@mydomain.com>
Apr 29 13:16:19 myhost postfix/smtpd[32240]: extract_addr: input: <support@mydomain.com>
Apr 29 13:16:19 myhost postfix/smtpd[32240]: smtpd_check_addr: addr=support@mydomain.com
Apr 29 13:16:19 myhost postfix/smtpd[32240]: ctable_locate: move existing entry key [email]support@mydomain.com[/email]
Apr 29 13:16:19 myhost postfix/smtpd[32240]: extract_addr: in: <support@mydomain.com>, result: [email]support@mydomain.com[/email]
Apr 29 13:16:19 myhost postfix/smtpd[32240]: >>> START Recipient address RESTRICTIONS <<<
Apr 29 13:16:19 myhost postfix/smtpd[32240]: generic_checks: name=permit_mynetworks
Apr 29 13:16:19 myhost postfix/smtpd[32240]: permit_mynetworks: mail-bw0-f51.google.com 209.85.214.51
Apr 29 13:16:19 myhost postfix/smtpd[32240]: match_hostname: mail-bw0-f51.google.com ~? 127.0.0.0/8
Apr 29 13:16:19 myhost postfix/smtpd[32240]: match_hostaddr: 209.85.214.51 ~? 127.0.0.0/8
Apr 29 13:16:19 myhost postfix/smtpd[32240]: match_hostname: mail-bw0-f51.google.com ~? 62.75.158.5/32
Apr 29 13:16:19 myhost postfix/smtpd[32240]: match_hostaddr: 209.85.214.51 ~? 62.75.158.5/32
Apr 29 13:16:19 myhost postfix/smtpd[32240]: match_list_match: mail-bw0-f51.google.com: no match
Apr 29 13:16:19 myhost postfix/smtpd[32240]: match_list_match: 209.85.214.51: no match
Apr 29 13:16:19 myhost postfix/smtpd[32240]: generic_checks: name=permit_mynetworks status=0
Apr 29 13:16:19 myhost postfix/smtpd[32240]: generic_checks: name=reject_unauth_destination
Apr 29 13:16:19 myhost postfix/smtpd[32240]: reject_unauth_destination: [email]support@mydomain.com[/email]
Apr 29 13:16:19 myhost postfix/smtpd[32240]: permit_auth_destination: [email]support@mydomain.com[/email]
Apr 29 13:16:19 myhost postfix/smtpd[32240]: ctable_locate: leave existing entry key [email]support@mydomain.com[/email]
Apr 29 13:16:19 myhost postfix/smtpd[32240]: generic_checks: name=reject_unauth_destination status=0
Apr 29 13:16:19 myhost postfix/smtpd[32240]: >>> END Recipient address RESTRICTIONS <<<
Apr 29 13:16:19 myhost postfix/smtpd[32240]: >>> CHECKING RECIPIENT MAPS <<<
Apr 29 13:16:19 myhost postfix/smtpd[32240]: ctable_locate: leave existing entry key [email]support@mydomain.com[/email]
Apr 29 13:16:19 myhost postfix/smtpd[32240]: maps_find: recipient_canonical_maps: [email]support@mydomain.com[/email]: not found
Apr 29 13:16:19 myhost postfix/smtpd[32240]: maps_find: recipient_canonical_maps: support: not found
Apr 29 13:16:19 myhost postfix/smtpd[32240]: maps_find: recipient_canonical_maps: @mydomain.com: not found
Apr 29 13:16:19 myhost postfix/smtpd[32240]: mail_addr_find: [email]support@mydomain.com[/email] -> (not found)
Apr 29 13:16:19 myhost postfix/smtpd[32240]: maps_find: canonical_maps: [email]support@mydomain.com[/email]: not found
Apr 29 13:16:19 myhost postfix/smtpd[32240]: maps_find: canonical_maps: support: not found
Apr 29 13:16:19 myhost postfix/smtpd[32240]: maps_find: canonical_maps: @mydomain.com: not found
Apr 29 13:16:19 myhost postfix/smtpd[32240]: mail_addr_find: [email]support@mydomain.com[/email] -> (not found)
Apr 29 13:16:19 myhost postfix/smtpd[32240]: maps_find: virtual_alias_maps: [email]support@mydomain.com[/email]: not found
Apr 29 13:16:19 myhost postfix/smtpd[32240]: maps_find: virtual_alias_maps: hash:/etc/postfix/virtual(0,lock|fold_fix): support = [email]myname@gmail.com[/email]
Apr 29 13:16:19 myhost postfix/smtpd[32240]: mail_addr_find: [email]support@mydomain.com[/email] -> [email]myname@gmail.com[/email]
Apr 29 13:16:19 myhost postfix/smtpd[32240]: smtpd_check_rewrite: trying: permit_inet_interfaces
Apr 29 13:16:19 myhost postfix/smtpd[32240]: permit_inet_interfaces: mail-bw0-f51.google.com 209.85.214.51
Apr 29 13:16:19 myhost postfix/smtpd[32240]: before input_transp_cleanup: cleanup flags = enable_header_body_filter enable_automatic_bcc enable_address_mapping enable_milters
Apr 29 13:16:19 myhost postfix/smtpd[32240]: after input_transp_cleanup: cleanup flags = enable_header_body_filter enable_automatic_bcc enable_address_mapping
Apr 29 13:16:19 myhost postfix/smtpd[32240]: connect to subsystem public/cleanup
Apr 29 13:16:19 myhost postfix/smtpd[32240]: public/cleanup socket: wanted attribute: queue_id
Apr 29 13:16:19 myhost postfix/smtpd[32240]: input attribute name: queue_id
Apr 29 13:16:19 myhost postfix/smtpd[32240]: input attribute value: 7C6B697E07F1
Apr 29 13:16:19 myhost postfix/smtpd[32240]: public/cleanup socket: wanted attribute: (list terminator)
Apr 29 13:16:19 myhost postfix/smtpd[32240]: input attribute name: (end)
Apr 29 13:16:19 myhost postfix/smtpd[32240]: send attr flags = 178
Apr 29 13:16:19 myhost postfix/smtpd[32240]: 7C6B697E07F1: client=mail-bw0-f51.google.com[209.85.214.51]
Apr 29 13:16:19 myhost postfix/smtpd[32240]: > mail-bw0-f51.google.com[209.85.214.51]: 250 2.1.5 Ok
Apr 29 13:16:19 myhost postfix/smtpd[32240]: < mail-bw0-f51.google.com[209.85.214.51]: DATA
Apr 29 13:16:19 myhost postfix/smtpd[32240]: > mail-bw0-f51.google.com[209.85.214.51]: 354 End data with <CR><LF>.<CR><LF>
Apr 29 13:16:19 myhost postfix/cleanup[32290]: 7C6B697E07F1: message-id=<BANLkTi=GrwrfWNYi=qz4HJ761siS8CuJpQ@mail.gmail.com>
Apr 29 13:16:19 myhost postfix/smtpd[32240]: public/cleanup socket: wanted attribute: status
Apr 29 13:16:19 myhost postfix/smtpd[32240]: input attribute name: status
Apr 29 13:16:19 myhost postfix/smtpd[32240]: input attribute value: 0
Apr 29 13:16:19 myhost postfix/smtpd[32240]: public/cleanup socket: wanted attribute: reason
Apr 29 13:16:19 myhost postfix/smtpd[32240]: input attribute name: reason
Apr 29 13:16:19 myhost postfix/smtpd[32240]: input attribute value: (end)
Apr 29 13:16:19 myhost postfix/smtpd[32240]: public/cleanup socket: wanted attribute: (list terminator)
Apr 29 13:16:19 myhost postfix/smtpd[32240]: input attribute name: (end)
Apr 29 13:16:19 myhost postfix/smtpd[32240]: > mail-bw0-f51.google.com[209.85.214.51]: 250 2.0.0 Ok: queued as 7C6B697E07F1
Apr 29 13:16:19 myhost postfix/qmgr[30391]: 7C6B697E07F1: from=<myname@gmail.com>, size=2210, nrcpt=1 (queue active)
Apr 29 13:16:20 myhost postfix/smtp[32306]: 7C6B697E07F1: to=<myname@gmail.com>, orig_to=<support@mydomain.com>, relay=gmail-smtp-in.l.google.com[74.125.79.27]:25, delay=0.52, delays=0.19/0/0.13/0.21, dsn=2.0.0, status=sent (250 2.0.0 OK 1304075779 y9si9561810eeh.80)
Apr 29 13:16:20 myhost postfix/qmgr[30391]: 7C6B697E07F1: removed

---

### Post by sgoetz on 2011-04-29
Ok, I'm really sorry about this, especially for all the time I lost myself.
The problem here was that the mails were send without problem but the webmail i'am using (gmail) was putting all emails with the "orig_to=" pointing to a different email than the official gmail one in a special imap folder and not the regular inbox as I expected. It took me really long (too long) to find this stupid thing out.
So sorry for bothering and I really hope somebody will find this post useful in the future.
Cheers, 
S.

---

### Post by Doug S on 2011-04-29
Glad you got it sorted out. And thanks for reporting back. As for myself, I had been to test .forward anyhow...

---

