---
title: "Lots of problems"
date: 2011-01-07
forum: General Help
---

### Post by Terry19 on 2011-01-07
Hey, 
My ubuntu 10.10 won't let me install anything. 
At first it wouldn't let me install software in the ubuntu software center, I could get around this using the terminal. But now it wont let me install updates. I get an error. 
[[Requires installation of untrusted packages

The action would require the installation of packages from sources that are not authenticated.]]

A similar message appears when i try to install software. 

Please help. 

[email]terryk_tv@hotmail.com[/email]

---

### Post by wojox on 2011-01-07
See here [[SOLVED] The action would require the installation of packages from not authenticated sources?]("http://ubuntuforums.org/showthread.php?t=1626757")

---

### Post by cipherboy_loc on 2011-01-07
Edit: See Wojox's post.

---

### Post by Terry19 on 2011-01-07
This did not fix the problem.

---

### Post by JC Cheloven on 2011-01-07
EDIT: I assume your system is the state after applying wojox' advice.

Hopefully, this sequence of commands may be of help:
```
sudo apt-get update
```
```
sudo dpkg-reconfigure -a
```
```
sudo apt-get update
```

---

### Post by Terry19 on 2011-01-08
Still has not fixed the problem. I get the same error message. 
The action would require the installation of packages from sources that are not authenticated.

---

### Post by oldos2er on 2011-01-08
Can you run ```
sudo apt-get update && sudo apt-get upgrade
``` in a terminal, and post the output here?

---

### Post by Terry19 on 2011-01-08
Still wont let me install software using the software center.

---

### Post by Terry19 on 2011-01-08
A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by JC Cheloven on 2011-01-09
OK, I think we have it!

Please see [here]("http://www.ubuntugeek.com/fix-for-gpg-error-httpextras-ubuntu-com-maverick-release.html"), and don't forget to mark the thread as solved if it works ;)

Cheers
JC

---

### Post by Terry19 on 2011-01-10
nope. still problems. 

[sudo] password for richard:********* 
gpg: no valid OpenPGP data found.
richard@richard-GA-MA780G-UD3H:~$ 


These problems are giving me the shits. anyone up for remote assistance?

---

### Post by oldos2er on 2011-01-10
Here's a direct link to the key: [http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg)
After you've downloaded it, run ```
cd Downloads
sudo apt-key add Release.gpg
``` assuming the key is in your ~/Downloads folder.

---

### Post by Terry19 on 2011-01-11
That did nothing. 
What is going on with my linux, it's giving me more troubles than windows vista and 7 combined.

---

### Post by Terry19 on 2011-01-11
After a restart everything seems to be working fine. Thanks sooo much. It took a bit of fuc**ng around but we got there in the end.

---

