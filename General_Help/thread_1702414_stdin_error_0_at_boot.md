---
title: "stdin: error 0 at boot"
date: 2011-03-07
forum: General Help
---

### Post by n~kf)}BW% on 2011-03-07
Hello, i've tryed to get rid of the ugly plymouth splash screen and this outpout at boot now:

stdin: error 0

and so on... It also appears in my /var/log/boot.log and /var/log/casper.log. But the OS works, just like before. I would like to know how can i get rid of this error. Or how can i hide it? Can i redirect the output to dev null at boot time?

Here is boot.log
```
stdin: error 0

Generating locales...

  sl_SI.UTF-8... up-to-date

Generation complete.

Using CD-ROM mount point /cdrom/

Identifying.. [f8ddb5cb551866e6ba1bbeda7f2eb344-2]

Scanning disc for index files..

Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures

Found label 'Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)'

This disc is called: 

'Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)'

Copying package lists...gpgv: Signature made Thu Oct  7 18:24:11 2010 CEST using DSA key ID FBB75451

gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"


Reading Package Indexes... 0%

Reading Package Indexes... 2%

Reading Package Indexes... Done


Writing new source list

Source list entries for this disc are:

deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted

Repeat this process for the rest of the CDs in your set.

W: Skipping nonexistent file /cdrom/dists/maverick/main/binary-amd64/Packages

W: Skipping nonexistent file /cdrom/dists/maverick/restricted/binary-amd64/Packages

No value set for `/apps/netbook-launcher/favorites/favorites_list'

No value set for `/apps/netbook-launcher/favorites/favorites_list'

No value set for `/apps/netbook-launcher/favorites/favorites_list'

No value set for `/apps/netbook-launcher/favorites/favorites_list'

No value to set for key: `/apps/netbook-launcher/favorites/favorites_list'

No value to set for key: `/apps/netbook-launcher/favorites/favorites_list'

 * Setting sensors limits       [80G 
[74G[ OK ]

speech-dispatcher disabled; edit /etc/default/speech-dispatcher

[9;0] * Starting the Winbind daemon winbind       [80G 
[74G[ OK ]

 [33m*[39;49m PulseAudio configured for per-user sessions

saned disabled; edit /etc/default/saned

 * Enabling additional executable binary formats binfmt-support       [80G 
[74G[ OK ]

 * Starting web server apache2       [80G
```Because it is really annoying to see an "error" when your computer boots, even if it is not really an error :popcorn:

---

### Post by n~kf)}BW% on 2011-03-08
Desperate bump... ](*,)

---

### Post by Urko on 2011-03-16
Try correct it with splashy or fbsplash.

---

