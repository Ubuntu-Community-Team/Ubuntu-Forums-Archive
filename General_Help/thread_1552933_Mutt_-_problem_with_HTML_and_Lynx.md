---
title: "Mutt - problem with HTML and Lynx"
date: 2010-08-14
forum: General Help
---

### Post by Duncan J Murray on 2010-08-14
Hi there,

I have a slight problem with using Mutt and Lynx to view html stuff that people send.

The problem is that mutt now seems to think almost everything is html!  So receiving mail from, say a gmail user, will give me a lynx dump, rather than just displaying the plain text.

Any ideas?

My muttrc is:

set from = "****"
set realname = "Duncan J Murray"
set imap_user = "****"
set imap_pass = "****"
set folder = "imaps://imap.gmail.com:993"
set spoolfile = "+INBOX"
set postponed = "+[Gmail]/Drafts"
set header_cache=~/.mutt/cache/headers
set message_cachedir =~/.mutt/cache/bodies
set certificate_file =~/.mutt/certificates
set smtp_url = "smtp://****:587/"
set smtp_pass = "****"
set move = no #Stop asking to "move read messages to mbox"!
set imap_keepalive = 900

#Text Editor
set editor="nano -r 0 --fill=-4"

#Colours!
color index brightgreen black ~N
color index brightred default ~D
color quoted green black
color signature cyan black
color attachment yellow black

#Address Book
macro index,pager A "<pipe-message>abook --add-email-quiet<return>" "add the sender address to abook"

#Reading Mail
set timeout=10
set mail_check=5
set sort=threads
set sort_aux=date

#Mailboxes
mailboxes +INBOX +archive +sent +drafts +spam +trash
bind editor <space> noop

macro index,pager y "<save-message>=[Google Mail/All Mail]<enter><enter>" "Archive"
macro index,pager d "<save-message>=[Google Mail/Trash]<enter><enter>" "Trash"

macro index <f3> "<change-folder>=[Google Mail]/All Mail<enter>" "Go to all mail"
macro index <f2> "c!\n"

#Reading URLs
macro pager \cl <pipe-entry>'urlview'<enter> 'Follow links with urlview'

#Reading HTML
#set implicit_autoview
#auto_view text/html application/x-pgp-message
#set mailcap_path="~/.mailcap"



And my .mailcap file is:

text/html; lynx -dump -force_html %s; needsterminal; copiousoutput





Many thanks in advance!

Duncan.

---

### Post by Duncan J Murray on 2010-08-14
Having a look in more detail - I think the problem is with email which provide text/html as well as text/plain.

These emails seem to trigger lynx to output, but all I really want is to view the text/plain file.  The only time I really need lynx is to view emails which only have text/html.

Any ideas?

Duncan.

---

### Post by andrew.46 on 2010-08-21
Hi Duncan,

I am not entirely sure about this problem as fortunately not many people send me this type of message :). I use w3m myself rather than lynx as this gives reasonable representation of tables as well. In my ~/.muttrc:

```

set mailcap_path="~/mail/mutt/mutt_mailcap"
auto_view text/html                                      
set implicit_autoview=yes               

```

And in ~/mail/mutt/mutt_mailcap:

```

text/html; /usr/bin/w3m -cols 90 -dump -T text/html '%s'; copiousoutput

```

For the multipart messages you describe perhaps try the following in ~/.muttrc:

```

alternative_order text/plain text/html

```

and this may force mutt text/plain rather than choke trying to display both :).

Andrew

---

### Post by Duncan J Murray on 2010-09-11
Hmmm, many thanks!

I will give that a try and see if it works...

Duncan.

---

