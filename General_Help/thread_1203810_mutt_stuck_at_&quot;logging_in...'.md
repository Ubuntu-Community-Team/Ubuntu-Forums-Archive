---
title: "mutt stuck at &quot;logging in...'"
date: 2009-07-03
forum: General Help
---

### Post by r_avital on 2009-07-03
Hi all,

Just installed mutt and followed the directions in [this linuxjournal article]("http://www.linuxjournal.com/article/10115").  Having difficulty logging in (or so it seems).  Found several beginner and advanced tutorials ion mutt on the net, but most are outdated or inaccurate.

Behavior:  when running mutt for the first time, I get a certificate from my email provider - which I suppose means I'm connecting to them ok.  I choose option to accept always - this saves the cert but the next time I run mutt, it prompts me to accept again, and if I select accept always it warns me that it could not save (if I delete the previously saved cert, this save succeeds).

The more pressing problem: It shows a message at the bottom - "Logging In..." and hangs there forever.  I need to close the terminal session (konsole) to exit.

Mutt shows me an INBOX mailbox with 0 messages.  I have also created (manually) the ~/Mail/Inbox, ~/Mail/Sent and ~/Mail/draft folders.

I also tried sending, by picking a name in abook and pressing m to send with mutt, but since I can't log in, it makes sense that it would fail.

Please, any thoughts would be greatly appreciated.  Thanks in advance.

Running mutt version 1.5.18 from konsole prompt, ubuntu jaunty, under gnome.  Here is my .muttrc file, minus the pretty colors stuff and with fake names for privacy:

```
# Local folder
set mbox_type=Maildir
set folder=~/Mail

# IMAP Settings
set realname="me myself"
#set folder=imaps://mail.soandso.net
set spoolfile=imaps://mail.soandso.net/Inbox
set record=imaps://mail.soandso.net/Sent
set postponed=mail.soandso.net/Draft
mailboxes =INBOX # check for new email here
set header_cache=~/.mutt_cache

set from="Me Myself <memyself@soandso.net>"
set imap_user=memyself@soandso.net
set header_cache=~/.mutt_cache
set smtp_url="smtps://memyself\@soandso.net@mail.soandso.net/"

# Reading Mail
set timeout=10  
set mail_check=5
set sort=threads
set sort_aux=date
set move=no     
set mark_old=no
ignore * # ignore all headers except for ...
unignore Date: From: To: CC: Bcc: Subject:
hdr_order Subject: Date: From: To: CC: Bcc:
set index_format="%{%b %d} %-15.15L [%Z] %s" # custom index format

# Composing Mail
set editor="nano"
set markers=no
#set signature=~/.sig
set include=yes
set forward_format="Fwd: %s"

# Sending Mail
set copy=yes
set smtp_url="smtps://memyself\@soandso.net@mail.mailsnare.net/"

```

---

