---
title: "cannot connect ssh"
date: 2010-11-30
forum: General Help
---

### Post by kaykav on 2010-11-30
HI,
    This ssh thing is driving me to frustration...
             I have two desktops,one has 'crunchbang linux',the other
             ubuntu 10.10. Both machines can ping each other. Crunchbang can ssh ubuntu successfully.However ubuntu can not ssh crunchbang. I have reinstalled openssh-server and restarted twice to no avail.
    The error message is 'connection timed out'.  Why can't I do this?
                       I think if I 'understood'this ssh protocol,I might be able to troubleshoot with success.   What do I need to do?
                        Thanks...Rich

---

### Post by czr114 on 2010-11-30
Is the affected server running (ps aux | grep sshd)?

Is the affected server listening (from another box, nmap -p22 [target])?

Is there a firewall on the affected server?

---

### Post by galvatron408 on 2010-11-30
you should try to connect to yourself to see if that works. i was going to say to do this on the suspect machine but thought that you might do it to the wrong machine, so do this to both machines and see if it works...

ssh localhost

did you get a connection?

---

### Post by kaykav on 2010-11-30
> **czr114 said:**
> Is the affected server running (ps aux | grep sshd)?

Is the affected server listening (from another box, nmap -p22 [target])?

Is there a firewall on the affected server?

kaykav@ditty:~$ ps aux | grep sshd
root     17620  0.0  0.0   5632   984 ?        Ss   16:53   0:00 /usr/sbin/sshd
kaykav   18449  0.0  0.0   4012   764 pts/0    S+   18:28   0:00 grep --color=auto sshd

---

### Post by czr114 on 2010-11-30
> **kaykav said:**
> kaykav@ditty:~$ ps aux | grep sshd
root     17620  0.0  0.0   5632   984 ?        Ss   16:53   0:00 /usr/sbin/sshd
kaykav   18449  0.0  0.0   4012   764 pts/0    S+   18:28   0:00 grep --color=auto sshd
Ok, that means sshd is running and not choking on its own config file or being terminated prematurely.

Now try connecting to it from the local machine or nmaping it from another machine.

Are you running a firewall?

---

### Post by kaykav on 2010-11-30
ok Now I have it.. All is well..I made sure I had sshopen-server installed on 'both' machines..      thank you for your replies.  Its good to know there is help, when needed...Rich

---

