---
title: "SSH to Remote Server with Alternate Port"
date: 2012-06-14
forum: General Help
---

### Post by nielsenrc on 2012-06-14
Probably something simple (stupid) but I hope someone here can help:

I have a brand new totally clean install of Ubuntu 12.04 LTS

I need to ssh to a server that uses port 76 for ssh.

Syntax: ssh -p xx [email]user@site.com[/email]

If I do this it will pause for a long time and then eventually ask for my password - when I enter the password it just says Connection closed by [ip]

I can ssh just fine in Ubuntu for remote servers that use the standard port - but not for this server with the alternate port. 

I can do this just fine on my Macbook - so it's not a networking issue. Is there something I need to configure within Ubuntu for it to properly SSH into machines using an alternate port?

---

### Post by papibe on 2012-06-14
Hi nielsenrc.

I use alternative ports without any problem. 

Could you post the log trying to connect using the triple verbose option:
```
ssh -vvv -p xx user@site.com
```
Regards.

---

### Post by kanikilu on 2012-06-14
**ssh -p 76 user@host** should work. Do you have any outbound ports blocked on your machine or at the gateway?

---

### Post by ajgreeny on 2012-06-14
Try deleting or renaming the **known_hosts** file in the hidden **.ssh** folder in your home.
```
mv /home/*user*/.ssh/known_hosts /home/*user*/.ssh/known_hostsbak
```

---

### Post by nielsenrc on 2012-06-14
Wow guys - thanks for the quick response:

AFAIK - It's not a network issue - the Macbook does this fine. I also moved the known_hosts file to no effect.

> **papibe said:**
> Hi nielsenrc.

I use alternative ports without any problem. 

Could you post the log trying to connect using the triple verbose option:
```
ssh -vvv -p xx user@site.com
```Regards.

Without blowing up this thread - here's the lines that stood out to me:

[B]debug1: Next authentication method: gssapi-with-mic
debug1: Unspecified GSS failure.  Minor code may provide more information
Credentials cache file '/tmp/krb5cc_1000' not found

debug1: Unspecified GSS failure.  Minor code may provide more information
Credentials cache file '/tmp/krb5cc_1000' not found

debug1: Unspecified GSS failure.  Minor code may provide more information


debug1: Unspecified GSS failure.  Minor code may provide more information
Credentials cache file '/tmp/krb5cc_1000' not found

debug2: we did not send a packet, disable method
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/ryan/.ssh/id_rsa
debug3: no such identity: /home/ryan/.ssh/id_rsa
debug1: Trying private key: /home/ryan/.ssh/id_dsa
debug3: no such identity: /home/ryan/.ssh/id_dsa
debug1: Trying private key: /home/ryan/.ssh/id_ecdsa
debug3: no such identity: /home/ryan/.ssh/id_ecdsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
[email]root@domain.net[/email]'s password: 
debug3: packet_send2: adding 48 (len 62 padlen 18 extra_pad 64)
debug2: we sent a password packet, wait for reply
Connection closed by [ip][/B]

---

### Post by nielsenrc on 2012-06-14
Well - it doesn't appear to be the port. I changed the SSh port on the remote server to standard and that had no impact. Pings also take forever - but ONLY for that remote server.

I'd chalk it up to the remote server except that my Macbook pings the server and SSHs just fine. It's limited exclusively to this new Ubuntu box.

---

### Post by kanikilu on 2012-06-14
I notice you are trying to SSH as root. Are you sure the sshd_config is setup to allow this on the server? I know you said "it works" from your Mac, but wasn't sure if you were trying as a different user, or what...?

Also, do you see anything useful in the logs on the server - assuming you can still log into it from another machine? You didn't specify, but if the server is Ubuntu, then you'd want to look in /var/log/auth.log. If RedHat based, I think it's /var/log/security, but it's been a while since I've used RH.

---

### Post by nielsenrc on 2012-06-14
Logging in as root on both the MacBook Pro and the Ubuntu box. Fails on Ubuntu - succeeds without problems on the Mac.

---

### Post by nielsenrc on 2012-06-14
The auth log didn't have any useful info in it - just indicates that I disconnected.

---

### Post by kanikilu on 2012-06-14
Does the connection get closed immediately, or does it take some time?

If it takes a while, another search brought up that sometimes ssh clients will timeout if the server is taking a long time to do a reverse DNS lookup. If you have access to change it, maybe try disabling that in the sshd_config.

[http://linux-tips.org/article/92/disabling-reverse-dns-lookups-in-ssh](http://linux-tips.org/article/92/disabling-reverse-dns-lookups-in-ssh)

Sorry, kind of grasping at straws here...don't really know what else to suggest :(

---

### Post by nielsenrc on 2012-06-14
OK solution found. 

Seems to be related to these issues and Centos and Ubuntu not playing well for some reason:

[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/416264](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/416264)
[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/84899](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/84899)

Fix (on the Ubuntu machine):

1) sudo vim /etc/ssh/ssh_config
2) Find 'GSSAPIAuthentication' and set to 'no'
3) Restart SSH (which I did by restarting Ubuntu)

Works like a charm now. Not sure why. 

**Question: Is this a bad thing to do? I really don't know.**

---

