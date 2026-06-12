---
title: "application installation help"
date: 2006-04-23
forum: General Help
---

### Post by yikesazombie on 2006-04-23
i am a linux newbie.  i am an IT consultant in windows environments and am looking to *nix to expand my horizons.

so far i love kubuntu.  i am having a major problem with installing new applications.  i have done searches on the forum and found good information, but have not been able to translate it into getting things to work ](*,) 

i am trying to install Mozilla Thunderbird.  can someone please steer me in the right direction?  once i am able to do an install i should be ok with moving forward.  i just need to be pushed "out of the nest."

---

### Post by gingermark on 2006-04-23
sudo apt-get install mozilla-thunderbird

Have a look at [http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php)

---

### Post by aysiu on 2006-04-23
If you want the newest version of Thunderbird, follow these instructions:
[http://wiki.ubuntu.com/ThunderbirdNewVersion](http://wiki.ubuntu.com/ThunderbirdNewVersion)

Just change this line ```
sudo tar -C /opt -x -z -v -f thunderbird-1.5.tar.gz
``` to say ```
sudo tar -C /opt -x -z -v -f thunderbird-1.5.0.2.tar.gz
```

---

### Post by yikesazombie on 2006-04-23
thanks a bunch, this is good informaiton!

---

