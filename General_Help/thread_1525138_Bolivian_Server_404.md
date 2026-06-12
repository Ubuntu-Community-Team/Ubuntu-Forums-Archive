---
title: "Bolivian Server 404"
date: 2010-07-06
forum: General Help
---

### Post by IamNot on 2010-07-06
Hello there, I don't know if a lot of member from the Bolivian community use linux ubuntu or not, but I know is awesome and everyone should. I have a question: the [http://bo.archive.ubuntu.com/](http://bo.archive.ubuntu.com/) means the server is in bolivia? if that's the case I think something is wrong with it since last night. I'm trying to update my ubuntu using the update tool and i get this message

W: Failed to obtain [http://bo.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc-bin_2.11.1-0ubuntu7.2_i386.deb](http://bo.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc-bin_2.11.1-0ubuntu7.2_i386.deb)
  404  Not Found


W: Failed to obtain [http://bo.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6_2.11.1-0ubuntu7.2_i386.deb](http://bo.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6_2.11.1-0ubuntu7.2_i386.deb)
  404  Not Found


W: Failed to obtain [http://bo.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-i686_2.11.1-0ubuntu7.2_i386.deb](http://bo.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-i686_2.11.1-0ubuntu7.2_i386.deb)
  404  Not Found

and like 50 more of those. Also, can't get the driver for my videocard because i get the same message. I'm using ubuntu 10.4 on a laptop wich is an acer aspire 3517. my videocard is an ATI 3200 but i don't think is a hardware problem since I could update some of the software i need and the apt-get comand was working fine. Probably the bolivian server is just missing those files. Any tips on how to modify the [http://bo.a](http://bo.a)... at least temporarily so i can get my videocard driver at least? appreciate it, thank you.

---

### Post by mkvnmtr on 2010-07-06
You can change the server you are using in software sources. I am in Mexico and find the server in the US is normally faster for me.

---

### Post by IamNot on 2010-07-06
ok this is what i did. On the updates window click configuration, go to the ubuntu software tab and there change the download from option to main server.

---

