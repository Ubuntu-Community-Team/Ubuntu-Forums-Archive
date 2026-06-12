---
title: "How to install add-on update for Java"
date: 2012-07-20
forum: General Help
---

### Post by rickm1945 on 2012-07-20
In Firefox add-ons I had a message that my Java was outdated and disabled. How do I update Java? I downloaded it 64 bit version to archive manager then I extracted it to the Desktop.

To install I typed in the terminal
sudo apt-get install jre1.7.0_05
the output

E: Unable to locate package jre1.7.0_05
E: Couldn't find any package by regex 'jre1.7.0_05'
richard@richard-HP-Pavilion-g6-Notebook-PC:~/Desktop$ 
What am I doing wrong?
How do I put these in a code box?

---

### Post by QIII on 2012-07-20
Please see the wiki in my signature and look for the link "Using webupd8.org's strikingly simple method" in the Oracle Java 7 section.

You are making this too hard on yourself.

---

### Post by rickm1945 on 2012-07-20
> **QIII said:**
> Oracle withdrew all licensing for anyone (including Microsoft) to keep Oracle Java in their repos.  Downloading and installing from Oracle is needlessy difficult and not necessary with Ubuntu.

Please see the wiki in my signature and look for the link "Using webupd8.org's strikingly simple method" in the Oracle Java 7 section.

Their PPA does not contain Oracle Java, but automates the installation process.  It also automatically updates to new versions as Oracle releases them.

I ran script, output here:
[HTML][/HTML]richard@richard-HP-Pavilion-g6-Notebook-PC:~$ cd ~/
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ wget [https://github.com/flexiondotorg/oab-java6/raw/0.2.4/oab-java.sh](https://github.com/flexiondotorg/oab-java6/raw/0.2.4/oab-java.sh) -O oab-java.sh
--2012-07-20 14:41:05--  [https://github.com/flexiondotorg/oab-java6/raw/0.2.4/oab-java.sh](https://github.com/flexiondotorg/oab-java6/raw/0.2.4/oab-java.sh)
Resolving github.com (github.com)... 207.97.227.239
Connecting to github.com (github.com)|207.97.227.239|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: [https://raw.github.com/flexiondotorg/oab-java6/0.2.4/oab-java.sh](https://raw.github.com/flexiondotorg/oab-java6/0.2.4/oab-java.sh) [following]
--2012-07-20 14:41:05--  [https://raw.github.com/flexiondotorg/oab-java6/0.2.4/oab-java.sh](https://raw.github.com/flexiondotorg/oab-java6/0.2.4/oab-java.sh)
Resolving raw.github.com (raw.github.com)... 207.97.227.243
Connecting to raw.github.com (raw.github.com)|207.97.227.243|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 22783 (22K) [text/plain]
Saving to: `oab-java.sh'

100%[======================================>] 22,783      --.-K/s   in 0.04s   

2012-07-20 14:41:07 (495 KB/s) - `oab-java.sh' saved [22783/22783]

richard@richard-HP-Pavilion-g6-Notebook-PC:~$ chmod +x oab-java.sh
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ sudo ./oab-java.sh
[sudo] password for richard: 
Sorry, try again.
[sudo] password for richard: 
oab-java.sh v0.2.4 - Create a local 'apt' repository for Sun Java 6 and/or Oracle Java 7 packages.

Copyright (c) Martin Wimpress, [http://flexion.org](http://flexion.org). MIT License

By running this script to download Java you acknowledge that you have
read and accepted the terms of the Oracle end user license agreement.

* [http://www.oracle.com/technetwork/java/javase/terms/license/](http://www.oracle.com/technetwork/java/javase/terms/license/)

If you want to see what this is script is doing while it is running then execute
the following from another shell:

  tail -f /home/richard/oab-java.sh.log

 [x] Installing Java build requirements success
 [x] Making build directories success
 [x] Removing clones of [https://github.com/rraptorr/sun-java6](https://github.com/rraptorr/sun-java6) success
 [x] Cloning [https://github.com/rraptorr/sun-java6](https://github.com/rraptorr/sun-java6) success
 [x] Checking out v6.33-2 success
 [x] Getting Java SE download page success
 [x] Getting current release download page success
 [x] Downloading jdk-6u33-linux-i586.bin : 68.42 MB success
 [x] Symlinking jdk-6u33-linux-i586.bin success
 [x] Downloading jdk-6u33-linux-x64.bin : 68.69 MB success
 [x] Symlinking jdk-6u33-linux-x64.bin success
 [x] Getting Java Cryptography Extension download page success
 [x] Downloading jce_policy-6.zip : 8.89 KB success
 [x] Symlinking jce_policy-6.zip success
 [x] Updating the changelog success
 [x] Building the packages success
ERROR! Packages failed to build.
richard@richard-HP-Pavilion-g6-Notebook-PC:~$ 
[HTML][/HTML]

I have no clue as to what I am doing but I tried.:(

---

### Post by QIII on 2012-07-20
I have edited my previous post for clarity.

You are making this too difficult for yourself.

Furthermore, the method you just tried is attempting to install Java 6 update 33, which is subject to security problems and will reach EOL and be unsupported by Oracle after November 2012.

I wrote a strong recommendation against installing Java 6 in the wiki and explained why and someone else also provided a link to an important announcement to that effect.

---

### Post by rickm1945 on 2012-07-21
> **QIII said:**
> I have edited my previous post for clarity.

You are making this too difficult for yourself.

Furthermore, the method you just tried is attempting to install Java 6 update 33, which is subject to security problems and will reach EOL and be unsupported by Oracle after November 2012.

I wrote a strong recommendation against installing Java 6 in the wiki and explained why and someone else also provided a link to an important announcement to that effect.

I ran the first command and at the end got the error message.
```

```Reading package lists... Done
W: GPG error: [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 68980A0EA10B4DE8
richard@XPS8100:~$ 
```

```
Is this anything to worry about? I have not gone forward from this point.

---

