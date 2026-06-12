---
title: "Thunderbird doesn't fetch all mail"
date: 2006-06-08
forum: General Help
---

### Post by marwal on 2006-06-08
Recently thunderbird doesnt indicate some of the mail on the server. When i use my webbmail i see new and unread mail but thunderbird won't fetch them.
I setup thunderbird to only fetch headlines and have some rulesets for mail it should download in full.
But that's not the problem 'cause not even the headlines show up on these mails.

Does anybody have the faintest idea what this could be, i would really appreciate it.=D>

---

### Post by bvanaerde on 2006-06-08
This may not be relevant at all, but... it just might :)
I noticed that when you send exactly the same e-mail multiple times, Thunderbird sees them as one.

I tested this right now on Thunderbird (on WindowsXP, as I'm at work atm).
Maybe it does the same thing on "ubuntu thunderbird"...

---

### Post by marwal on 2006-06-09
*bump*
it's really annoying having a semi-functional mozilla-thunderbird

---

### Post by marwal on 2006-06-12
OK, i've traced the traffic with ethereal.

 There is the HELO, USER and PASSWORD
it asks for STAT and gets a response : +OK  3 31125 for one account
and +OK 4 81738 for the other.

Then there is the LIST request :

REQEST: LIST
[TCP Retransmission] Request: LIST
[TCP Previous segment lost] pop3 > 58978 [AC] Seq=267 ...
[TCP Out-Of-Order] Response: +OK ...
Request: UIDL
pop3 > 58978 [ACK] Seq=267 ...
Response: +OK
Request: QUIT
Response: +OK Bye-bye.

And NO mail is fetched.
I don't understand what's going on here. Do you?

---

### Post by vespo on 2006-06-12
Hi

Is it a @gmail.com address?

If yes, your problem has to do with google mail threading messages and NOT broken thunderbird.
If not at gmail, please ignore what I just said.

Hope this helps
vespo

---

### Post by asimon on 2006-06-12
Is this about checking mails in all folders from an IMAP account?
If yes, then see [Check all IMAP folders for new mail](http://www.mozilla.org/support/thunderbird/tips#beh_downloadstartup).

---

### Post by marwal on 2006-06-12
No, it's not g-mail and it's not IMAP.
It's a pop3 account.
Thunderbird says "downloading 3 messages" and dont.

I setup evolution with the same pop and smtp settings and it works dandy (just as thunderbird did a while back).

There's no firewall settings that would intefer with ports 2525 (used because my ISP won't allow port 25 - this is not part of the problem) and 110

Thunderbird is also fetching one mail over and over again. It is never flagged fetched and deleted from server.

---

### Post by vespo on 2006-06-12
[QUOTE=marwal]No, it's not g-mail and it's not IMAP.
It's a pop3 account.
Thunderbird says "downloading 3 messages" and dont.

I setup evolution with the same pop and smtp settings and it works dandy (just as thunderbird did a while back).

There's no firewall settings that would intefer with ports 2525 (used because my ISP won't allow port 25 - this is not part of the problem) and 110

Thunderbird is also fetching one mail over and over again. It is never flagged fetched and deleted from server.[/QUOTE]


Allright, well I was thinking you were possibly using gmail pop3 feature but appearently you are not. 

Just one more stupid thought and then I stop: is the size of your three messages less then, let's say a few Mbs and are you not connecting with 56k phone line? It happened to me once, a message was recognised as new but it never dowloaded. It later turned out to be 15 Mb of nice holyday pictures from a mate... obviously it is not your case since evolution works fine with the very same messages.

Cheers

---

