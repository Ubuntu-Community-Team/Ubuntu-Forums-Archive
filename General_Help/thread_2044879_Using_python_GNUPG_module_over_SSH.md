---
title: "Using python GNUPG module over SSH"
date: 2012-08-20
forum: General Help
---

### Post by guardian2 on 2012-08-20
Hello all,

I have recently started using Python GNUPG for signing and verification,  and it has been working well. My current intention is to be able to do  this using similar scripts over SSH.

Logging into my SSH server with the script is no problem. However when  running the line which loads the Python GNUPG details (from which I can proceed to sign or verify a file), a problem occurs. The line, with the accompanying  traceback is:

gpg = gnupg.GPG(gnupghome="/home/toolserv/.gnupg") 

Traceback (most recent call last):
  File "sshx.py", line 10, in <module>
    gpg = gnupg.GPG(gnupghome="/home/toolserv/.gnupg") 
  File "/usr/local/lib/python2.7/dist-packages/gnupg.py", line 495, in __init__
    os.makedirs(self.gnupghome,0x1C0)
  File "/usr/lib/python2.7/os.py", line 150, in makedirs
    makedirs(head, mode)
  File "/usr/lib/python2.7/os.py", line 157, in makedirs
    mkdir(name, mode)
OSError: [Errno 13] Permission denied: '/home/toolserv'

Manually logging in via SSH I get the following for user permissions:

toolserv@toolserv:~$ ls -ld /home/toolserv/
drwxr-xr-x 29 toolserv toolserv 4096 2012-08-19 22:38 /home/toolserv/

I'm new to SSH and can't figure out what the problem is here. Any help please?

---

