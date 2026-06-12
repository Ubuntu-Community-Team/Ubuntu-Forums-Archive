---
title: "mutt on 10.4 will not work"
date: 2012-04-01
forum: General Help
---

### Post by cssutto on 2012-04-01
I have used mutt for several years now and have had all of my muttrc, fetchmailrc, msmtprc files, etc., properly configured.

So I bought a new HP Pavillion 64 bit and I can not get mutt to run on it at all.

Even fetchmaii, which should run on the command line, gives me the permission denied message.

I have looked at all permissions and made them all exc files with zero results.

Does anyone have any suggestions?

My old machine also runs on 10.4.

---

### Post by andrew.46 on 2012-04-02
Could you post the permissions on your ~/.fetchmailrc? My own is:

```

andrew@skamandros~$ **[COLOR="Red"]ls -l ~/.fetchmailrc [/COLOR]**
-rw------- 1 andrew users 866 Jun 12  2011 /home/andrew/.fetchmailrc

```

and I guess also the result of:

```

andrew@skamandros~$ **[COLOR="Red"]echo $USER[/COLOR]**
andrew

```

Hopefully this will not be too hard to fix up.....

---

### Post by cssutto on 2012-04-02
claude@ubuntu:~$ ls -l ~/.fetchmailrc 
-rw------- 1 claude claude 830 2012-03-25 16:29 /home/claude/.fetchmailrc
claude@ubuntu:~$ 
claude@ubuntu:~$ echo suser
suser
claude@ubuntu:~$

---

### Post by zombifier25 on 2012-04-02
> **cssutto said:**
> claude@ubuntu:~$ ls -l ~/.fetchmailrc 
-rw------- 1 claude claude 830 2012-03-25 16:29 /home/claude/.fetchmailrc
claude@ubuntu:~$ 
claude@ubuntu:~$ echo suser
suser
claude@ubuntu:~$
No, it's
```
echo $USER
```
not```
echo suser
```
Pay attention to the spelling.

---

### Post by cssutto on 2012-04-02
I have some eye problems.  

Cataracts and macular degeneration in one eye.


claude@ubuntu:~$ echo $USER
claude
claude@ubuntu:~$

---

### Post by andrew.46 on 2012-04-02
Your permissions look ok. What do you see when you run:
```

fetchmail -vvv
```

If your eyesight is a problem just copy and paste the command. On my own system this is the result:

```

andrew@skamandros~$ **[COLOR="Red"]fetchmail -vvv[/COLOR]**
Old UID list from pop.gmail.com: <empty>
Old UID list from mail.aapt.net.au: <empty>
Old UID list from mail.une.edu.au: <empty>
Scratch list of UIDs: <empty>
fetchmail: 6.3.20 querying pop.gmail.com (protocol POP3) at Tue 03 Apr 2012 06:44:14 AM EST: poll started
Trying to connect to 173.194.79.108/995...connected.
fetchmail: Certificate chain, from root to peer, starting at depth 2:
fetchmail: Issuer Organization: Equifax
fetchmail: Unknown Issuer CommonName
fetchmail: Certificate at depth 1:
fetchmail: Issuer Organization: Equifax
fetchmail: Unknown Issuer CommonName
fetchmail: Subject CommonName: Google Internet Authority
fetchmail: Server certificate:
fetchmail: Issuer Organization: Google Inc
fetchmail: Issuer CommonName: Google Internet Authority
fetchmail: Subject CommonName: pop.gmail.com
fetchmail: pop.gmail.com key fingerprint: B8:AF:A7:80:CD:E2:31:50:6F:ED:0E:4F:C8:04:D6:CD
fetchmail: POP3< +OK Gpop ready for requests from 124.168.132.215 q5pf21484907pbh.7
fetchmail: POP3> CAPA
fetchmail: POP3< +OK Capability list follows
fetchmail: POP3< USER
fetchmail: POP3< RESP-CODES
fetchmail: POP3< EXPIRE 0
fetchmail: POP3< LOGIN-DELAY 300
fetchmail: POP3< TOP
fetchmail: POP3< UIDL
fetchmail: POP3< X-GOOGLE-VERHOEVEN
fetchmail: POP3< X-GOOGLE-RICO
fetchmail: POP3< .
fetchmail: POP3> USER andrew@andrews-corner.org
fetchmail: POP3< +OK send PASS
fetchmail: POP3> PASS *
fetchmail: POP3< +OK Welcome.
fetchmail: selecting or re-polling default folder
fetchmail: POP3> STAT
fetchmail: POP3< +OK 0 0
fetchmail: No mail for andrew@andrews-corner.org at pop.gmail.com
fetchmail: POP3> QUIT
fetchmail: POP3< +OK Farewell.
fetchmail: 6.3.20 querying pop.gmail.com (protocol POP3) at Tue 03 Apr 2012 06:44:16 AM EST: poll completed
New UID list from pop.gmail.com: <empty>
fetchmail: not swapping UID lists, no UIDs seen this query
fetchmail: Query status=1 (NOMAIL)
fetchmail: 6.3.20 querying mail.aapt.net.au (protocol POP3) at Tue 03 Apr 2012 06:44:16 AM EST: poll started
Trying to connect to 210.10.73.252/110...connected.
fetchmail: POP3< +OK POP3 Ready pfep03
fetchmail: POP3> CAPA
fetchmail: POP3< -ERR Command must be one of USER, PASS or QUIT
fetchmail: Command must be one of USER, PASS or QUIT
fetchmail: Repoll immediately on adjlstrong@aapt.net.au@mail.aapt.net.au
Trying to connect to 210.10.73.252/110...connected.
fetchmail: POP3< +OK POP3 Ready pfep02 000132ed
fetchmail: POP3> USER adjlstrong@aapt.net.au
fetchmail: POP3< +OK USER adjlstrong@aapt.net.au set, mate
fetchmail: POP3> PASS *
fetchmail: POP3< +OK Maildrop locked and ready
fetchmail: selecting or re-polling default folder
fetchmail: POP3> STAT
fetchmail: POP3< +OK 0 0
fetchmail: No mail for adjlstrong@aapt.net.au at mail.aapt.net.au
fetchmail: POP3> QUIT
fetchmail: POP3< +OK
fetchmail: 6.3.20 querying mail.aapt.net.au (protocol POP3) at Tue 03 Apr 2012 06:44:20 AM EST: poll completed
New UID list from mail.aapt.net.au: <empty>
fetchmail: not swapping UID lists, no UIDs seen this query
fetchmail: Query status=1 (NOMAIL)
fetchmail: 6.3.20 querying mail.une.edu.au (protocol POP3) at Tue 03 Apr 2012 06:44:20 AM EST: poll started
Trying to connect to 129.180.3.51/110...connected.
fetchmail: POP3< +OK Hello there.
fetchmail: POP3> CAPA
fetchmail: POP3< +OK Here's what I can do:
fetchmail: POP3< TOP
fetchmail: POP3< USER
fetchmail: POP3< LOGIN-DELAY 10
fetchmail: POP3< PIPELINING
fetchmail: POP3< UIDL
fetchmail: POP3< IMPLEMENTATION Courier Mail Server
fetchmail: POP3< .
fetchmail: POP3> USER astrong3
fetchmail: POP3< +OK Password required.
fetchmail: POP3> PASS *
fetchmail: POP3< +OK logged in.
fetchmail: selecting or re-polling default folder
fetchmail: POP3> STAT
fetchmail: POP3< +OK 0 0
fetchmail: No mail for astrong3 at mail.une.edu.au
fetchmail: POP3> QUIT
fetchmail: POP3< +OK Bye-bye.
fetchmail: 6.3.20 querying mail.une.edu.au (protocol POP3) at Tue 03 Apr 2012 06:44:20 AM EST: poll completed
New UID list from mail.une.edu.au: <empty>
fetchmail: not swapping UID lists, no UIDs seen this query
fetchmail: Query status=1 (NOMAIL)
fetchmail: normal termination, status 1


```

This successfully checks 3 mailboxes but no mail :(.

---

### Post by cssutto on 2012-04-02
claude@ubuntu:~$ fetchmail -vvv
bash: /usr/bin/fetchmail: Permission denied
claude@ubuntu:~$ 


Same old thing.

---

### Post by andrew.46 on 2012-04-02
Interesting. What go you have for:

```

andrew@skamandros~$ **[COLOR="Red"]ls -l /usr/bin/fetchmail[/COLOR]**
-rwxr-xr-x 1 root root 251456 Jun 18  2011 /usr/bin/fetchmail

```

---

