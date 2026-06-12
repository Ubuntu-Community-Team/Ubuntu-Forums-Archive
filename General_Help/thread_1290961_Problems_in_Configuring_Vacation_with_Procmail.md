---
title: "Problems in Configuring Vacation with Procmail"
date: 2009-10-14
forum: General Help
---

### Post by kevinkan on 2009-10-14
Dear all,
I have followed the instructions in configuring vacation with procmail from this website: [http://www.clarkconnect.com/wiki/index.php?title=Howtos_-_Procmail_Vacation_Auto-Reply_Recipe](http://www.clarkconnect.com/wiki/index.php?title=Howtos_-_Procmail_Vacation_Auto-Reply_Recipe)
However, when I was sending test emails to the test email address, I am unable to receive the auto reply emails. From the log file, I've noticed that the logging stopped halfway. As I am not familiar with procmail scripting, I am unable to debug the script.
I am attaching the script with I have updated my domain and password, as well as the log. 
=======================================================================
<Script>
 
# Uncomment the lines below if you need log output for testing.
#
LOGFILE=/tmp/procmailvacation.log
VERBOSE=on
# vim: ft=procmail
# User-managed vacation recipe for procmail
# Written by Jason Thaxter
# ([http://www.google.com/search?q=jason+thaxter](http://www.google.com/search?q=jason+thaxter))
# * Include this file in the procmail file.
# * Set $VACATION_PASSWORD. (for security, this is mandatory)
# * Define $VACATION_SENDER in your procmail recipe: it will be "from" this
# address.
# * E-mail a message with $VACATION_PASSWORD and $VACATION_ON in the subject
# line. The body of the message becomes the vacation message. $VACATION_ON
# can be set prior to the INCLUDERC, but it defaults to "vacation on".
# * To turn it off, e-mail a message with $VACATION_PASSWORD and $VACATION_OFF
# in the subject line. Likewise, $VACATION_OFF defaults to "vacation off".
# Note that you probably want this to execute *after* any mailing list or spam
# delivery recipes. You can set $VACATION_SKIP to disable vacation processing
# if it's inconvenient to skip this recipe.
# -----------------------------------------------------------------------------
# Configurable variables: These variables allow you to use this vacation recipe
# as an include and customize it from your main procmail file.
#
# lockfile:
VACATION_LOCK=$HOME/${VACATION_LOCK:-".vacation$LOCKEXT"}
# cache file:
VACATION_CACHE=$HOME/${VACATION_CACHE:-".vacation_cache"}
# cache size:
VACATION_CACHE_SZ=${VACATION_CACHE_SZ:-8192}
# message file
VACATION_MSG=$HOME/${VACATION_MSG:-".vacation_mesg"}
# what to use as the xloop header
HOSTNAME=${HOSTNAME:-`hostname`}
VACATION_XLOOP=${VACATION_XLOOP:-"$LOGNAME@$HOSTNAME"}
# base token for default $VACATION_ON and $VACATION_OFF
# so you could set this and not those individually
VACATION_COOKIE=${VACATION_COOKIE:-"vacation"}
VACATION_ON=${VACATION_ON:-"$VACATION_COOKIE on"}
VACATION_OFF=${VACATION_OFF:-"$VACATION_COOKIE off"}
#
#Change these variables
#
VACATION_PASSWORD=password
VACATION_DOMAIN_NAME=xxx.com
VACATION_SENDER=$LOGNAME@$VACATION_DOMAIN_NAME
VACATION_SENDMAILFROM=${VACATION_SENDMAILFROM:-"-f$VACATION_SENDER"}
VACATION_SENDMAILFLAGS="-oi -t $VACATION_SENDMAILFROM"
# -----------------------------------------------------------------------------
SENDMAIL_CMD="$SENDMAIL $VACATION_SENDMAILFLAGS"
SHELL=/bin/sh
# check if we should send vacation message, add user to cache
:0 Whc: $VACATION_LOCK
# if i haven't been instructed to skip processing
* ? test -z “$VACATION_SKIP”
# if i have a vacation message file
* ? test -f “$VACATION_MSG”
# and the message is not from a daemon or mailer
* !^FROM_DAEMON
* !^FROM_MAILER
# not declared spam by spamassassin
* !^X-Spam-Flag: YES
# not discernably in a mailing list
* !^List-
* !^(Mailing-List|Approved-By|BestServHost|Resent-(Message-ID|Sender)):
* !^X-[^:]*-List:
* !^X-(Sent-To|(Listprocessor|Mailman)-Version):
# and not x-loop
* $ !^X-Loop: $VACATION_XLOOP
# add it to the cache
| formail -rD $VACATION_CACHE_SZ $VACATION_CACHE
:0 ehc
# if the name was not in the cache
# if we can find who we're sending it to
# and who we are sending this "From"
* ? test -n ${VACATION_MSG_SEND_TO}
* ? test -n ${VACATION_SENDER}
* $ !^From:.*$VACATION_SENDER
| (formail -r \
-I"Precedence: junk" \
-A"From: $VACATION_SENDER" \
-A"X-Loop: $VACATION_XLOOP"; \
cat $VACATION_MSG ) | \
$SENDMAIL_CMD
# Add/remove vacation message
:0
# First make sure that the sender has 
# the correct username
* ^TO_\/[-\.a-z_]+@
*$ ^From:.*$\MATCH
# the correct email domain
*$ ^From:.*$\VACATION_DOMAIN_NAME
# only do this if we have a password set
* ? test -n “$VACATION_PASSWORD”
# and it's in the subject line
* $^Subject:.*${VACATION_PASSWORD}
{
# VACATION ON
# if subject line matches magic cookie for ON:
:0
* $^Subject:.*${VACATION_ON}
{
# pipe the body into the vacation message file
:0c:$VACATION_LOCK
| formail -I "" > $VACATION_MSG
 
# add message to the body
:0f
| cat - ; \
echo; \
echo '---------- VACATION -----------------'; \
echo 'The above text was installed as your vacation message'
}
# VACATION OFF
# if subject line matches magic cookie for OFF:
# delete the vacation file and notify
:0f
* $^Subject:.*${VACATION_OFF}
| cat -; \
echo '---------- VACATION -----------------'; \
echo 'Removing message and cache: '; \
rm -vf $VACATION_MSG; \
rm -vf $VACATION_CACHE; \
echo ; \
echo "Removed vacation message."
}
=======================================================================
<Log>
procmail: [7204] Wed Oct 14 15:38:01 2009
procmail: Assigning "VACATION_LOCK=/home/prj/mrs/.vacation.lock"
procmail: Assigning "VACATION_CACHE=/home/prj/mrs/.vacation_cache"
procmail: Assigning "VACATION_CACHE_SZ=8192"
procmail: Assigning "VACATION_MSG=/home/prj/mrs/.vacation_mesg"
procmail: Executing "hostname"
procmail: Assigning "HOSTNAME=mail.xxx.com"
procmail: Assigning "[EMAIL="VACATION_XLOOP=mrs@mail.xxx.com"]VACATION_XLOOP=mrs@mail.xxx.com[/EMAIL]"
procmail: Assigning "VACATION_COOKIE=vacation"
procmail: Assigning "VACATION_ON=vacation on"
procmail: Assigning "VACATION_OFF=vacation off"
procmail: Assigning "VACATION_PASSWORD=password"
procmail: Assigning "VACATION_DOMAIN_NAME=xxx.com"
procmail: Assigning "[EMAIL="VACATION_SENDER=mrs@xxx.com"]VACATION_SENDER=mrs@xxx.com[/EMAIL]"
procmail: Assigning "[EMAIL="VACATION_SENDMAILFROM=-fmrs@xxx.com"]VACATION_SENDMAILFROM=-fmrs@xxx.com[/EMAIL]"
procmail: Assigning "VACATION_SENDMAILFLAGS=-oi -t [EMAIL="-fmrs@xxx.com"]-fmrs@xxx.com[/EMAIL]"
procmail: Assigning "SENDMAIL_CMD=/usr/sbin/sendmail -oi -t [EMAIL="-fmrs@xxx.com"]-fmrs@xxx.com[/EMAIL]"
procmail: Assigning "SHELL=/bin/sh"
procmail: Executing " test -z "$VACATION_SKIP""
procmail: Match on " test -z "$VACATION_SKIP""
procmail: Executing " test -f "$VACATION_MSG""
procmail: Non-zero exitcode (1) from " test -f "$VACATION_MSG""
procmail: No match on " test -f "$VACATION_MSG""
procmail: Assigning "MATCH="
procmail: Matched "mrs@"
procmail: Match on "(^((Original-)?(Resent-)?(To|Cc|Bcc)|(X-Envelope|Apparently(-Resent)?)-To):(.*[^-a-zA-Z0-9_.])?)\/[-\.a-z_]+@"
procmail: No match on "^From:.*()mrs@"
procmail: Bypassed locking "/var/mail/mrs.lock"
procmail: Assigning "LASTFOLDER=/var/mail/mrs"
procmail: Opening "/var/mail/mrs"
procmail: Acquiring kernel-lock
procmail: Notified comsat: "mrs@8329:/var/mail/mrs"
From [EMAIL="kevin@xxx.com"]kevin@xxx.com[/EMAIL] Wed Oct 14 15:38:01 2009
Subject: password vacation on
Folder: /var/mail/mrs 657
procmail: [7220] Wed Oct 14 15:39:53 2009
procmail: Assigning "VACATION_LOCK=/home/prj/mrs/.vacation.lock"
procmail: Assigning "VACATION_CACHE=/home/prj/mrs/.vacation_cache"
procmail: Assigning "VACATION_CACHE_SZ=8192"
procmail: Assigning "VACATION_MSG=/home/prj/mrs/.vacation_mesg"
procmail: Executing "hostname"
procmail: Assigning "HOSTNAME=mail.xxx.com"
procmail: Assigning "[EMAIL="VACATION_XLOOP=mrs@mail.xxx.com"]VACATION_XLOOP=mrs@mail.xxx.com[/EMAIL]"
procmail: Assigning "VACATION_COOKIE=vacation"
procmail: Assigning "VACATION_ON=vacation on"
procmail: Assigning "VACATION_OFF=vacation off"
procmail: Assigning "VACATION_PASSWORD=password"
procmail: Assigning "VACATION_DOMAIN_NAME=xxx.com"
procmail: Assigning "[EMAIL="VACATION_SENDER=mrs@xxx.com"]VACATION_SENDER=mrs@xxx.com[/EMAIL]"
procmail: Assigning "[EMAIL="VACATION_SENDMAILFROM=-fmrs@xxx.com"]VACATION_SENDMAILFROM=-fmrs@xxx.com[/EMAIL]"
procmail: Assigning "VACATION_SENDMAILFLAGS=-oi -t [EMAIL="-fmrs@xxx.com"]-fmrs@xxx.com[/EMAIL]"
procmail: Assigning "SENDMAIL_CMD=/usr/sbin/sendmail -oi -t [EMAIL="-fmrs@xxx.com"]-fmrs@xxx.com[/EMAIL]"
procmail: Assigning "SHELL=/bin/sh"
procmail: Executing " test -z "$VACATION_SKIP""
procmail: Match on " test -z "$VACATION_SKIP""
procmail: Executing " test -f "$VACATION_MSG""
procmail: Non-zero exitcode (1) from " test -f "$VACATION_MSG""
procmail: No match on " test -f "$VACATION_MSG""
procmail: Assigning "MATCH="
procmail: Matched "mrs@"
procmail: Match on "(^((Original-)?(Resent-)?(To|Cc|Bcc)|(X-Envelope|Apparently(-Resent)?)-To):(.*[^-a-zA-Z0-9_.])?)\/[-\.a-z_]+@"
procmail: No match on "^From:.*()mrs@"
procmail: Bypassed locking "/var/mail/mrs.lock"
procmail: Assigning "LASTFOLDER=/var/mail/mrs"
procmail: Opening "/var/mail/mrs"
procmail: Acquiring kernel-lock
procmail: Notified comsat: "mrs@8986:/var/mail/mrs"
From [EMAIL="kevin@xxx.com"]kevin@xxx.com[/EMAIL] Wed Oct 14 15:39:53 2009
Subject: what is this?
Folder: /var/mail/mrs 647
========================================================================
Can someone help me please??
Thank you very much in advance.
 
Regards,
Kevin

---

### Post by slakkie on 2009-10-14
Holy... 

This is my .procmailrc for .vacation messages:

```

# .procmailrc
## GENERAL
TZ=CET
DATE=`date +%Y%m`
LOGFILE=$HOME/maillog/procmail-$DATE.log
MSGIDLOGFILE=$HOME/maillog/procmail-messageid.log

## MAILFOLDERS
MAILDIR=$HOME/mail

# [snip, procmail filters for all kinds of stuff]

# Vacation message
#INCLUDERC=$HOME/.procmailrc_vacation

```

```

# $HOME/.procmailrc_vacation
#VERBOSE=yes
#
# This is actually two recipies. This is meant to go at the END of your
# .procmailrc so it doesn't trigger on mailing lists that you're filtering above.
#
# Will add the sender to the vacation cache if not already in the vacation
# cache  FROM_DAEMON is a macro for a lot of "system" addresses. see the
# procmailrc man page fordetails
#
:0 Whc: vacation.lock
* !^FROM_DAEMON
* !^X-Loop:
| formail -rD 8192 name_of_cache

#
# Only run this rule if the last rule didn't match, meaning it will only mail each
# user once.
#
:0 ehc         # if the name was not in the cache
| (formail -rA"Precedence: junk" \
   -A"X-Loop: myname@somedomain.tld" ; \
   cat $HOME/.vacation; \
   echo ""; \
   echo "-- "; cat $HOME/.signature.work \
   ) | $SENDMAIL -oi -t -r myname@somedomain.tld

```

---

