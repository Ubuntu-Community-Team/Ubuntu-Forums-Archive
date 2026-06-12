---
title: "Accessing lavabit's IMAP folder with mutt?"
date: 2010-07-02
forum: General Help
---

### Post by 10972349873 on 2010-07-02
I'm having some issues accessing any folders besides INBOX on the  lavabit IMAP server using mutt.  I'm not sure if it's something I'm  doing wrong specifically or if lavabit just has some funky folder setup  and I don't know how to use it.  Here's the server setup:
[http://lavabit.com/help.html](http://lavabit.com/help.html)
though I don't think that'll do much good for my issue  (more specifically: I can log in, send messages and read my inbox, but  not use other folders).

Here's my .muttrc:

```
#####.muttrc#####
set realname		= '<REAL NAME>'
set from		= <USER>

set imap_user		= [user]@lavabit.com
set folder		=imaps://lavabit.com:993
set spoolfile		= +INBOX
set postponed		= +Drafts
set trash		= +Trash
set record		= +Sent



#Check mail regularly
mailboxes 		= +Inbox +Important

# allow mutt to open new imap connection automatically
set imap_passive 	= no

# keep imap connection alive by polling intermittently (time in seconds)
set imap_keepalive 	= 300

# how often to check for new mail (time in seconds)
set mail_check 		= 20

#Cache config stuff to speed everything up
set header_cache 	= ~/.mutt/cache/headers
set message_cachedir 	= ~/.mutt/cache/bodies
set certificate_file 	= ~/.mutt/certificates
set edit_headers	= yes


#Sending emails
set sendmail		= "/usr/bin/msmtp"
set my_user		= <USER>@lavabit.comm
set smtp_url		= smtps://<USER>@lavabit.com
set ssl_force_tls	= yes


# Header stuff
ignore "Authentication-Results:"
ignore "DomainKey-Signature:"
ignore "DKIM-Signature:"
hdr_order Date From To Cc

ignore *
unignore from: date subject to cc
unignore x-mailing-list: posted-to:
unignore x-mailer:

# For better looks
set markers		= no #(don't put '+' at the beginning of wrapped lines)
set pager_index_lines	= 5 # how large is the index window?
set sort 		= 'threads'
set sort_aux 		= 'last-date-received'


```

---

### Post by polarops on 2011-09-23
Hi. I've discovered the exact same problem. Did you figure this out or give up?

---

