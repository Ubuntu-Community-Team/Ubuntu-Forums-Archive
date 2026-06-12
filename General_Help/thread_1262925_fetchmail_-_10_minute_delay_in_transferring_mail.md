---
title: "fetchmail - 10 minute delay in transferring mail"
date: 2009-09-10
forum: General Help
---

### Post by George Heine on 2009-09-10
Hello -

Am using Ubuntu 9.04, recently installed the "fetchmail" package.  
This is strictly a client system; I only want to retrieve and store
old mail messages to avoid clogging the server.

Last night I used fetchmail to retrieve 127 messages from the server.
Immediately after, I checked (with 'alpine') and found only 10 of them
in the inbox.  Same result with 'mail.'  Opened up /var/mail/<username>
with a text editor and it looked the same.

After about ten minutes, went back into alpine and all the messages
were there!  This is only a minor annoyance, but - what causes this delay?
Where do those missing messages go? What can be done about it?

A dump of my results from 'fetchmail --version' are listed below in case this
is helpful (user and server names deleted).  Thank you!

_____________________________________________________________________________
This is fetchmail release 6.3.9-rc2+GSS+NTLM+SDPS+SSL+NLS+KRB5.
Copyright (C) 2002, 2003 Eric S. Raymond
Copyright (C) 2004 Matthias Andree, Eric S. Raymond, Robert M. Funk, Graham Wilson
Copyright (C) 2005 - 2006 Sunil Shetye
Copyright (C) 2005 - 2008 Matthias Andree
Fetchmail comes with ABSOLUTELY NO WARRANTY. This is free software, and you
are welcome to redistribute it under certain conditions. For details,
please see the file COPYING in the source or documentation directory.

Fallback MDA: (none)
Linux ganesh 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux
Taking options from command line and /home/gheine/.fetchmailrc
Idfile is /home/gheine/.fetchids
Fetchmail will show progress dots even in logfiles.
Fetchmail will forward misaddressed multidrop messages to gheine.
Options for retrieving from <>
  True name of server is <>
  Password will be prompted for.
  Protocol is IMAP.
  All available authentication methods will be tried.
  Server nonresponse timeout is 120 seconds.
  Default mailbox selected.
  All messages will be retrieved (--all on).
  Fetched messages will be kept on the server (--keep on).
  Old messages will not be flushed before message retrieval (--flush off).
  Oversized messages will not be flushed before message retrieval (--limitflush off).
  Rewrite of server-local addresses is enabled (--norewrite off).
  Carriage-return stripping is disabled (stripcr off).
  Carriage-return forcing is disabled (forcecr off).
  Interpretation of Content-Transfer-Encoding is enabled (pass8bits off).
  MIME decoding is disabled (mimedecode off).
  Idle after poll is disabled (idle off).
  Nonempty Status lines will be kept (dropstatus off)
  Delivered-To lines will be kept (dropdelivered off)
  Message size limit is 100000 octets (--limit 100000).
  Fetch message size limit is 100 (--fetchsizelimit 100).
  Do binary search of UIDs during 3 out of 4 polls (--fastuidl 4).
  Messages will be SMTP-forwarded to: localhost (default)
  Single-drop mode: 1 local name recognized.
  No UIDs saved from this host.
__________________________________________________________________________

---

### Post by George Heine on 2010-12-20
Fifteen months later, no replies.  Oh well, have found a solution in case someone else has this problem.
Turns out the problem is in the Mail Transport Agent (MTA), which on my box is exim4.  (Installed by default
on 9.04; apparently in Lucid there is no default MTA).   

Anyway, there are two steps.
STEP ONE. At the command line, enter 

```
$ sudo adduser <username> Debian-exim

```This changes the /etc/groups file; howerver, it does not seem to be read except on startup (or possibly login).  So restart the computer (or logout, then log back in again), type

```
$ groups
```and you should see "Debian-exim" listed among the groups you belong to.

STEP TWO After every run of fetchmal, type

```
$exim -q
```This starts the mail delivery queue in the background.  After a short or long delay, depending on
how many messages you fetched, the process exits.  You should now have all of your messages
in your inbox.

---

### Post by George Heine on 2010-12-20
Oh, I forgot.  There is a way, via a postprocessing directive in the ~/.fetchmailrc file, to automatically
run exim -q after fetchmail.  (See fetchmail documentation for details.)   I might try this out someday.
However, for the present, it seems about as easy to type two commands as one.

---

