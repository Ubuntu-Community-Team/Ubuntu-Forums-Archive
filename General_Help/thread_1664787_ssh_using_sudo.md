---
title: "ssh using sudo?"
date: 2011-01-11
forum: General Help
---

### Post by garyed on 2011-01-11
Can anyone tell me how I can get my other computer to recognize me when I ssh to it using sudo. If I use the same command without sudo it works fine.
I have it set up so I don't need a password using the ssh-keygen method as myself.
but when I use sudo ssh .... I get:
> Please contact your system administrator.
Add correct host key in /root/.ssh/known_hosts to get rid of this message.
Offending key in /root/.ssh/known_hosts:4
RSA host key for ocean has changed and you have requested strict checking.
Host key verification failed.

I was thinking about logging in as root & doing the ssh-keygen method  
& was wondering if that would generate files in /root/.ssh instead of ~/.ssh. I don't want to do anything as root until I'm sure it won't cause any problems.

What I'm really trying to do in the end is be able to use rsync to copy some files to a directory that needs root permission.

---

### Post by nothingspecial on 2011-01-11
Have you considered using sudo once you have logged into the other computer?

---

### Post by bodhi.zazen on 2011-01-11
> **garyed said:**
> Can anyone tell me how I can get my other computer to recognize me when I ssh to it using sudo. If I use the same command without sudo it works fine.
I have it set up so I don't need a password using the ssh-keygen method as myself.
but when I use sudo ssh .... I get:

I was thinking about logging in as root & doing the ssh-keygen method  
& was wondering if that would generate files in /root/.ssh instead of ~/.ssh. I don't want to do anything as root until I'm sure it won't cause any problems.

What I'm really trying to do in the end is be able to use rsync to copy some files to a directory that needs root permission.

Read the error message :

> Add correct host key in /root/.ssh/known_hosts to get rid of this message.
Offending key in /root/.ssh/known_hosts:4
RSA host key for ocean has changed and you have requested strict checking.
Host key verification failed.

Something has changed, new key, new host ssh key ??

Remove line #4 in /root/.ssh/known_hosts

---

### Post by garyed on 2011-01-11
> **nothingspecial said:**
> Have you considered using sudo once you have logged into the other computer?
I can do that but it doesn't solve my problem.
What I'm actually doing is running rsync in a shell script for backing up certain files like my Apache stuff in /var/www.
The script works fine until I get to those type of directories that have root permissions. I don't want to change the permissions for security reasons so I'm trying to run the script as root & it won't let me back in.

---

### Post by garyed on 2011-01-11
> **bodhi.zazen said:**
> Read the error message :



Something has changed, new key, new host ssh key ??

Remove line #4 in /root/.ssh/known_hosts
That's what I'm not sure of what to do.
I don't want to lose the passwordless login I've already created for myself as a user but also want root to be able to do the same thing.
I'm just a little nervous about messing things up a root so I was hoping to get a little guidance.

---

### Post by bodhi.zazen on 2011-01-11
> **garyed said:**
> That's what I'm not sure of what to do.
I don't want to lose the passwordless login I've already created for myself as a user but also want root to be able to do the same thing.
I'm just a little nervous about messing things up a root so I was hoping to get a little guidance.

Well back up the file before you edit it or post more details.

The error message is telling us there is a problem with your hosts, my guess is your ip address changed, not sure.

---

### Post by bodhi.zazen on 2011-01-11
The known_hosts file tracks the host keys, and deleting that entry is not expected to affect the client keys.

If that does not make sense to you, see

[http://www.panix.com/help/ssh.html](http://www.panix.com/help/ssh.html)

[http://gablog.eu/online/node/35](http://gablog.eu/online/node/35)

or man ssh ;)

---

### Post by ticketswapz on 2011-01-11
Gotta love this when you install / reinstall Linux on a virtual private server or dedicated server :rolleyes:

---

### Post by garyed on 2011-01-11
I must not be explaining myself right. 
Computer "A" is the new install
Computer "B" user "Gary"(me) can use ssh to log in fine without a password
but if I use sudo ssh or become root I can not log in to "A" from "B" 
I posted the error message in my other post that I get when trying to log in as root. What I need help on is how to to get computer A to recognize root on computer B. Can anyone tell me what steps to take?

---

### Post by hawkmage on 2011-01-11
Does the root user on Computer B have an ssh public and private key?  
Have you added this public key to the Computer As root users authorized_keys file?
Is there a line with "PermitRootLogin yes" in /etc/ssh/sshd_config?

---

### Post by garyed on 2011-01-12
> **hawkmage said:**
> Does the root user on Computer B have an ssh public and private key?  
Have you added this public key to the Computer As root users authorized_keys file?
Is there a line with "PermitRootLogin yes" in /etc/ssh/sshd_config?
The answer to all your questions is "yes"
Whether I've done everything right I'm not sure but I repeated the steps that I did when I made myself able to log in except logged in as root first.

---

### Post by bodhi.zazen on 2011-01-12
You are going in circles. 

Please read the error message from the first post and then fix /root/.ssh/known_hosts

> Remove line #4 in /root/.ssh/known_hosts 

This is not a configuration problem ;)

---

### Post by garyed on 2011-01-12
> **bodhi.zazen said:**
> You are going in circles. 

Please read the error message from the first post and then fix /root/.ssh/known_hosts



This is not a configuration problem ;)

I tried removing the offending lines & that didn't help.
I just got new offending lines.
Isn't there a way to create a completely new known_hosts file?
What if I just deleted it?
Also computer "A" doesn't even have a known_hosts file in either
~/.ssh/ or /root/.ssh/

---

### Post by bodhi.zazen on 2011-01-12
> **garyed said:**
> I tried removing the offending lines & that didn't help.
I just got new offending lines.
Isn't there a way to create a completely new known_hosts file?
What if I just deleted it?
Also computer "A" doesn't even have a known_hosts file in either
~/.ssh/ or /root/.ssh/

mv /root/.ssh/known_hosts /root/.ssh/known_hosts.bak

---

### Post by ragtag on 2011-01-12
If you've enabled the root user on computer B, you could just do 'su -' and switch to the root user, or you can do all this using 'sudo'.

Remove any offending lines from /root/.ssh/known_hosts, or just move the whole thing away as suggested aboev. You don't need to be afraid to do this, I do it all the time. Every time a computer has been re-installed or changed identity in some way, you'll get this message. It's no big deal. The only thing you need to do to restore the entry in the known_hosts file, is to ssh to the computer, and answer YES, when it asks you. It doesn't affect any keys you may have set up for password less login.

Create new keys for the root user, using ssh-keygen.

Copy those keys to computer A using something like 'ssh-copy-id -i /root/.ssh/id_rsa.pub user@computerA'. See the man page for details.

Now you should be all set.

---

### Post by garyed on 2011-01-12
Thanks to bodhi & ragtag, deleting the known_hosts file worked like a charm. I already set the authorized_keys file for root so I can now do a password-less login too. 
I thought that would solve my rsync permission problem though but it didn't. Even using rsync as root I still can't copy files directly from computer "B" to /var/www on computer "A" .  I guess thats a question for another thread.

---

### Post by bodhi.zazen on 2011-01-12
> **garyed said:**
> Thanks to bodhi & ragtag, deleting the known_hosts file worked like a charm. I already set the authorized_keys file for root so I can now do a password-less login too. 
I thought that would solve my rsync permission problem though but it didn't. Even using rsync as root I still can't copy files directly from computer "B" to /var/www on computer "A" .  I guess thats a question for another thread.

Glad it worked out =)

For rsync see :

[http://www.ehow.com/how_4750765_rsync-over-ssh-password.html](http://www.ehow.com/how_4750765_rsync-over-ssh-password.html)

[http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html)

---

