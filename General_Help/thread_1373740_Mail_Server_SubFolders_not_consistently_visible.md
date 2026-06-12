---
title: "Mail Server SubFolders not consistently visible"
date: 2010-01-06
forum: General Help
---

### Post by Dougga on 2010-01-06
I have a mail server running ubuntu 9.04 w/ the default setup (for the most part): Postfix + Dovecot + SSL.

I generally use Ubuntu 9.10 as the client machine running evolution.
I have a myriad of subfolders to the inbox on the server that I created in Evolution.

Occassionally I do connect using another machine and use IMAP.  In one instance I use the Windows 7 I have on the same machine (dual boot) and access the server.  Most of the server's sub-folders are not visible but many are.

This is very odd behavior.

I'd like to understand what is going on and how I might fix the problem.
My own searches have not helped much.
Thanks in advance.
:confused:

---

### Post by HermanAB on 2010-01-06
Howdy,

Folders is an IMAP feature (therefore Dovecot), but there are different versions of IMAP and some clients support only subsets.  So, the trick is to use the same mail client everywhere, eg Thunderbird.  Outlook is not cross platform so you should expect trouble with that one.

---

### Post by Dougga on 2010-01-06
> **HermanAB said:**
> Howdy,

Folders is an IMAP feature (therefore Dovecot), but there are different versions of IMAP and some clients support only subsets.  So, the trick is to use the same mail client everywhere, eg Thunderbird.  Outlook is not cross platform so you should expect trouble with that one.

Interesting (and slightly annoying).
I'll look into various clients to see the differences.
Thanks for the tip.

---

