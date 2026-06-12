---
title: "LDAP setup &quot;Ich habe keinen Benutzernamen&quot;"
date: 2011-01-31
forum: General Help
---

### Post by natomb on 2011-01-31
Hello,

I was setup my ldap-server again. While I am quite sure to follow the same steps like last time, I get the following message from the prompt:

Ich habe keinen Benutzernamen!@vSonne:~$

It means something like "I do not have a username". Yet, I can login and execute some commands (vi, ls, ...) . "whoami" returns "whoami: Es ist kein Name zur Nutzer&#8208;ID 5001 zu finden". Thus, I would expect that something went wrong in letting the different tools use the LDAP.

As I have only the german version I could not find any relevant information (just one person who had moved his /etc).

Did you have this problem? How have you solved it?

Thank you very much
  Bjoern

---

### Post by natomb on 2011-02-27
Hi,

problem solved. The cause were too restrictive ACL definitions. After sticking strictly with the "tutorial", everything works now. Yet, because my LDAP is more open than I wanted, I will not make it accessible to the Internet as address book.

Cheers,
  Bjoern

---

