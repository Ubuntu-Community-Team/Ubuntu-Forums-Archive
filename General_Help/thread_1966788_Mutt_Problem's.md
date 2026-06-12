---
title: "Mutt Problem's"
date: 2012-04-27
forum: General Help
---

### Post by jfreak53 on 2012-04-27
Anyone a Mutt person?  I'm having major problem's with a mutt config and multiple account's.

Oh believe me it works just fine, for reading and writing :), but I have two account's a gmail and a google app's.  They work great, but on the second account, gmail, when I delete an email it doesn't go to trash, it just removes label's.  Which in turn put's it in All Mail and removes from inbox.  So once a week I have to filter through all mail and remove those that I deleted! ha ha

Here are my config's:

.muttrc
```
macro index <f2> '<change-folder>imaps://imap.gmail.com<enter>'
macro index <f3> '<change-folder>imaps://user@imap.gmail.com<enter>'

account-hook    imaps://user@imap.gmail.com 'set imap_user=user@gmail.com imap_pass="password"'
account-hook    imaps://imap.gmail.com 'set imap_user=me@domain.com imap_pass="password"'
folder-hook     'imaps://user@imap.gmail.com' 'source ~/.mutt/account.gmail'
folder-hook     'imaps://imap.gmail.com' 'source ~/.mutt/account.micro'

source ~/.mutt/account.micro

mailboxes "=INBOX"
unset imap_passive

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
set markers=no # don't put '+' at the beginning of wrapped lines
set pager_index_lines= 5 # how large is the index window?
set sort = 'threads'
set sort_aux = 'last-date-received'

# My Rolodeck :)
set alias_file= ~/.mutt/aliases
set sort_alias= alias
set reverse_alias=yes
source $alias_file

set include # quote msg when replying
set fast_reply # do not ask for to, sbuject,.. when replying

macro index gt "<change-folder>=[Gmail]/Trash<enter>" "Go to trash"
macro index,pager gi "<change-folder>=INBOX<enter>" "Go to inbox"
```

micro:
```
set smtp_url = "smtp://me@domain.com@smtp.gmail.com:587/"
set smtp_pass = "pass"
set from = "me@domain.com"
set realname = "name"
set imap_user = 'me@domain.com'
set imap_pass = 'pass'
set spoolfile = imaps://imap.gmail.com:993/INBOX
set folder = imaps://imap.gmail.com:993
set record='imaps://imap.gmail.com/[Gmail]/Sent Mail'
set postponed='imaps://imap.gmail.com/[Gmail]/Drafts'
set trash = "imaps://imap.gmail.com/[Gmail]/Trash"
set header_cache='~/.mutt/cache/headers'
set message_cachedir='~/.mutt/cache/bodies'
set certificate_file=~/.mutt/certificates
set move = no  #Stop asking to "move read messages to mbox"!
set imap_keepalive = 250
set signature="~/.mutt/sig"
set sig_on_top = yes

```

gmail
```
set smtp_url = "smtp://user@gmail.com@smtp.gmail.com:587/"
set smtp_pass = "pass"
set from = "user@gmail.com"
set realname = "name"
set imap_user = 'user@gmail.com'
set imap_pass = 'pass'
set spoolfile = imaps://imap.gmail.com:993/INBOX
set folder = imaps://imap.gmail.com:993
set record='imaps://imap.gmail.com/[Gmail]/Sent Mail'
set postponed='imaps://imap.gmail.com/[Gmail]/Drafts'
#set trash = "imaps://imap.gmail.com/[Gmail]/Trash"
set trash = "=[Gmail]/Trash"
set header_cache='~/.mutt/cache/headers'
set message_cachedir='~/.mutt/cache/bodies'
set certificate_file=~/.mutt/certificates
set move = no  #Stop asking to "move read messages to mbox"!
set imap_keepalive = 250
set signature="~/.mutt/sig"
set sig_on_top = yes

```

Now you'll notice that in the gmail one I have two trash option's one commented.  I've tried both that's why, neither one work.

It work's just great on my apps account, moves things to trash.  But for some reason on the regular gmail account, NIL!!! ha ha

Thank's for any help.

---

### Post by jfreak53 on 2012-04-28
Anyone?

---

### Post by jfreak53 on 2012-04-28
Nevermind I just figured it out after much trial and error.  Seems since I have a default account if I just put imap/trash it doesn't work since it think's it the default, I have to include the username.  So my final trash line looks like this:

```
set trash = "imaps://user@imap.gmail.com/[Gmail]/Trash"
```

That one is working for me just fine :)

---

