---
title: "Software update failed"
date: 2009-12-07
forum: General Help
---

### Post by arifcsecu on 2009-12-07
How can i fix this problem: 

arifcsecu@arifcsecu:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) jaunty Release.gpg                            
  Could not connect to bd.archive.ubuntu.com:80 (91.189.88.30). - connect (101 Network is unreachable) [IP: 91.189.88.30 80]
Err [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (101 Network is unreachable)


..........................

---

### Post by dcstar on 2009-12-07
> **arifcsecu said:**
> How can i fix this problem: 

arifcsecu@arifcsecu:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) jaunty Release.gpg                            
  Could not connect to bd.archive.ubuntu.com:80 (91.189.88.30). - connect (101 Network is unreachable) [IP: 91.189.88.30 80]
Err [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (101 Network is unreachable)


Try rebooting, you have a networking problem.

---

### Post by arifcsecu on 2009-12-07
Yes i solved it
it was a network proxy setting problem
i just set the IP address and Port number
Then it suffices

---

