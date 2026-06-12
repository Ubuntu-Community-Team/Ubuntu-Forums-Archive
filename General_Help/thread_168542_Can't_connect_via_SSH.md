---
title: "Can't connect via SSH"
date: 2006-04-30
forum: General Help
---

### Post by OMJD on 2006-04-30
I am trying to connect to my Ubuntu system via another system on my network using SSH. However, I always get "connection refused" or "Broken Pipe" responses. When I ping the system from here, it reaches it fine.

Any ideas?

---

### Post by astoltz on 2006-04-30
Do you have the openssh-server package installed?

---

### Post by OMJD on 2006-04-30
Yep, I do. I also have DMZ enabled on the correct internal IP. But no luck however. :(

---

### Post by chriscando on 2006-04-30
make sure it is running:
sudo /etc/init.d/ssh start

---

### Post by OMJD on 2006-05-01
I did that but it said "[fail]"

---

### Post by OMJD on 2006-05-02
Sorry for the double post, but any ideas why it isn't working? I assume what I said in the above post has something to do with it, but I don't know why it's not starting up.

---

### Post by christhemonkey on 2006-05-02
Have you tried the howto on the wiki? worked great for me
[https://wiki.ubuntu.com/SSHHowto](https://wiki.ubuntu.com/SSHHowto)

If that doesnt work try reading this page
[https://wiki.ubuntu.com/AdvancedOpenSSH](https://wiki.ubuntu.com/AdvancedOpenSSH)

Let us know.

---

### Post by cellarguy on 2006-05-04
Recently I've been playing around with installing ubuntu on an old broken computer here in the basement.  Getting the memory-deficient machine to run ubuntu is another story.  

I got **ssh** working fine between the old and new computers, then the new computer settings broke when I played too heavily with **compiz** and had to reinstall everything.  But that's yet another story.

When I got the newer computer up and running again, of course **ssh** no longer worked, as the public/private keys of the machines (and even the IP addresses now) were different.  So I followed the [link to the howto]("https://wiki.ubuntu.com/SSHHowto") that you so kindly provided:  and started over.  It took the better part of the morning because I had to copy the public keys to and from the computers via floppies.  And I had to find some floppies and remember how to mount and umount them, its been so long...

One thing that was different: the HowTo describes a file 

 ~/.ssh/authorized_keys2

This file didn't exist, so I made it, but that didn't help.  It appears that the file should have been called

 ~/.ssh/known_hosts

When I copied the ~/.ssh/id_dsa.pub (public keys file) from one machine to the other and put it in ~/.ssh/known_hosts , I was up and running again, and did a little dance.

---

