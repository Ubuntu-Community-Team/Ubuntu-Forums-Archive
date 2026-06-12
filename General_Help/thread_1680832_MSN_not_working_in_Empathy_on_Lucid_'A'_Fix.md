---
title: "MSN not working in Empathy on Lucid 'A' Fix"
date: 2011-02-03
forum: General Help
---

### Post by Fenris_rising on 2011-02-03
Hi All

I have just upgraded to Lucid and very pleased I am to.

One issue I had was the Empathy app. It wouldn't work with MSN at all. No contact list, wouldn't connect and in fact it kept telling me I was connected elsewhere.

After about an hour of googling I found an answer which has solved my problem. I hope it works for some or all of those who have a similar issue.

Here's the link -

[http://digitizor.com/2010/10/23/how-to-fix-the-msn-bug-in-empathy-ubuntu-10-10/](http://digitizor.com/2010/10/23/how-to-fix-the-msn-bug-in-empathy-ubuntu-10-10/)

The article has this line to use first. I have corrected it here as on the page the / is missing before usr.

```
gksudo gedit /usr/share/pyshared/papyon/service/description/SingleSignOn/RequestMultipleSecurityTokens.py
```

Look for a line very similar to this -

```
CONTACTS = ("contacts.msn.com", "?fs=1&id=24000&kv=7&rn=93S9SWWw&tw=0&ver=2.1.6000.1")
```

Change it to this -

```
CONTACTS = ("contacts.msn.com", "MBI")
```

regards

Fenris

---

### Post by irv on 2011-02-04
Why don't you mark this thread solved.

---

