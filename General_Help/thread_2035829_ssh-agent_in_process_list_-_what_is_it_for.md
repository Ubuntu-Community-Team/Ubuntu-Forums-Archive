---
title: "ssh-agent in process list - what is it for?"
date: 2012-07-31
forum: General Help
---

### Post by MrsUser on 2012-07-31
Checking my process list today, I noticed that there is a process running called 'ssh-agent'. 

I found some Wikipedia information:
[http://en.wikipedia.org/wiki/Ssh-agent](http://en.wikipedia.org/wiki/Ssh-agent)

So, it stores the 'private key', it says on Wikipedia. But what private key are they talking about? What is it for? What does it on my system? And I'd like to know why it runs on startup. Is it needed?

Using Ubuntu 12.04 64-bit.

---

### Post by Slim Odds on 2012-07-31
It's only used if you use ssh.

It's a convenience feature so that you don't have to type your password every single time you use ssh.

---

