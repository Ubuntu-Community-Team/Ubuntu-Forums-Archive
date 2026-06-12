---
title: "ssh permission denied"
date: 2012-06-24
forum: General Help
---

### Post by EddievV on 2012-06-24
Hello all,

I use ssh to connect my Ubuntu-PC to an audio streamer (Logitech Touch). _Worked fine until yesterday_! After typing the password I get: Permission denied, please try again.

Part of the debug information:
debug1: Connecting to 192.168.0.100 [192.168.0.100] port 22.
debug1: Connection established.
...
debug1: Trying private key: /root/.ssh/id_dsa
debug1: Next authentication method: password
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.

I looked in /var/log/auth.log, that doesn't say anything to me.

I tried this suggestion:
"Next, try logging in from your own computer: 
ssh -v localhost
This will print a lot of debugging information, and will try to connect to your SSH server. You should be prompted to type your password."
No prompt showed up, the only information I got is 'connection refused'.

Any suggestions on how to solve this? (Besides installing the latest Ubuntu version, I still run 9.10 because I got sick of all the trouble I had with the updates every half year).

Kind regards, Eddie

---

### Post by EddievV on 2012-07-01
Hello all,

A test with connecting to a Linux server showed that my ssh worked fine. So the problem was in the Logitech Touch and was 'solved' with a factory reset. 

Kind regards, Eddie

---

