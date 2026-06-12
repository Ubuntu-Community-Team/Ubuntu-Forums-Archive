---
title: "ssh authentication: key &amp; password mix"
date: 2011-07-25
forum: General Help
---

### Post by pieroxy on 2011-07-25
Hello,

I am running a small ubuntu-server headless machine at home. It is configured with sshd so that I can connect from anywhere (if I have Internet access.)

However, there is a thing: I'd like to have good security and disable password authentication, but I also want to be able to connect from a PC that I've never touched before. And no, I'm not prepared to type a 256 bytes password every time I type "sudo ..."

Here is what I thought: I could have a login (pieroxy) that has a moderately strong password and another user (pieroxy-ext) that has a very strong password (100+ chars.) I would use my regular account (pieroxy) whenever I have a key-based authentication and the other one (pieroxy-ext) whenever I have a password-based authentication to do. Then, I'll just su to "pieroxy" and I'm done typing the 100 chars pwd. 

In order to do that, I would need to be able to configure my machine so that password-based authentication is disabled for all accounts but enabled for my account that has a strong password (pieroxy-ext). Is it possible to disable password-based authentication on a user basis?

---

### Post by galvatron408 on 2011-07-25
of course you can...
[http://stackoverflow.com/questions/4241197/how-to-disable-password-authentication-for-every-users-except-several](http://stackoverflow.com/questions/4241197/how-to-disable-password-authentication-for-every-users-except-several)

---

### Post by pieroxy on 2011-07-26
Thanks, it looks great. I'll try that as soon as I'm home !

---

