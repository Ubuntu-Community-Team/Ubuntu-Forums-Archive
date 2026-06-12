---
title: "ssh program unexpectedly exited"
date: 2010-12-24
forum: General Help
---

### Post by Dex73 on 2010-12-24
That's the message I get when I try to connect two laptops to one another. I have been following this link 

[http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/]("http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/")

and that is the message that I've been getting. I've tried using it both ways. e.g. with one to the other and vice versa and I get the same message. Also was able to have one computer share files with its self by entering the ip address of the computer I was using. Can anyone tell me how to fix this?

---

### Post by mikewhatever on 2010-12-24
Make sure the openssh-server is installed and running on the remote computer (the one you are trying to connect to).
Verify that the remote computer's IP is correct.

---

### Post by Dex73 on 2010-12-24
> **mikewhatever said:**
> Make sure the openssh-server is installed and running on the remote computer (the one you are trying to connect to).
Verify that the remote computer's IP is correct.

Check and double check. The commands given on the previously mentioned link have been re-entered on the receiving computer and nothing had to be modified, then I tried again with the same result. Plus, I've since tried to enter the broadcast address instead of the IP to see what happens and it gave the message much faster instead of waiting for about 10 seconds. This, I think, suggest that I'm not just getting the IP address wrong. Right?

---

### Post by spiky001 on 2010-12-24
Can you ssh straight into the server from terminal, has the ssh port been changed?

---

### Post by Dex73 on 2010-12-24
> **spiky001 said:**
> Can you ssh straight into the server from terminal, has the ssh port been changed?

can you give me an example to follow for the command line? I don't know how to enter the info that way. I did enter the command ssh 192.168.1.102 and it gives me

"ssh: connect to host 192.168.1.102 port 22: Connection timed out".

I haven't changed the port that I know of. I typed in 22 like the link said to the first time and I tried not typing in a port # the next time and I got the same result.

---

### Post by efflandt on 2010-12-24
Can you ssh to the computer you are on?  In other words:  **ssh localhost**

If that does not work, you are not going to be able to ssh to it from a different computer.  Open Synaptic, type **openssh** in Quick search, and see if **openssh-server** is installed (not just openssh-client).

Also if you have ~/.ssh directory for keys or config, make sure the directory has 700 permission (drwx------) and files in it have 600 permission (-rw-------).

---

### Post by Dex73 on 2010-12-24
> **efflandt said:**
> Can you ssh to the computer you are on?  In other words:  **ssh localhost**

If that does not work, you are not going to be able to ssh to it from a different computer.  Open Synaptic, type  in Quick search, and see if  is installed (not just ).

Also if you have ~/.ssh directory for keys or config, make sure the directory has  and files in it have 600 permission (-rw-------).

I can ssh to the computer I'm on, both openssh-client and **openssh-server** are installed.

Also, /.ssh has 700 permission I think?
~$ ls -al
drwx------   2 next   next     4096 2010-12-24 16:28 .ssh

Thinks for the help I still kinda new at this.

---

### Post by efflandt on 2010-12-25
One other thing I thought of is if you are trying to connect to another PC on the same LAN, make sure you use the LAN IP of the server.

Someone else was wondering why they could ssh home from work, but could not ssh to the home computer when at home.  But most routers do not do loopback (LAN2LAN via WAN IP) and he had been trying to connect using his public dynamic DNS name (public IP).  Once he using the LAN IP of the PC he was trying to connect to, it worked.

Also are you running any firewall on either machine?

---

### Post by mikewhatever on 2010-12-25
> **Dex73 said:**
> can you give me an example to follow for the command line? I don't know how to enter the info that way. I did enter the command ssh 192.168.1.102 and it gives me

"ssh: connect to host 192.168.1.102 port 22: Connection timed out".



ssh username@192.168.1.102

where 'usename' is a valid user on the remote computer. You'll be asked for that user's password.

---

### Post by Dex73 on 2010-12-25
I'm running a firewall(ufw) on both laptops.

Also ran "ssh username@192.168.1.102" where username is a valid user name and got the same thing. Thinking of creating a new user and then trying it. Something simple like 123456 just to make sure I didn't screw something up. I'll post the results.

---

### Post by spiky001 on 2010-12-25
What happens if you turn the firewall off

---

### Post by mikewhatever on 2010-12-25
> **Dex73 said:**
> I'm running a firewall(ufw) on both laptops.


What are the merits of doing that if you are behind the router? Anyway, whatever the reasons, you'll need to allow port 22, which is the default for ssh.

---

### Post by Dex73 on 2010-12-26
Allowing port 22 worked. Thanks for the help.

---

### Post by fkoskotas on 2012-05-14
> **Dex73 said:**
> I'm running a firewall(ufw) on both laptops.

Also ran "ssh username@192.168.1.102" where username is a valid user name and got the same thing. Thinking of creating a new user and then trying it. Something simple like 123456 just to make sure I didn't screw something up. I'll post the results.


Did that work?

---

