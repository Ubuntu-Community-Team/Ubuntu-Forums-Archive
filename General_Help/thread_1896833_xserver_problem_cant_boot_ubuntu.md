---
title: "xserver problem cant boot ubuntu"
date: 2011-12-17
forum: General Help
---

### Post by tetsu7 on 2011-12-17
have ubuntu 11.10 just clean installed a couple days ago. restarted computer and now i cant boot. i do get the grub. recovery console only gives me read only and wont mount into wr. seems to be a problem with xserver. when i try to start xserver from command in recovery i get "could not create lock file in /tmp/.txo-lock" "giving up" "unable to connect to x server: network is unreachable" "unexpected signal 2" "error in locking authority file /root/.xauthority" i already tried chrooting into the file system from a live cd and deleting the .Xauthority file as ive seen several other forums people said this worked for them as a new file was generated on boot. however this did not work for me and it did not generate a new file. any ideas?

---

### Post by 2F4U on 2011-12-18
If your partitions are only mounted in read mode, this has not much to with the X server. The X server is started at a much later point in time.
If the root partition is mounted read-only, it is only natural that the X server fails, since it is not able create certain files (because the root partiton has been mounted read-only). So the question is why are your partitions mounted read-only? Was this the case from the beginning (probably not) and what happened in the time between?

---

### Post by tetsu7 on 2011-12-18
good point. i was changing some permissions with mount manager but i dont recall changing anything with /dev/sda however in light of my problem happening on my next boot and the point you just made i can only assume i must have made a mistake at some point. it makes sense because i deleted some files in tmp thinking they would be recreated but they havnt. any idea how to check if this is the case, and or change this? i can chroot into /dev/sda from the live cd to make changes, im just not sure what to change...

---

### Post by tetsu7 on 2011-12-18
i chrooted into the system and found an fstab.BAK so i deleted fstab and renamed fstab.BAK to fstab and now im all good. thank you very much sir for pointing out what my problem was, i really appreciate it!

---

