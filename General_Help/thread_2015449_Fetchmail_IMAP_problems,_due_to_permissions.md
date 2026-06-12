---
title: "Fetchmail IMAP problems, due to permissions?"
date: 2012-07-03
forum: General Help
---

### Post by OpEn_SoUrCe_RoCkS on 2012-07-03
Hi all,

I ran a "chmod 777 *" on my home folder. (I know, I know. I'll never do it again.)

Ever since then, fetchmail seems to be broken for some reason. 

I use it to fetch mail from an Exchange 2003 mailbox through DAVMail and OWA.

The problem is that fetchmail complains about an "expunge mismatch" whenever I get a new message. It deletes the message from the mailbox, yet it never forwards it. There seems to be a problem somwhere along the mail processing, but I haven't been able to pinpoint where.

Any help would be appreciated.

Here are the relevant config files.

~/fetchmailrc
```
set no bouncemail
defaults:
  antispam -1
  batchlimit 100
poll localhost with protocol imap and port 1143
user domain\\user password Password is root
no rewrite
mda "/usr/bin/procmail -f %F -d %T";
```

~/procmailrc
```
:0
* ^Subject.*ack
| expand | sed -e 's/[ ]*$//g' | sed -e 's/^/ /' > /usr/local/nagios/libexec/mail_acknowledgement
```

~/.forward
```
| "/usr/bin/procmail"
```


Here is the output when I run "fetchmail -f /root/.fetchmailrc  -vv":
```
fetchmail: WARNING: Running as root is discouraged.
Old UID list from localhost: <empty>
Scratch list of UIDs: <empty>
fetchmail: 6.3.19 querying localhost (protocol IMAP) at Tue 03 Jul 2012 09:46:36 AM EDT: poll started
Trying to connect to 127.0.0.1/1143...connected.
fetchmail: IMAP< * OK [CAPABILITY IMAP4REV1 AUTH=LOGIN] IMAP4rev1 DavMail 3.9.7-1870 server ready
fetchmail: IMAP> A0001 CAPABILITY
fetchmail: IMAP< * CAPABILITY IMAP4REV1 AUTH=LOGIN
fetchmail: IMAP< A0001 OK CAPABILITY completed
fetchmail: Protocol identified as IMAP4 rev 1
fetchmail: GSSAPI error gss_inquire_cred: Unspecified GSS failure.  Minor code may provide more information
fetchmail: GSSAPI error gss_inquire_cred:
fetchmail: No suitable GSSAPI credentials found. Skipping GSSAPI authentication.
fetchmail: If you want to use GSSAPI, you need credentials first, possibly from kinit.
fetchmail: IMAP> A0002 LOGIN "domain\\user" *
fetchmail: IMAP< A0002 OK Authenticated
fetchmail: selecting or re-polling default folder
fetchmail: IMAP> A0003 SELECT "INBOX"
fetchmail: IMAP< * 1 EXISTS
fetchmail: IMAP< * 1 RECENT
fetchmail: IMAP< * OK [UIDVALIDITY 1]
fetchmail: IMAP< * OK [UIDNEXT 344]
fetchmail: IMAP< * FLAGS (\Answered \Deleted \Draft \Flagged \Seen $Forwarded Junk)
fetchmail: IMAP< * OK [PERMANENTFLAGS (\Answered \Deleted \Draft \Flagged \Seen $Forwarded Junk)]
fetchmail: IMAP< A0003 OK [READ-WRITE] SELECT completed
fetchmail: 1 message waiting after first poll
fetchmail: IMAP> A0004 EXPUNGE
fetchmail: IMAP< A0004 OK EXPUNGE completed
fetchmail: 1 message waiting after expunge
fetchmail: IMAP> A0005 SEARCH UNSEEN
fetchmail: IMAP< * SEARCH 1
fetchmail: 1 is unseen
fetchmail: IMAP< A0005 OK SEARCH completed
fetchmail: 1 is first unseen
1 message for domain\user at localhost.
fetchmail: IMAP> A0006 FETCH 1 RFC822.SIZE
fetchmail: IMAP< * 1 FETCH (UID 343 RFC822.SIZE 1350)
fetchmail: IMAP< A0006 OK FETCH completed
fetchmail: IMAP> A0007 FETCH 1 RFC822.HEADER
fetchmail: IMAP< * 1 FETCH (UID 343 RFC822.HEADER  {1350}
reading message domain\user@localhost:1 of 1 (1350 header octets) fetchmail: about to deliver with: /usr/bin/procmail -f 'my.name@domain.com' -d 'root'
#
fetchmail: IMAP<
fetchmail: IMAP<
fetchmail: IMAP< Bonne journ=E9e..
fetchmail: IMAP<
fetchmail: IMAP< Company Name
fetchmail: IMAP< My Name
fetchmail: IMAP< IT
fetchmail: IMAP< Tel: (XXX) XXX-XXXX xXXX
fetchmail: IMAP< www.domain.com=20
fetchmail: IMAP<
fetchmail: IMAP<
fetchmail: IMAP< -----Message d'origine-----
fetchmail: IMAP< De=A0: User [mailto:user@domain.com]=20
fetchmail: IMAP< Envoy=E9=A0: 2 juillet 2012 15:50
fetchmail: IMAP< =C0=A0: Informatique
fetchmail: IMAP< Objet=A0: PROBLEM: photo
fetchmail: IMAP<
fetchmail: IMAP< Notification Type: PROBLEM
fetchmail: IMAP< Author:=20
fetchmail: IMAP< Comment:=20
fetchmail: IMAP<
fetchmail: IMAP< Host: Photos
fetchmail: IMAP< Hostname: photo
fetchmail: IMAP< State: DOWN
fetchmail: IMAP< Address: XXX.XX.X.XX
fetchmail: IMAP<
fetchmail: IMAP< Date/Time: Mon Jul 2 15:49:38 EDT 2012
fetchmail: IMAP<
fetchmail: IMAP< Info: CRITICAL - XXX.XX.X.XX: rta nan, lost 100%
fetchmail: IMAP<
fetchmail: IMAP<
fetchmail: IMAP< )
fetchmail: IMAP< A0007 OK FETCH completed
fetchmail: IMAP> A0008 FETCH 1 BODY.PEEK[TEXT]
fetchmail: IMAP< * 1 FETCH (UID 343 BODY[TEXT] {539}
 (539 body octets) *******************************
fetchmail: IMAP< )
fetchmail: IMAP< A0008 OK FETCH completed
 flushed
fetchmail: IMAP> A0009 STORE 1 +FLAGS (\Seen \Deleted)
fetchmail: IMAP< * 1 FETCH (UID 343 FLAGS (\Seen \Deleted))
fetchmail: IMAP< * 1 EXPUNGE
fetchmail: IMAP< A0009 OK STORE completed
fetchmail: IMAP> A0010 EXPUNGE
fetchmail: IMAP< A0010 OK EXPUNGE completed
fetchmail: mail expunge mismatch (0 actual != 1 expected)
fetchmail: IMAP> A0011 LOGOUT
fetchmail: IMAP< * BYE Closing connection
fetchmail: IMAP< A0011 OK LOGOUT completed
fetchmail: client/server synchronization error while fetching from domain\user@localhost
fetchmail: 6.3.19 querying localhost (protocol IMAP) at Tue 03 Jul 2012 09:46:36 AM EDT: poll completed
Merged UID list from localhost: <empty>
fetchmail: Query status=7 (ERROR)
fetchmail: normal termination, status 7
```

---

### Post by cipherboy_loc on 2012-07-03
Have you reset the permissions on your home folder yet, to see if it helps?

---

### Post by OpEn_SoUrCe_RoCkS on 2012-07-03
How would I do that? I wasn't aware that there's a command to reset permissions..

---

### Post by cipherboy_loc on 2012-07-03
This blog has a tutorial on how to do it. There isn't a command you use, but a series of commands. But to actually change the permissions, chmod/chown. 
[URL="http://timwise.blogspot.com/2008/08/reseting-home-folder-permissions-in.html"]
http://timwise.blogspot.com/2008/08/reseting-home-folder-permissions-in.html[/URL]

---

### Post by OpEn_SoUrCe_RoCkS on 2012-07-03
Well, I just did this, and no cigar.

I still get the same errors.

---

