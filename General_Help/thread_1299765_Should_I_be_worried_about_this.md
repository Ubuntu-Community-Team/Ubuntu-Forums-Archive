---
title: "Should I be worried about this?"
date: 2009-10-24
forum: General Help
---

### Post by harecanada on 2009-10-24
When I run sudo apt-get update and sudo apt-get upgrade I get the folowing:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061

W: Failed to fetch [http://deb.opera.com/opera/dists/lenny/Release](http://deb.opera.com/opera/dists/lenny/Release)  

W: Failed to fetch [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/binary/Packages](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/binary/Packages)  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/source/Sources](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/source/Sources)  Unable to fetch file, server said 'Failed to open file.  '

W: Some index files failed to download, they have been ignored, or old ones used instead.

Is this something I should be concerned about?
Thanks,
harecanada

---

### Post by nothingspecial on 2009-10-24
```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
``` should help.

---

### Post by harecanada on 2009-10-25
Hi nothingspecial,
I tried this and got the following output:
Get:17 [ftp://ftp.mysql.com](ftp://ftp.mysql.com) source/ Sources                                     
Err [ftp://ftp.mysql.com](ftp://ftp.mysql.com) source/ Sources                                        
  Unable to fetch file, server said 'Failed to open file.  '
Fetched 3945B in 9s (419B/s)                                                   
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061

W: Failed to fetch [http://deb.opera.com/opera/dists/lenny/Release](http://deb.opera.com/opera/dists/lenny/Release)  

W: Failed to fetch [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/binary/Packages](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/binary/Packages)  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/source/Sources](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/source/Sources)  Unable to fetch file, server said 'Failed to open file.  '

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


I haven't a clue what all this stuff means.
harecanada

---

### Post by oldos2er on 2009-10-25
It looks like  some directories have changed at ftp.mysql.com. If you open System, Administration, Software Sources, you can temporarily remove them from your sources.list. If I were you, I'd do the same for deb.opera.com. You can download Opera from here: [http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

---

### Post by harecanada on 2009-10-27
Hi oldos2er,

This seems to have handled it. 
Thanks for the help.
Do you know if there is something wrong with Apple Quicktime Movie trailers? I can't seem to get them to run. I can get other video to run like BBC news feed videos but there are some that I can't get to work. Any ideas?
harecanada

---

### Post by oldos2er on 2009-10-27
Have you installed the package libquicktime1 ?

---

### Post by harecanada on 2009-10-28
yes, that's installed. When I click on a trailer, the player window at quicktime opens and then just flashes for a minute and then stops. I can't figure it out. There is another webcam that I try to watch and when I go to that sight, it freezes my computer and I have to do a cold boot to get it going. 
harecanada

---

