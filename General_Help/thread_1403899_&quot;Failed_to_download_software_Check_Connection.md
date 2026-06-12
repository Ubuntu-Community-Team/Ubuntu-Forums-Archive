---
title: "&quot;Failed to download software: Check Connection&quot;"
date: 2010-02-10
forum: General Help
---

### Post by miggerish on 2010-02-10
Using the Ubuntu Software Center Program to get a prgram called "Cheese", and it stopped in middle and said could not get software check internet connection.

Details are as follows:


"Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cheese/cheese_2.28.1-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cheese/cheese_2.28.1-0ubuntu1_i386.deb) Could not connect to localhost:8118 (127.0.0.1). - connect (111: Connection refused)"

Please help.  Internet and everything else works.  I am in firefox browsing the web it works.  I have Tor Button in firefox but it is completely deactivated.

---

### Post by sandyd on 2010-02-10
> **miggerish said:**
> Using the Ubuntu Software Center Program to get a prgram called "Cheese", and it stopped in middle and said could not get software check internet connection.

Details are as follows:


"Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cheese/cheese_2.28.1-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cheese/cheese_2.28.1-0ubuntu1_i386.deb) Could not connect to localhost:8118 (127.0.0.1). - connect (111: Connection refused)"

Please help.  Internet and everything else works.  I am in firefox browsing the web it works.  I have Tor Button in firefox but it is completely deactivated.

you have to disable tor for the entire system.
apt-get is still using tor to connect to the internet.

---

### Post by miggerish on 2010-02-11
solved thanks

---

