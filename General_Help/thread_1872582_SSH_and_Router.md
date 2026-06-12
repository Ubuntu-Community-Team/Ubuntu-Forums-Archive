---
title: "SSH and Router?"
date: 2011-10-30
forum: General Help
---

### Post by TechieJustin on 2011-10-30
I am tying to get SSH working, from outside the router.

What I'm trying to do is VNC from outside, to the Linux machine running 10.10.  But I want to run VNC over an SSH tunnel, which I thought I had set up.

Port 22, is forwarded to the internal IP of the machine, and I can connect via SFTP.  But, when I try to connect via SSH login, this is what I get
```

ssh -L 6900:localhost:5900 -N justin@<external IP>
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
9d:c2:80:2c:9f:77:cd:47:a5:e2:11:f7:13:34:44:23.
Please contact your system administrator.
Add correct host key in /Users/Justin/.ssh/known_hosts to get rid of this message.
Offending RSA key in /Users/Justin/.ssh/known_hosts:2
RSA host key for krustybutt.dyndns-home.com has changed and you have requested strict checking.
Host key verification failed.
```

When I'm inside the router on the local network, everything is fine, and I can SSH to the internal IP address without any problem.

---

### Post by wojox on 2011-10-30
Your answer is right there:

> Add correct host key in /Users/Justin/.ssh/known_hosts to get rid of this message.


---

### Post by CharlesA on 2011-10-30
You can also remove the key by using ssh-keygen -R hostname/ip address

---

### Post by TechieJustin on 2011-10-31
> **wojox said:**
> Your answer is right there:

When I try to edit that file, it doesn't exist.

What about when others' try to ssh in?  If I create that directory and file, and add that key, that will only apply to my account.

EDIT:

I created .ssh in my homedir, created that file and added that key.
Same result.

actually, another question.
Which known_hosts file do I edit?  The one on my laptop or the one on the server?

---

### Post by wojox on 2011-10-31
Run:

```
rm ~/.ssh/known_hosts

```

---

### Post by TechieJustin on 2011-10-31
> **wojox said:**
> Run:

```
rm ~/.ssh/known_hosts

```

Done.

No change.

---

### Post by TechieJustin on 2011-10-31
I looked around and I still can't find a solution.  I'm not sure what's going on.

---

### Post by CharlesA on 2011-10-31
Are you able to ssh to localhost on the machine in question?

---

### Post by TechieJustin on 2011-10-31
> **CharlesA said:**
> Are you able to ssh to localhost on the machine in question?

Yes I can.
```
justin@Krustybutt:~$ ssh localhost
The authenticity of host 'localhost (::1)' can't be established.
RSA key fingerprint is 9d:c2:80:2c:9f:77:cd:47:a5:e2:11:f7:13:34:44:23.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.
justin@localhost's password: 
Linux Krustybutt 2.6.35-30-generic #61-Ubuntu SMP Tue Oct 11 15:29:15 UTC 2011 i686 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

Your CPU appears to be lacking expected security protections.
Please check your BIOS settings, or for more information, run:
  /usr/bin/check-bios-nx --verbose

New release 'natty' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Mon Oct 31 17:43:47 2011 from justins-macbook-pro.local
```

---

### Post by CharlesA on 2011-10-31
Ok. It is giving a similar error, try running this:

```
sudo updatedb
```

Then post the output of:

```
locate known_hosts
```

---

### Post by TechieJustin on 2011-10-31
> **CharlesA said:**
> Ok. It is giving a similar error, try running this:

```
sudo updatedb
```Then post the output of:

```
locate known_hosts
```

Got it.
```

locate known_hosts
/home/justin/.ssh/known_hosts
```

---

### Post by CharlesA on 2011-10-31
Hm, that's the only known_hosts file. What are the permissions on it?

Deleting it should have gotten that error to go away.

---

### Post by TechieJustin on 2011-10-31
> **CharlesA said:**
> Hm, that's the only known_hosts file. What are the permissions on it?

Deleting it should have gotten that error to go away.

I'll try deleting it again and see what happens.

```
justin@Krustybutt:~/.ssh$ ls -la
total 12
drwxr-xr-x  2 justin justin 4096 2011-10-31 18:56 .
drwxr-xr-x 38 justin justin 4096 2011-10-31 21:32 ..
-rw-r--r--  1 justin justin  442 2011-10-31 18:56 known_hosts
```

---

### Post by CharlesA on 2011-10-31
Those are the right permissions too.

Very strange.

Were you sshing into the machine from another machine on the same network? You might have to delete the known_hosts file from the client machine.

---

### Post by TechieJustin on 2011-10-31
> **CharlesA said:**
> Those are the right permissions too.

Very strange.

Were you sshing into the machine from another machine on the same network? You might have to delete the known_hosts file from the client machine.

No change after deleting the .ssh directory in my home folder.

This is what I get from **outside** the router```

Justins-MacBook-Pro:~ Justin$ ssh -L 6900:localhost:5900 -N justin@blahblahblah.dyndns.com
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
9d:c2:80:2c:9f:77:cd:47:a5:e2:11:f7:13:34:44:23.
Please contact your system administrator.
Add correct host key in /Users/Justin/.ssh/known_hosts to get rid of this message.
Offending RSA key in /Users/Justin/.ssh/known_hosts:2
RSA host key for krustybutt.dyndns-home.com has changed and you have requested strict checking.
Host key verification failed.
```

I am using dyndns since my ip ddress changes constantly, however the same thing happens if I  use my ISP's external address.


From **inside** the router on the local LAN...```

Justins-MacBook-Pro:~ Justin$ ssh justin@192.168.1.127
justin@192.168.1.127's password: 
Linux Krustybutt 2.6.35-30-generic #61-Ubuntu SMP Tue Oct 11 15:29:15 UTC 2011 i686 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

Your CPU appears to be lacking expected security protections.
Please check your BIOS settings, or for more information, run:
  /usr/bin/check-bios-nx --verbose

New release 'natty' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Mon Oct 31 18:57:21 2011 from krustybutt
```

The thing is, I had something similar set up using my iMac, including the ssh tunnel and it worked perfectly.

I'll try blowing away my SSH stuff on the client...  But for now I'm going to bed.  I think I'm getting sick.
I wish flu shots came with a warranty.

---

### Post by CharlesA on 2011-10-31
Ok, check the known_hosts file on the macbook and delete/rename it

It says where it is:

```
Offending RSA key in /Users/Justin/.ssh/known_hosts:2
```

---

### Post by TechieJustin on 2011-10-31
> **CharlesA said:**
> Ok, check the known_hosts file on the macbook and delete/rename it

It says where it is:

```
Offending RSA key in /Users/Justin/.ssh/known_hosts:2
```


Right after I posted my last message I think I figured it out.
I blew everything away in my client's .ssh directory.
The error message was legit.  From ssh's point of view the machine changed, but I was trying to access it in the exact same way.
Like I said, it worked perfectly when I had the iMac taking the ssh connections.  I swapped out the iMac for this B100 running Maverick.  So, when the client SSH authenticated with what it thought was the iMac, it didn't match up and kicked up the error.

I don;t know if I n00bed myself on this one or not.

Now my next task is to get VNC working at the login screen....

---

### Post by CharlesA on 2011-10-31
Good luck. It was probably due to the IP address changing.

---

### Post by TechieJustin on 2011-10-31
> **CharlesA said:**
> Good luck. It was probably due to the IP address changing.


The machine, OS, IP and literally everything changed.  I just thought I could swap them and it wouldn't notice.

---

