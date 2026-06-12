---
title: "Error during make install hping3"
date: 2011-07-01
forum: General Help
---

### Post by Naudin on 2011-07-01
Hello all,

I'm new to these forums and I'm not that experienced with Linux, but I want to understand more of the TCP/IP protocol and networking in general so I'm trying to install hping3. However, I keep running into an error I can't seem to fix. I run the following commands:

```

./configure
make
sudo make install
```During make install I run into the following error:

```
ln: creating symbolic link 'usr/sbin/hping': File exists
make: *** [install] Error 1
```However, when I check this directory, I can't find any file named hping. Does anybody know what the problem is here? I'm running Xubuntu 11.04.

Thanks in advance,

Naudin

Edit: 
I see now that the hping symbolic link is in fact created during make install. Does this mean "file exists" is not the error and the error notification is just Error 1?

Edit:
I'm sorry. After removing both hping and hping2 from /usr/sbin/ make install worked.

---

### Post by Toz on 2011-07-01
FYI. hping3 is available in the universe repository.> $ apt-cache policy hping3
hping3:
  Installed: (none)
  Candidate: 3.a2.ds2-6
  Version table:
     3.a2.ds2-6 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) natty/universe i386 Packages


You don't have to build from source. Make sure the universe repository is enabled and:```
sudo apt-get install hping3
```

---

