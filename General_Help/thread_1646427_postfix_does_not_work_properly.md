---
title: "postfix does not work properly"
date: 2010-12-15
forum: General Help
---

### Post by fnever on 2010-12-15
Hi everyone, forgive my english.
I have spent 3 days search over internet to solve this problem

 I am installing postfix2.7 on ubuntu Ubuntu 10.04 LTS

```
Dec 16 01:52:30 localhost postfix/smtpd[4186]: < mail-iw0-f181.google.com[209.85.214.181]: EHLO mail-iw0-f181.google.com
Dec 16 01:52:30 localhost postfix/smtpd[4186]: > mail-iw0-f181.google.com[209.85.214.181]: 250-li222-96.members.linode.com
Dec 16 01:52:30 localhost postfix/smtpd[4186]: > mail-iw0-f181.google.com[209.85.214.181]: 250-PIPELINING
Dec 16 01:52:30 localhost postfix/smtpd[4186]: > mail-iw0-f181.google.com[209.85.214.181]: 250-SIZE 10240000
Dec 16 01:52:30 localhost postfix/smtpd[4186]: > mail-iw0-f181.google.com[209.85.214.181]: 250-VRFY
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_list_match: mail-iw0-f181.google.com: no match
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_list_match: 209.85.214.181: no match
Dec 16 01:52:30 localhost postfix/smtpd[4186]: > mail-iw0-f181.google.com[209.85.214.181]: 250-ETRN
Dec 16 01:52:30 localhost postfix/smtpd[4186]: > mail-iw0-f181.google.com[209.85.214.181]: 250-ENHANCEDSTATUSCODES
Dec 16 01:52:30 localhost postfix/smtpd[4186]: > mail-iw0-f181.google.com[209.85.214.181]: 250-8BITMIME
Dec 16 01:52:30 localhost postfix/smtpd[4186]: > mail-iw0-f181.google.com[209.85.214.181]: 250 DSN
Dec 16 01:52:30 localhost postfix/smtpd[4186]: < mail-iw0-f181.google.com[209.85.214.181]: MAIL FROM:<th8china@gmail.com>
Dec 16 01:52:30 localhost postfix/smtpd[4186]: extract_addr: input: <th8china@gmail.com>
Dec 16 01:52:30 localhost postfix/smtpd[4186]: smtpd_check_addr: addr=th8china@gmail.com
Dec 16 01:52:30 localhost postfix/smtpd[4186]: connect to subsystem private/rewrite
Dec 16 01:52:30 localhost postfix/smtpd[4186]: send attr request = rewrite
Dec 16 01:52:30 localhost postfix/smtpd[4186]: send attr rule = local
Dec 16 01:52:30 localhost postfix/smtpd[4186]: send attr address = th8china@gmail.com
Dec 16 01:52:30 localhost postfix/smtpd[4186]: private/rewrite socket: wanted attribute: flags
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: flags
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute value: 0
Dec 16 01:52:30 localhost postfix/smtpd[4186]: private/rewrite socket: wanted attribute: address
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: address
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute value: th8china@gmail.com
Dec 16 01:52:30 localhost postfix/smtpd[4186]: private/rewrite socket: wanted attribute: (list terminator)
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: (end)
Dec 16 01:52:30 localhost postfix/smtpd[4186]: rewrite_clnt: local: th8china@gmail.com -> th8china@gmail.com
Dec 16 01:52:30 localhost postfix/smtpd[4186]: send attr request = resolve
Dec 16 01:52:30 localhost postfix/smtpd[4186]: send attr sender = 
Dec 16 01:52:30 localhost postfix/smtpd[4186]: send attr address = th8china@gmail.com
Dec 16 01:52:30 localhost postfix/smtpd[4186]: private/rewrite socket: wanted attribute: flags
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: flags
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute value: 0
Dec 16 01:52:30 localhost postfix/smtpd[4186]: private/rewrite socket: wanted attribute: transport
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: transport
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute value: smtp
Dec 16 01:52:30 localhost postfix/smtpd[4186]: private/rewrite socket: wanted attribute: nexthop
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: nexthop
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute value: gmail.com
Dec 16 01:52:30 localhost postfix/smtpd[4186]: private/rewrite socket: wanted attribute: recipient
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: recipient
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute value: th8china@gmail.com
Dec 16 01:52:30 localhost postfix/smtpd[4186]: private/rewrite socket: wanted attribute: flags
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: flags
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute value: 4096
Dec 16 01:52:30 localhost postfix/smtpd[4186]: private/rewrite socket: wanted attribute: (list terminator)
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: (end)
Dec 16 01:52:30 localhost postfix/smtpd[4186]: resolve_clnt: `' -> `th8china@gmail.com' -> transp=`smtp' host=`gmail.com' rcpt=`th8china@gmail.com' flags= class=default
Dec 16 01:52:30 localhost postfix/smtpd[4186]: ctable_locate: install entry key th8china@gmail.com
Dec 16 01:52:30 localhost postfix/smtpd[4186]: extract_addr: in: <th8china@gmail.com>, result: th8china@gmail.com
Dec 16 01:52:30 localhost postfix/smtpd[4186]: fsspace: .: block size 4096, blocks free 7590547
Dec 16 01:52:30 localhost postfix/smtpd[4186]: smtpd_check_queue: blocks 4096 avail 7590547 min_free 0 msg_size_limit 10240000
Dec 16 01:52:30 localhost postfix/smtpd[4186]: > mail-iw0-f181.google.com[209.85.214.181]: 250 2.1.0 Ok
Dec 16 01:52:30 localhost postfix/smtpd[4186]: < mail-iw0-f181.google.com[209.85.214.181]: RCPT TO:<tt@aussiedragon.com.au>
Dec 16 01:52:30 localhost postfix/smtpd[4186]: extract_addr: input: <tt@aussiedragon.com.au>
Dec 16 01:52:30 localhost postfix/smtpd[4186]: smtpd_check_addr: addr=tt@aussiedragon.com.au
Dec 16 01:52:30 localhost postfix/smtpd[4186]: send attr request = rewrite
Dec 16 01:52:30 localhost postfix/smtpd[4186]: send attr rule = local
Dec 16 01:52:30 localhost postfix/smtpd[4186]: send attr address = tt@aussiedragon.com.au
Dec 16 01:52:30 localhost postfix/smtpd[4186]: private/rewrite socket: wanted attribute: flags
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: flags
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute value: 0
Dec 16 01:52:30 localhost postfix/smtpd[4186]: private/rewrite socket: wanted attribute: address
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: address
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute value: tt@aussiedragon.com.au
Dec 16 01:52:30 localhost postfix/smtpd[4186]: private/rewrite socket: wanted attribute: (list terminator)
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: (end)
Dec 16 01:52:30 localhost postfix/smtpd[4186]: rewrite_clnt: local: tt@aussiedragon.com.au -> tt@aussiedragon.com.au
Dec 16 01:52:30 localhost postfix/smtpd[4186]: send attr request = resolve
Dec 16 01:52:30 localhost postfix/smtpd[4186]: send attr sender = 
Dec 16 01:52:30 localhost postfix/smtpd[4186]: send attr address = tt@aussiedragon.com.au
Dec 16 01:52:30 localhost postfix/smtpd[4186]: private/rewrite socket: wanted attribute: flags
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: flags
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute value: 0
Dec 16 01:52:30 localhost postfix/smtpd[4186]: private/rewrite socket: wanted attribute: transport
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: transport
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute value: virtual
Dec 16 01:52:30 localhost postfix/smtpd[4186]: private/rewrite socket: wanted attribute: nexthop
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: nexthop
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute value: aussiedragon.com.au
Dec 16 01:52:30 localhost postfix/smtpd[4186]: private/rewrite socket: wanted attribute: recipient
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: recipient
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute value: tt@aussiedragon.com.au
Dec 16 01:52:30 localhost postfix/smtpd[4186]: private/rewrite socket: wanted attribute: flags
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: flags
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute value: 1024
Dec 16 01:52:30 localhost postfix/smtpd[4186]: private/rewrite socket: wanted attribute: (list terminator)
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: (end)
Dec 16 01:52:30 localhost postfix/smtpd[4186]: resolve_clnt: `' -> `tt@aussiedragon.com.au' -> transp=`virtual' host=`aussiedragon.com.au' rcpt=`tt@aussiedragon.com.au' flags= class=virtual
Dec 16 01:52:30 localhost postfix/smtpd[4186]: ctable_locate: install entry key tt@aussiedragon.com.au
Dec 16 01:52:30 localhost postfix/smtpd[4186]: extract_addr: in: <tt@aussiedragon.com.au>, result: tt@aussiedragon.com.au
Dec 16 01:52:30 localhost postfix/smtpd[4186]: send attr request = rewrite
Dec 16 01:52:30 localhost postfix/smtpd[4186]: send attr rule = local
Dec 16 01:52:30 localhost postfix/smtpd[4186]: send attr address = double-bounce
Dec 16 01:52:30 localhost postfix/smtpd[4186]: private/rewrite socket: wanted attribute: flags
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: flags
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute value: 0
Dec 16 01:52:30 localhost postfix/smtpd[4186]: private/rewrite socket: wanted attribute: address
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: address
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute value: double-bounce@li222-96.members.linode.com
Dec 16 01:52:30 localhost postfix/smtpd[4186]: private/rewrite socket: wanted attribute: (list terminator)
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: (end)
Dec 16 01:52:30 localhost postfix/smtpd[4186]: rewrite_clnt: local: double-bounce -> double-bounce@li222-96.members.linode.com
Dec 16 01:52:30 localhost postfix/smtpd[4186]: >>> START Recipient address RESTRICTIONS <<<
Dec 16 01:52:30 localhost postfix/smtpd[4186]: generic_checks: name=permit_mynetworks
Dec 16 01:52:30 localhost postfix/smtpd[4186]: permit_mynetworks: mail-iw0-f181.google.com 209.85.214.181
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_hostname: mail-iw0-f181.google.com ~? 127.0.0.1/32
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_hostaddr: 209.85.214.181 ~? 127.0.0.1/32
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_hostname: mail-iw0-f181.google.com ~? 173.255.212.98/32
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_hostaddr: 209.85.214.181 ~? 173.255.212.98/32
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_hostname: mail-iw0-f181.google.com ~? 173.255.212.96/32
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_hostaddr: 209.85.214.181 ~? 173.255.212.96/32
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_list_match: mail-iw0-f181.google.com: no match
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_list_match: 209.85.214.181: no match
Dec 16 01:52:30 localhost postfix/smtpd[4186]: generic_checks: name=permit_mynetworks status=0
Dec 16 01:52:30 localhost postfix/smtpd[4186]: generic_checks: name=reject_unauth_destination
Dec 16 01:52:30 localhost postfix/smtpd[4186]: reject_unauth_destination: tt@aussiedragon.com.au
Dec 16 01:52:30 localhost postfix/smtpd[4186]: permit_auth_destination: tt@aussiedragon.com.au
Dec 16 01:52:30 localhost postfix/smtpd[4186]: ctable_locate: leave existing entry key tt@aussiedragon.com.au
Dec 16 01:52:30 localhost postfix/smtpd[4186]: generic_checks: name=reject_unauth_destination status=0
Dec 16 01:52:30 localhost postfix/smtpd[4186]: >>> END Recipient address RESTRICTIONS <<<
Dec 16 01:52:30 localhost postfix/smtpd[4186]: >>> CHECKING RECIPIENT MAPS <<<
Dec 16 01:52:30 localhost postfix/smtpd[4186]: ctable_locate: leave existing entry key tt@aussiedragon.com.au
Dec 16 01:52:30 localhost postfix/smtpd[4186]: maps_find: recipient_canonical_maps: tt@aussiedragon.com.au: not found
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_string: aussiedragon.com.au ~? li222-96.members.linode.com
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_string: aussiedragon.com.au ~? localhost.members.linode.com
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_string: aussiedragon.com.au ~? localhost
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_list_match: aussiedragon.com.au: no match
Dec 16 01:52:30 localhost postfix/smtpd[4186]: maps_find: recipient_canonical_maps: @aussiedragon.com.au: not found
Dec 16 01:52:30 localhost postfix/smtpd[4186]: mail_addr_find: tt@aussiedragon.com.au -> (not found)
Dec 16 01:52:30 localhost postfix/smtpd[4186]: maps_find: canonical_maps: tt@aussiedragon.com.au: not found
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_string: aussiedragon.com.au ~? li222-96.members.linode.com
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_string: aussiedragon.com.au ~? localhost.members.linode.com
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_string: aussiedragon.com.au ~? localhost
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_list_match: aussiedragon.com.au: no match
Dec 16 01:52:30 localhost postfix/smtpd[4186]: maps_find: canonical_maps: @aussiedragon.com.au: not found
Dec 16 01:52:30 localhost postfix/smtpd[4186]: mail_addr_find: tt@aussiedragon.com.au -> (not found)
Dec 16 01:52:30 localhost postfix/smtpd[4186]: maps_find: virtual_alias_maps: tt@aussiedragon.com.au: not found
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_string: aussiedragon.com.au ~? li222-96.members.linode.com
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_string: aussiedragon.com.au ~? localhost.members.linode.com
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_string: aussiedragon.com.au ~? localhost
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_list_match: aussiedragon.com.au: no match
Dec 16 01:52:30 localhost postfix/smtpd[4186]: maps_find: virtual_alias_maps: @aussiedragon.com.au: not found
Dec 16 01:52:30 localhost postfix/smtpd[4186]: mail_addr_find: tt@aussiedragon.com.au -> (not found)
Dec 16 01:52:30 localhost postfix/smtpd[4186]: maps_find: virtual_mailbox_maps: tt@aussiedragon.com.au: not found
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_string: aussiedragon.com.au ~? li222-96.members.linode.com
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_string: aussiedragon.com.au ~? localhost.members.linode.com
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_string: aussiedragon.com.au ~? localhost
Dec 16 01:52:30 localhost postfix/smtpd[4186]: match_list_match: aussiedragon.com.au: no match
Dec 16 01:52:30 localhost postfix/smtpd[4186]: maps_find: virtual_mailbox_maps: hash:/etc/postfix/vmailbox(0,lock|fold_fix): @aussiedragon.com.au = test
Dec 16 01:52:30 localhost postfix/smtpd[4186]: mail_addr_find: tt@aussiedragon.com.au -> test
Dec 16 01:52:30 localhost postfix/smtpd[4186]: smtpd_check_rewrite: trying: permit_inet_interfaces
Dec 16 01:52:30 localhost postfix/smtpd[4186]: permit_inet_interfaces: mail-iw0-f181.google.com 209.85.214.181
Dec 16 01:52:30 localhost postfix/smtpd[4186]: before input_transp_cleanup: cleanup flags = enable_header_body_filter enable_automatic_bcc enable_address_mapping enable_milters
Dec 16 01:52:30 localhost postfix/smtpd[4186]: after input_transp_cleanup: cleanup flags = enable_header_body_filter enable_automatic_bcc enable_address_mapping
Dec 16 01:52:30 localhost postfix/smtpd[4186]: connect to subsystem public/cleanup
Dec 16 01:52:30 localhost postfix/smtpd[4186]: public/cleanup socket: wanted attribute: queue_id
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: queue_id
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute value: 45E7E182F2
Dec 16 01:52:30 localhost postfix/smtpd[4186]: public/cleanup socket: wanted attribute: (list terminator)
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: (end)
Dec 16 01:52:30 localhost postfix/smtpd[4186]: send attr flags = 178
Dec 16 01:52:30 localhost postfix/smtpd[4186]: 45E7E182F2: client=mail-iw0-f181.google.com[209.85.214.181]
Dec 16 01:52:30 localhost postfix/smtpd[4186]: > mail-iw0-f181.google.com[209.85.214.181]: 250 2.1.5 Ok
Dec 16 01:52:30 localhost postfix/smtpd[4186]: < mail-iw0-f181.google.com[209.85.214.181]: DATA
Dec 16 01:52:30 localhost postfix/smtpd[4186]: > mail-iw0-f181.google.com[209.85.214.181]: 354 End data with <CR><LF>.<CR><LF>
Dec 16 01:52:30 localhost postfix/cleanup[4190]: 45E7E182F2: message-id=<AANLkTinnYswtNeypUhf4NU+KgcridpeL8TJNY56DCsBm@mail.gmail.com>
Dec 16 01:52:30 localhost postfix/smtpd[4186]: public/cleanup socket: wanted attribute: status
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: status
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute value: 0
Dec 16 01:52:30 localhost postfix/smtpd[4186]: public/cleanup socket: wanted attribute: reason
Dec 16 01:52:30 localhost postfix/qmgr[4183]: 45E7E182F2: from=<th8china@gmail.com>, size=1620, nrcpt=1 (queue active)
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: reason
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute value: (end)
Dec 16 01:52:30 localhost postfix/smtpd[4186]: public/cleanup socket: wanted attribute: (list terminator)
Dec 16 01:52:30 localhost postfix/smtpd[4186]: input attribute name: (end)
Dec 16 01:52:30 localhost postfix/smtpd[4186]: > mail-iw0-f181.google.com[209.85.214.181]: 250 2.0.0 Ok: queued as 45E7E182F2
Dec 16 01:53:00 localhost postfix/smtpd[4186]: < mail-iw0-f181.google.com[209.85.214.181]: QUIT
Dec 16 01:53:00 localhost postfix/smtpd[4186]: > mail-iw0-f181.google.com[209.85.214.181]: 221 2.0.0 Bye
Dec 16 01:53:00 localhost postfix/smtpd[4186]: match_hostname: mail-iw0-f181.google.com ~? 127.0.0.1/32
Dec 16 01:53:00 localhost postfix/smtpd[4186]: match_hostaddr: 209.85.214.181 ~? 127.0.0.1/32
Dec 16 01:53:00 localhost postfix/smtpd[4186]: match_hostname: mail-iw0-f181.google.com ~? 173.255.212.98/32
Dec 16 01:53:00 localhost postfix/smtpd[4186]: match_hostaddr: 209.85.214.181 ~? 173.255.212.98/32
Dec 16 01:53:00 localhost postfix/smtpd[4186]: match_hostname: mail-iw0-f181.google.com ~? 173.255.212.96/32
Dec 16 01:53:00 localhost postfix/smtpd[4186]: match_hostaddr: 209.85.214.181 ~? 173.255.212.96/32
Dec 16 01:53:00 localhost postfix/smtpd[4186]: match_list_match: mail-iw0-f181.google.com: no match
Dec 16 01:53:00 localhost postfix/smtpd[4186]: match_list_match: 209.85.214.181: no match
Dec 16 01:53:00 localhost postfix/smtpd[4186]: send attr request = disconnect
Dec 16 01:53:00 localhost postfix/smtpd[4186]: send attr ident = smtp:209.85.214.181
Dec 16 01:53:00 localhost postfix/smtpd[4186]: private/anvil: wanted attribute: status
Dec 16 01:53:00 localhost postfix/smtpd[4186]: input attribute name: status
Dec 16 01:53:00 localhost postfix/smtpd[4186]: input attribute value: 0
Dec 16 01:53:00 localhost postfix/smtpd[4186]: private/anvil: wanted attribute: (list terminator)
Dec 16 01:53:00 localhost postfix/smtpd[4186]: input attribute name: (end)
Dec 16 01:53:00 localhost postfix/smtpd[4186]: disconnect from mail-iw0-f181.google.com[209.85.214.181]
Dec 16 01:53:00 localhost postfix/smtpd[4186]: master_notify: status 1
Dec 16 01:53:00 localhost postfix/smtpd[4186]: connection closed
Dec 16 01:53:00 localhost postfix/smtpd[4186]: proxymap stream disconnect
Dec 16 01:53:00 localhost postfix/smtpd[4186]: auto_clnt_close: disconnect private/tlsmgr stream
Dec 16 01:53:00 localhost postfix/smtpd[4186]: rewrite stream disconnect
Dec 16 01:53:28 localhost postfix/virtual[4195]: fatal: dict_open: unsupported dictionary type: virtual:  Is the postfix-virtual package installed?
Dec 16 01:53:29 localhost postfix/master[3375]: warning: process /usr/lib/postfix/virtual pid 4195 exit status 1
Dec 16 01:53:29 localhost postfix/master[3375]: warning: /usr/lib/postfix/virtual: bad command startup -- throttling

```


after I send a text email from gmail , I got the error in log file:
**localhost postfix/virtual[4195]: fatal: dict_open: unsupported dictionary type: virtual:  Is the postfix-virtual package installed?**

here is some of my server configuration:

```
root@li222-96:~# hostname
li222-96
```

```
root@li222-96:~# cat /etc/mailname 
li222-96.members.linode.com
```

```
root@li222-96:~# cat /etc/postfix/main.cf 
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = li222-96.members.linode.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
##mydestination = aussiedragon.com.au

mynetworks_style = host
relay_domains =
relayhost = 
#mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4



virtual_mailbox_domains = aussiedragon.com.au
virtual_mailbox_base = /var/mail/virtual/
#virtual_mailbox_maps = mysql:/etc/postfix/mysql_maps.cf
virtual_mailbox_maps = hash:/etc/postfix/vmailbox
virtual_uid_maps = virtual:5000
virtual_gid_maps = virtual:5000

```

```

root@li222-96:~# cat /etc/postfix/master.cf 
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd -v
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
	-o smtp_fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual 
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# ====================================================================
#
# Recent Cyrus versions can use the existing "lmtp" master.cf entry.
#
# Specify in cyrus.conf:
#   lmtp    cmd="lmtpd -a" listen="localhost:lmtp" proto=tcp4
#
# Specify in main.cf one or more of the following:
#  mailbox_transport = lmtp:inet:localhost
#  virtual_transport = lmtp:inet:localhost
#
# ====================================================================
#
# Cyrus 2.1.5 (Amos Gouaux)
# Also specify in main.cf: cyrus_destination_recipient_limit=1
#
#cyrus     unix  -       n       n       -       -       pipe
#  user=cyrus argv=/cyrus/bin/deliver -e -r ${sender} -m ${extension} ${user}
#
# ====================================================================
# Old example of delivery via Cyrus.
#
#old-cyrus unix  -       n       n       -       -       pipe
#  flags=R user=cyrus argv=/cyrus/bin/deliver -e -m ${extension} ${user}
#
# ====================================================================
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}


```

```
root@li222-96:~# cat /etc/postfix/vmailbox
@aussiedragon.com.au test

```

The mail is in the queue which can be accessed by mailq command, but the mailbox directory is empty

Could anyone help please..?

---

