---
title: "Please Help! Can't get SSH working with id_rsa.pub key"
date: 2011-11-12
forum: General Help
---

### Post by robn30 on 2011-11-12
I want to connect over my local network from my laptop to my desktop.  I have gone through all the procedures to edit the sshd_config and copied my id_rsa.pub key to the remote machine (desktop in this case).  Every time I try to connect it tells me permission denied (publickey).  I have done much Googling and tried many different things.  I am very new to this.  Please spell it out in layman's terms, please don't expect I will just know it.  I know many folks here have been doing this for years.  I am totally new but ready to learn and have figured out a lot already.  I really need help on this one it is boggling me.

---

### Post by lykwydchykyn on 2011-11-12
I think something is backwards; you need to copy the public key from the machine you're sitting at to the remote machine that you want to SSH into.  

Try this:
- Re-enable password logins on the desktop's sshd_config
- create an ssh key on your LAPTOP with this command:
```

ssh-keygen -t rsa

```

- copy the ssh key to the desktop with this command:
```

ssh-copy-id -i ~/.ssh/id_rsa.pub myuser@desktopHostname

```

- Now re-disable password logins on the desktop

That should get you working.

---

### Post by robn30 on 2011-11-12
> **lykwydchykyn said:**
> I think something is backwards; you need to copy the public key from the machine you're sitting at to the remote machine that you want to SSH into.  

Try this:
- Re-enable password logins on the desktop's sshd_config
- create an ssh key on your LAPTOP with this command:
```

ssh-keygen -t rsa

```- copy the ssh key to the desktop with this command:
```

ssh-copy-id -i ~/.ssh/id_rsa.pub myuser@desktopHostname

```- Now re-disable password logins on the desktop

That should get you working.

I did copy to the station I want to remote into and I have edited the sshd_config file for password login to no.  I used the scp .ssh/id_rsa.pub [email]user@desktophost:.ssh[/email]/authorized_keys and it copied the key to the remote machine.  I would assume as long as the key gets in there it doesn't much matter how you do it, right?  Could have used a USB flash drive for all its worth.  BTW if I leave password login to yes I can connect perfectly.  As soon as I comment to no and restart the ssh daemon is when I get the Permission Denied (publickey).  Do you think it is a permissions thing or something?  Or could it be that my laptop and desktop both use the same username for login?  I am a bit lost here.

---

### Post by lykwydchykyn on 2011-11-12
> **robn30 said:**
> I did copy to the station I want to remote into and I have edited the sshd_config file for password login to no.  I used the scp .ssh/id_rsa.pub [email]user@desktophost:.ssh[/email]/authorized_keys and it copied the key to the remote machine.  I would assume as long as the key gets in there it doesn't much matter how you do it, right?  Could have used a USB flash drive for all its worth.  BTW if I leave password login to yes I can connect perfectly.  As soon as I comment to no and restart the ssh daemon is when I get the Permission Denied (publickey).  Do you think it is a permissions thing or something?  Or could it be that my laptop and desktop both use the same username for login?  I am a bit lost here.

Since it's not working, I'd try the commands listed.  

Same login name is not a problem.

---

### Post by Cyclane on 2011-11-12
Do you mean that when you have the same username on the client as on the server it works?

trie the following command: ssh USERNAME@HOST

---

### Post by robn30 on 2011-11-12
> **lykwydchykyn said:**
> Since it's not working, I'd try the commands listed.  

Same login name is not a problem.

Ok so I tried your ssh-copy-id and it gave me this. bash: /home/rob/.ssh/authorized_keys: Is a directory.  BTW I did re-enable password login before trying that command.  This is crazy.  It works perfect when just using a password.  It has to be something simple but I just don't know enough to figure it out.  Not sure why the scp command works but not the ssh-copy-id.

> **Cyclane said:**
> Do you mean that when you have the same username on the client as on the server it works?

trie the following command: ssh USERNAME@HOST

It works with password but not with RSA key login where you would bypass password authentication.

---

### Post by Cyclane on 2011-11-12
uhmmm, is '/home/rob/.ssh/authorized_keys' a directory?

ls -l /home/rob/.ssh/

I'm not sure if a sudo is needed

---

### Post by robn30 on 2011-11-12
> **Cyclane said:**
> uhmmm, is '/home/rob/.ssh/authorized_keys' a directory?

ls -l /home/rob/.ssh/

I'm not sure if a sudo is needed

If it is a directory is that bad?  How can it not be a directory? It's a folder under the ~/.ssh.  Is it supposed to be something else? This is what results from the ls -l.

drw------- 2 rob rob 4096 2011-11-12 23:13 authorized_keys
-rw------- 1 rob rob 1766 2011-11-12 23:13 id_rsa
-rw-r--r-- 1 rob rob  389 2011-11-12 23:13 id_rsa.pub
-rw-r--r-- 1 rob rob  222 2011-11-12 23:14 known_hosts

---

### Post by robn30 on 2011-11-12
I am completely lost here.  I just turned back on password authentication and perfectly created a SSH tunnel for a VNC server with no problem.  Damned if I can get the RSA key to work.  Again it has to be something simple if the password login works flawlessly. I just keep getting the Permission Denied: (publickey) when I try to RSA Authenticate.  Very frustrating for sure.  Now I know why they built Windows, for situations like this and for noob's like me.

---

### Post by Cyclane on 2011-11-12
```
rmdir ~/.ssh/authorized_keys
```

It's supposed to be a file. Run above command and try again.

---

### Post by robn30 on 2011-11-13
> **Cyclane said:**
> ```
rmdir ~/.ssh/authorized_keys
```It's supposed to be a file. Run above command and try again.

Holy $*@%.  I knew it had to be something simple, it worked!  I just assumed the authorized_keys was a directory that I had to create.  Of course the ssh-copy-id worked perfectly after removing the stupid folder I created.  Thanks Cyclane, your a lifesaver!

---

### Post by Cyclane on 2011-11-13
No problem, have fun managing your desktop remotely.

---

