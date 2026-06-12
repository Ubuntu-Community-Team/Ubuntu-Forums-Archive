---
title: "Ubuntu boot.log error"
date: 2010-09-28
forum: General Help
---

### Post by martinlall on 2010-09-28
Hi all,

I've got this in my boot.log file.
I searched for sulution, but it seems to be quite rare problem.

```
/etc/rc2.d/S99lookup-domain: 21: /usr/share/webmin/virtual-server/lookup-domain$
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service S99mysql start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start S99mysql
start: Unknown job: S99mysql

```
How to fix it?

---

### Post by martinlall on 2010-09-30
Really no one has any idea what the webmin error is and how to get rid of it?

---

### Post by martinlall on 2010-10-01
As it has become common for my posts, I'll answer to the question for myself.
**update-rc.d -f mysql remove** fixed the problem.

---

### Post by sikander3786 on 2010-10-01
> **martinlall said:**
> As it has become common for my posts, I'll answer to the question for myself.
**update-rc.d -f mysql remove** fixed the problem.
You are a geek yourself :-) Do you really need help from the forums?

Sometimes the problems appear to be geeky and no one really knows an answer to them. So Google is your best friend then. For current problem,

[http://www.google.com/search?client=ubuntu&channel=fs&q=%2Fusr%2Fshare%2Fwebmin%2Fvirtual-server%2Flookup-domain%24&ie=utf-8&oe=utf-8#hl=en&q=+site:ubuntuforums.org+Since+the+script+you+are+attempting+to+invoke+has+been+converted+to+an+Upstart+job,+you+may+also+use+the+start%288%29+utility&sa=X&ei=5nalTMXFCoHKvQPgwfj2DA&ved=0CBcQrQIwAA&fp=c6affe93747c32d0](http://www.google.com/search?client=ubuntu&channel=fs&q=%2Fusr%2Fshare%2Fwebmin%2Fvirtual-server%2Flookup-domain%24&ie=utf-8&oe=utf-8#hl=en&q=+site:ubuntuforums.org+Since+the+script+you+are+attempting+to+invoke+has+been+converted+to+an+Upstart+job,+you+may+also+use+the+start%288%29+utility&sa=X&ei=5nalTMXFCoHKvQPgwfj2DA&ved=0CBcQrQIwAA&fp=c6affe93747c32d0)

You solved it anyways.

Happy Ubuntu-ing !

---

### Post by martinlall on 2010-10-01
Hi,

You know, sometimes when you try to figure something out, you'll miss the key to solution that has always been in front of your eyes.

I was tracing "S99mysql" but should have been looking for rc.d common errors as you said (S99 is rc.d's, not for mysql's)

Both of those errors on that log file were caused by virtualmin removal. My sql server runs fine, even after remoing the dead link from rc.d

Thank you for your support.

---

