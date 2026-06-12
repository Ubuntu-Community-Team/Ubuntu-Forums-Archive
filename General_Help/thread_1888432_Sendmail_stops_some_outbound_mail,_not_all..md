---
title: "Sendmail stops some outbound mail, not all."
date: 2011-11-29
forum: General Help
---

### Post by DurhamDev on 2011-11-29
Hi everyone,

I think I have a problem that is probably extremely simple to fix. I'm pretty sure the answer is staring me right in the face.

I have configured a Server that's been working well for months as a LAMP Server (I serve web pages up just fine) and have just installed POSTFIX using the following command...

```
sudo apt-get install postfix mailutils
```

...after which, I tested it with the following command...

```
echo "hello world, my email works!" | sendmail -v email@domainname.com
```

..and it worked GREAT!  (Sort of.)  Here's my dilemma.  My Server is configured with a Host name of (for example) "abcwidgets.com".  When I use the command to send E-Mail to any address that DOESN'T end with my Domain Name, they go through perfectly.  When I use the command above to send E-Mail to "bob.jones@abcwidgets.com", I find errors when I use the MAIL command, as it says there is "no such user".

TL;DR / clarification: If I send to "bob.jones@gmail.com", my E-Mail sends.  If I send to "bob.jones@abcwidgets.com", it does not leave the server.

I call upon the Ubuntu Gods to hopefully tell me what I am doing wrong, or how I may fix my problem!  I simply need my Server to send out the E-Mail that it recognizes as the same domain, and not hold onto it, because it thinks it's doing me a favour.

Thanks, in advance!

Rick

---

