---
title: "Cannot connect Google / Gmail"
date: 2009-11-30
forum: General Help
---

### Post by danp451 on 2009-11-30
Hi All,

About a week ago I stopped being able to connect to Gmail. I'm using Jaunty and Firefox 3.0.15 (upgraded today to 3.5 and still no luck) and connecting on Vodafone's mobile broadband.

I can see other sites including Google but when I go to Gmail (or Calendars etc. I've now discovered) I get as far as the message 'Waiting for Google.com...' in the bottom left corner and that's it.

Am I blocking access from Ubuntu somehow and if so how can I find out / rectify?

All help welcome.

Dan
p.s. sorry if this is a duplicate my original message seemed to get lost.

---

### Post by solitaire on 2009-11-30
try :
[https://mail.google.com/mail/?ui=html&zy=a](https://mail.google.com/mail/?ui=html&zy=a)   (basic HTML mode)
or
[https://mail.google.com/mail/?ui=1](https://mail.google.com/mail/?ui=1) (origional Gmail pages)
See if those work...

---

### Post by danp451 on 2009-11-30
Hi,

Unofortunately not. Still 'Waiting for Google...' on both.

D.

---

### Post by john newbuntu on 2009-11-30
Open up a terminal.  Applications->accessories->terminal.  Type:
ping [www.google.com](www.google.com)
and see if you are able to send and receive packets.  If so, your network connection is most likely ok.

---

### Post by danp451 on 2009-11-30
I can ping [www.google.com](www.google.com) and gmail.com and various other permutations but still no joy. 

I read someone talking about latex having broken packages.......I'd have to look more into that but any ideas further?

D.

---

### Post by cdenley on 2009-11-30
Post this output.
```

echo -e "GET /mail/ HTTP/1.0\nHost: mail.google.com\n"|nc -v mail.google.com 80

```

---

### Post by danp451 on 2009-11-30
Here you go. I have to say I'm reliant on you for interpretation......




```
dan@dan-laptop:~$ echo -e "GET /mail/ HTTP/1.0\nHost: mail.google.com\n"|nc -v mail.google.com 80
DNS fwd/rev mismatch: googlemail.l.google.com != ww-in-f83.1e100.net
DNS fwd/rev mismatch: googlemail.l.google.com != ww-in-f17.1e100.net
DNS fwd/rev mismatch: googlemail.l.google.com != ww-in-f18.1e100.net
DNS fwd/rev mismatch: googlemail.l.google.com != ww-in-f19.1e100.net
googlemail.l.google.com [209.85.229.83] 80 (www) open
HTTP/1.0 302 Moved Temporarily
Connection: close
Content-Type: text/html; charset=UTF-8
Content-Length: 408
Cache-Control: no-cache, no-store, max-age=0, must-revalidate
Date: Mon, 30 Nov 2009 15:52:34 GMT
Expires: Fri, 01 Jan 1990 00:00:00 GMT
Location: https://www.google.com/accounts/ServiceLogin?service=mail&passive=true&rm=false&continue=http%3A%2F%2Fmail.google.com%2Fmail%2F%3Fui%3Dhtml%26zy%3Dl&bsv=zpwhtygjntrz&scc=1&ltmpl=default&ltmplcache=2
Pragma: no-cache
Server: GFE/2.0
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 0

<HTML>
<HEAD>
<TITLE>Moved Temporarily</TITLE>
</HEAD>
<BODY BGCOLOR="#FFFFFF" TEXT="#000000">
<H1>Moved Temporarily</H1>
The document has moved <A HREF="https://www.google.com/accounts/ServiceLogin?service=mail&amp;passive=true&amp;rm=false&amp;continue=http%3A%2F%2Fmail.google.com%2Fmail%2F%3Fui%3Dhtml%26zy%3Dl&amp;bsv=zpwhtygjntrz&amp;scc=1&amp;ltmpl=default&amp;ltmplcache=2">here</A>.
</BODY>
</HTML>
dan@dan-laptop:~$ 
```

---

