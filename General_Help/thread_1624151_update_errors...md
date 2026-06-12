---
title: "update errors.."
date: 2010-11-17
forum: General Help
---

### Post by MacKai on 2010-11-17
Been trying to update (With automatic update manager)for a couple of weeks now and keep getting this error:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.92.171 80]



Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.92.171 80]


Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.92.171 80]


Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.92.171 80]


Some index files failed to download, they have been ignored, or old ones used instead.


how do i fix this 

thanks

---

### Post by Dr Mac 24 on 2010-11-23
Hi,

I've just been trying to update from 9.10 to 10.04 with very similar results:


Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-common_1.7.6-2ubuntu7.3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-common_1.7.6-2ubuntu7.3_all.deb) 404  Not Found [IP: 91.189.92.171 80]

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.7.6-2ubuntu7.3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.7.6-2ubuntu7.3_amd64.deb) 404  Not Found [IP: 91.189.92.171 80]

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy_2.30.2-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy_2.30.2-0ubuntu1_amd64.deb) 404  Not Found [IP: 91.189.92.171 80]

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy-common_2.30.2-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy-common_2.30.2-0ubuntu1_all.deb) 404  Not Found [IP: 91.189.92.171 80]

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.98-1ubuntu7_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.98-1ubuntu7_amd64.deb) 404  Not Found [IP: 91.189.92.171 80]

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber-service_2.30.2-0ubuntu3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber-service_2.30.2-0ubuntu3_all.deb) 404  Not Found [IP: 91.189.92.171 80]

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber_2.30.2-0ubuntu3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber_2.30.2-0ubuntu3_all.deb) 404  Not Found [IP: 91.189.92.171 80]

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_2.30.2-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_2.30.2-0ubuntu1_amd64.deb) 404  Not Found [IP: 91.189.92.171 80]

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8k-7ubuntu8.3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8k-7ubuntu8.3_amd64.deb) 404  Not Found [IP: 91.189.92.171 80]

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/i/indicator-sound/indicator-sound_0.2.5-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/i/indicator-sound/indicator-sound_0.2.5-0ubuntu1_amd64.deb) 404  Not Found [IP: 91.189.92.171 80]


Have you solved the problem? if so how?

Cheers

---

### Post by MacKai on 2010-11-23
nobody answered this thread so I re posted and got an answer.

look here

[http://ubuntuforums.org/showthread.php?p=10137034#post10137034](http://ubuntuforums.org/showthread.php?p=10137034#post10137034)

 it fixed the problem for me ...



Good luck 
MacKai

---

### Post by sikander3786 on 2010-11-23
> **MacKai said:**
> Been trying to update (With automatic update manager)for a couple of weeks now and keep getting this error:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.92.171 80]



Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.92.171 80]


Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.92.171 80]


Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.92.171 80]


Some index files failed to download, they have been ignored, or old ones used instead.


how do i fix this 

thanks
Please post the output of

```
cat /etc/apt/sources.list
```

---

### Post by Dr Mac 24 on 2010-11-24
Unfortunately didn't wait for a repay. Instead found solution at "https://answers.launchpad.net/ubuntu/+question/130008" and cleared fault using:
QUOTE
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
QUOTE
in the Terminal. 
Download went OK install started OK. 
Then screen went dark, you could just see the image of the message box as things progressed but couldn't read anything.
Then screen went blank with nothing happening.
Reset after a couple of hours, which loaded to a purple screen with nothing happening.
Switched off and to bed.
I now load to a bark purple screen with few dashes along the top of the screen.
I'll have a search to see if anyone else has the same problem and start a new thread if not.

Thanks for your help.

---

