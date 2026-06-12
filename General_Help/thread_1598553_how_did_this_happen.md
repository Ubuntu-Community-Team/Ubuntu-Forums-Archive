---
title: "how did this happen?"
date: 2010-10-16
forum: General Help
---

### Post by xdweaver on 2010-10-16
I am not sure how to fix this:


wendy@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory
wendy@ubuntu:~$ 


F9AB0399-F007-94B2-BC6B-F4F10195A42D
1.03.01

---

### Post by nothingspecial on 2010-10-16
Try it with sudo
```

sudo apt-get update
```

---

### Post by xdweaver on 2010-10-16
Thanks for the reply, i did that and this is what i got:


wendy@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory
wendy@ubuntu:~$ sudo apt-get update
[sudo] password for wendy: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Get:1 [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release.gpg [197B]               
Ign [http://debian.wgdd.de/ubuntu/](http://debian.wgdd.de/ubuntu/) jaunty/main Translation-en_US               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                       
Ign [http://debian.wgdd.de/ubuntu/](http://debian.wgdd.de/ubuntu/) jaunty/restricted Translation-en_US          
Ign [http://debian.wgdd.de/ubuntu/](http://debian.wgdd.de/ubuntu/) jaunty/universe Translation-en_US  
Ign [http://debian.wgdd.de/ubuntu/](http://debian.wgdd.de/ubuntu/) jaunty/multiverse Translation-en_US
Get:2 [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release [13.2kB]                  
Ign [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Hit [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/main Packages                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/restricted Packages
Hit [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/universe Packages
Hit [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Fetched 198B in 1s (147B/s)
Reading package lists... Done
W: GPG error: [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0F719C35E394D996
wendy@ubuntu:~$ 

F9AB0399-F007-94B2-BC6B-F4F10195A42D
1.03.01

---

### Post by nothingspecial on 2010-10-16
You have 3rd party repos in your sources list.

Try ```

 sudo gpg --keyserver pgp.mit.edu --recv-keys 0xE394D996  && gpg --armor --export 0xE394D996 | apt-key add -
```

Then ```
sudo apt-get update
```

---

### Post by xdweaver on 2010-10-16
tried what you said and this is what happened
:


wendy@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory
wendy@ubuntu:~$ sudo apt-get update
[sudo] password for wendy: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Get:1 [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release.gpg [197B]               
Ign [http://debian.wgdd.de/ubuntu/](http://debian.wgdd.de/ubuntu/) jaunty/main Translation-en_US               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                       
Ign [http://debian.wgdd.de/ubuntu/](http://debian.wgdd.de/ubuntu/) jaunty/restricted Translation-en_US          
Ign [http://debian.wgdd.de/ubuntu/](http://debian.wgdd.de/ubuntu/) jaunty/universe Translation-en_US  
Ign [http://debian.wgdd.de/ubuntu/](http://debian.wgdd.de/ubuntu/) jaunty/multiverse Translation-en_US
Get:2 [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release [13.2kB]                  
Ign [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Hit [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/main Packages                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/restricted Packages
Hit [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/universe Packages
Hit [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Fetched 198B in 1s (147B/s)
Reading package lists... Done
W: GPG error: [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0F719C35E394D996
wendy@ubuntu:~$ sudo gpg --keyserver pgp.mit.edu --recv-keys 0xE394D996  && gpg --armor --export 0xE394D996 | apt-key add -
[sudo] password for wendy: 
Sorry, try again.
[sudo] password for wendy: 
gpg: directory `/home/wendy/.gnupg' created
gpg: new configuration file `/home/wendy/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/wendy/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/wendy/.gnupg/secring.gpg' created
gpg: keyring `/home/wendy/.gnupg/pubring.gpg' created
gpg: requesting key E394D996 from hkp server pgp.mit.edu
gpg: /home/wendy/.gnupg/trustdb.gpg: trustdb created
gpg: key E394D996: public key "Automatic Archive Signing Key for wgdd.de (2009/2010) <daniel.leidert@wgdd.de>" imported
gpg: Total number processed: 1
gpg:               imported: 1
gpg: failed to create temporary file `/home/wendy/.gnupg/.#lk0x8f13328.ubuntu.4149': Permission denied
gpg: keyblock resource `/home/wendy/.gnupg/secring.gpg': general error
gpg: failed to create temporary file `/home/wendy/.gnupg/.#lk0x8f13e78.ubuntu.4149': Permission denied
gpg: keyblock resource `/home/wendy/.gnupg/pubring.gpg': general error
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.
wendy@ubuntu:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                       
Get:1 [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release.gpg [197B]                          
Ign [http://debian.wgdd.de/ubuntu/](http://debian.wgdd.de/ubuntu/) jaunty/main Translation-en_US               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release               
Ign [http://debian.wgdd.de/ubuntu/](http://debian.wgdd.de/ubuntu/) jaunty/restricted Translation-en_US          
Ign [http://debian.wgdd.de/ubuntu/](http://debian.wgdd.de/ubuntu/) jaunty/universe Translation-en_US  
Ign [http://debian.wgdd.de/ubuntu/](http://debian.wgdd.de/ubuntu/) jaunty/multiverse Translation-en_US
Get:2 [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release [13.2kB]
Ign [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/main Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/restricted Packages
Hit [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/universe Packages
Hit [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/multiverse Packages
Fetched 198B in 1s (149B/s)
Reading package lists... Done
W: GPG error: [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0F719C35E394D996
wendy@ubuntu:~$ 

F9AB0399-F007-94B2-BC6B-F4F10195A42D
1.03.01

---

### Post by dborba on 2010-10-20
The previous replier omitted a necessary sudo. Try this:

```
sudo gpg --keyserver pgp.mit.edu --recv-keys 0xE394D996  && sudo gpg --armor --export 0xE394D996 | apt-key add -
```

---

### Post by 3rdalbum on 2010-10-20
If you are using Ubuntu 10.04 then you should definitely not have any entries in your list for Ubuntu 9.04 "jaunty". Remove the lines in /etc/apt/sources.list with "jaunty" in them and then try again.

---

