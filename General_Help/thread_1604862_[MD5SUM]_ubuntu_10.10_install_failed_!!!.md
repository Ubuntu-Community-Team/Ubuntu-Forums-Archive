---
title: "[MD5SUM] ubuntu 10.10 install failed !!!"
date: 2010-10-24
forum: General Help
---

### Post by rostom_zer on 2010-10-24
Hello.

please could someone expplain my case please !!!

i downloaded ubuntu 10.10 desktop i386 version from ubuntu site

i noticed that the MD5 of my file does not correspond with the hash posted in ubuntu hashes

i burned the iso then tried to install ubuntu ---> install failed

i redownloaded the iso again ----> not the original MD5 ----> failed

i redownloaded the iso again again ----> not the original MD5 ----> failed

i redownloaded the iso again again again ----> not the original MD5 ----> failed

i redownloaded the iso again again again................ ----> not the original MD5 ----> failed

so... when will i get the (not corrupted file) !!!!!!! :confused:

note:

i'm sick of downloading this file, because i downloaded it looooooooots of time.

please........... help me...

thanX in advance

---

### Post by mr clark25 on 2010-10-24
if you still have all of the files you downloaded, check and see if their md5sums match.

it could be that only the first one you downloaded was bad, and then you started using the wrong md5sum to check the rest...

---

### Post by rostom_zer on 2010-10-25
No i'deleted them all.

now i'm downloading one again then i'll compare it's MD5 with the original one which is written here [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

must my downloaded ISO has this MD5 : 59d15a16ce90c8ee97fa7c211b7673a8 ???

---

### Post by Dans564 on 2010-10-25
> **rostom_zer said:**
> No i'deleted them all.

now i'm downloading one again then i'll compare it's MD5 with the original one which is written here [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

must my downloaded ISO has this MD5 : 59d15a16ce90c8ee97fa7c211b7673a8 ???

59d15a16ce90c8ee97fa7c211b7673a8 is what it should be. try downloading via a torrent, it will be faster and maybe fix your problem.  [http://releases.ubuntu.com/maverick/ubuntu-10.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/maverick/ubuntu-10.10-desktop-i386.iso.torrent)

---

### Post by rostom_zer on 2010-10-26
Got it using torrent link ;)

now my downloaded iso matches the original MD5

but... one other thing

i installed uubntu using USB mode (USB live 10.10)

now when my laptop boots, i get this msg " 
**could not load /lib/modules/2.6.35-22-generic/modules.deb**


but it boots normal !!!

now i'm getting worried 

could some one help ?

thanX in advance ;)

---

### Post by mr clark25 on 2010-10-26
you might want to boot from the usb drive again and select "check this drive for errors"

i don't know exactly how to get there in ubuntu 10.10 as i haven't used it yet myself. i like to stick to the LTS releases.

---

### Post by spiky001 on 2010-10-26
Found a bug report here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421)  they mention a fix if you go through it

---

### Post by rostom_zer on 2010-10-28
yes i've read about that bug on many forums, i even tried to repack my linux kernel but it ends by a non booting system :D

well i burned the iso to a CD at 4x speed, i installed the system, got some errors while copying the files but i just pressed the [retry] button and its gone

now the system boots fine and the msg error was gone...

thanX alot for every one's support

by the way dont get sick while pressing [retry] button just be patient, i pressed that button about 50 or more times ;)

good luck

ah i forgot to appologise for my bad english [shy]

thanX...

---

