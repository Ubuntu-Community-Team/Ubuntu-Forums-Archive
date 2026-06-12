---
title: "SSH Setup - Few Small Issues"
date: 2010-11-01
forum: General Help
---

### Post by Nanyak on 2010-11-01
Hi all,
 
This is my first venture into CLI linux, only being playing around with it for a day, so my apologies in advance. Also, sorry if I have posted in the wrong forum. 
 
I have jumped straight into building a server running Ubuntu Server 10.04. I spent a significant part of today getting SSH up and running.
 
After a bit of reading I saw that 'securing' ssh is very important. So I did the following:
-changed the port from 22 to something less common
-disabled root login 
-used a authentication keys to login instead of passwords
 
Now I want to 'ssh' my ubuntu server through my windows7 pc. So I am running putty. I managed to generate the keys on ubuntu (which putty recognised) and all is well. Now when I ssh my server it asks me for the passphrase and not my username and login (which is exactly what I want) 
 
To be more secure, I have read that I should disable the ability to gain 'ssh access' through username and password. So I edited the config file: /etc/ssh/sshd_config
 
> 
# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes
# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no
# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no
# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication no
# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

 
So, now come my questions:
 
**1)**The above does not seemed to have worked. I can open another instance of putty and still log in using my username and password (and not have to use the key). So I was hoping that someone here could see what I am doing wrong?
**2)**Also, for shits and giggles, I downloaded and installed winSCP on my PC to see whether I would be able to log in using username and password...and just like before I was able to log into the server.Should the above edit to the config file have fixed this? 
**3)**This one may be a silly question. When I am on the home network and I want to specify to Putty the destination that I want to connect to, I just enter the static ip that I have given the server. What would I need to do if I wanted to access this server from another network? (e.g. a friends house, work etc)
**4)**Finally by using winSCP I was actually able to get access to the authorized_keys file in the .ssh directory and open it up. Should I be concerened by this? How can I secure this file and prevent it from being viewed?

---

### Post by eric_1982 on 2010-11-01
Just a quick question, have you restarted the ssh server since you made the changes?

sudo /etc/init.d/ssh restart

---

### Post by gmargo on 2010-11-01
Make sure you have "UsePAM no" in your sshd_config.

---

### Post by efflandt on 2010-11-01
Any line that begins with # is generally considered a comment in config files and scripts, so the following is ignored

#PasswordAuthentication no

Remove the # so it reads:

PasswordAuthentication no

Connecting from the internet works best if you get some sort of dynamic DNS to point a fixed name to your public IP (even if dynamic).  And then, unless your Linux box is directly connected to a cable modem, you likely need to port forward the port you set up for ssh though your router to private IP of your server.  I have used no-ip.com for dynamic DNS for many years, but web search "dns hosting" for others.  Subdomains of theirs are free.

When you connect with ssh (or scp, etc.) you should have access to anything that user has access to.  Your ~/.ssh directory should have 700 permission drwx------, and files in it should have 600 permission -rw-------.  But "you" can still access them as that user.

---

### Post by blueridgedog on 2010-11-01
And don't forget to restart the service after the changes...

---

### Post by gordintoronto on 2010-11-01
One more thing about access via the Internet: you will need to set up "port forwarding" on your router.

---

### Post by Nanyak on 2010-11-01
Thanks everyone for the replies. I can't believe I missed the # on the config file. Everything is working now, cannot login with username and password. Its great not having to have another monitor and keyboard and keep running backwards and forwards from my ubuntu server. 
 
I will have a look into port forwarding. 
 
I used chmod 600 on the keys file and chmod 700 on the folder. Then used ls -l on ~/.ssh and it said that the permissions on the authorized_keys file was -rw. So I believe that that has worked now as well. 
 
 
Thanks for all your help.

---

