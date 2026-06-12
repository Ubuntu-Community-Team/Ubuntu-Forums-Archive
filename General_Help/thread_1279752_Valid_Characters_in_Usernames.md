---
title: "Valid Characters in Usernames"
date: 2009-10-01
forum: General Help
---

### Post by Discus on 2009-10-01
Hi, 
I'm trying to use a split dns solution to enable seamless in/out of office email (see [http://ubuntuforums.org/showthread.php?p=8035058](http://ubuntuforums.org/showthread.php?p=8035058)). 

However, there is a small snag. The hosting company requires usernames to be the full email address of the user. These obviously contain "." and "@" characters. 

I seem to recall reading somewhere that using usernames that are not all lowercase, longer than about 8 characters and excluding any punctuation or odd characters was a bad idea. 

Would it be a problem to change the usernames on the local Ubuntu server (8.04) to email addresses, or is this not an issue in Ubuntu? Or are these kinds of problems application specific?  

I have tried creating such usernames and Ubuntu doesn't prevent it, but I'm loath to do this to actual user accounts in case it breaks anything important. 

Many thanks!

---

### Post by dcstar on 2009-10-02
> **Discus said:**
> Hi, 
I'm trying to use a split dns solution to enable seamless in/out of office email (see [http://ubuntuforums.org/showthread.php?p=8035058](http://ubuntuforums.org/showthread.php?p=8035058)). 

However, there is a small snag. The hosting company requires usernames to be the full email address of the user. These obviously contain "." and "@" characters. 

I seem to recall reading somewhere that using usernames that are not all lowercase, longer than about 8 characters and excluding any punctuation or odd characters was a bad idea. 

Would it be a problem to change the usernames on the local Ubuntu server (8.04) to email addresses, or is this not an issue in Ubuntu? Or are these kinds of problems application specific?  

I have tried creating such usernames and Ubuntu doesn't prevent it, but I'm loath to do this to actual user accounts in case it breaks anything important. 

Many thanks!

Having e-mail address usernames can cause problems as a Linux system using them will also append it's own "@domain-name.com" suffix.

For example, you can set up a username like: [email]joe.bloggs@this.domain.com[/email]", but if you use that to log into a system with the domain listed above, and then send an e-mail using the Linux system's MTA it will come out as:

"joe.bloggs@this.domain.com@domain-name.com"

If you don't use the Linux system's MTA, then you may be able to get away with it.

The bottom-line is that you are trying to get users to log into two totally different e-mail systems, and you should recognise that and actually set up two sets of credentials for the users - the actual e-mails can end up in the same place (depending on the e-mail client).

---

### Post by Discus on 2009-10-02
Many thanks dcstar, 

The problem is that end users are stupid and don't seem able to cope with having multiple accounts in their email clients - that's what I have configured at the moment!

---

