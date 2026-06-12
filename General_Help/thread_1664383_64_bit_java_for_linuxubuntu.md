---
title: "64 bit java for linux/ubuntu"
date: 2011-01-10
forum: General Help
---

### Post by neokyle on 2011-01-10
I need to install 64 bit java on my server which is running ubuntu 9.10 64 bit.

I cant find a download link for 64 bit java anywhere, can anyone link me?

Also i do i install java once i have the download link. just do:

apt-get install [Http://www.XXXXXX.xom](Http://www.XXXXXX.xom) right?

thanks in advance :)

---

### Post by WorMzy on 2011-01-10
Java is in the repos.

```
sudo apt-get install default-jre
```

---

### Post by neokyle on 2011-01-10
> **WorMzy said:**
> Java is in the repos.

```
sudo apt-get install default-jre
```

but thats not 64 bit isi t? i know 32 bit will run on a 64 bit system but what im runnig on my server requires the 64 bit jdk.

---

### Post by WorMzy on 2011-01-10
If you are on 64-bit Ubuntu, apt-get will fetch and install the 64-bit packages; if you are on 32-bit, it will install the 32-bit packages.

Once it's installed, you can check by running (in a terminal)
```
java -version
```

You should see something like 

```
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.3) (ArchLinux-6.b20_1.9.3-1-x86_64)
OpenJDK 64-Bit Server VM (build 17.0-b16, mixed mode)
```

---

### Post by neokyle on 2011-01-10
> **WorMzy said:**
> If you are on 64-bit Ubuntu, apt-get will fetch and install the 64-bit packages; if you are on 32-bit, it will install the 32-bit packages.

Once it's installed, you can check by running (in a terminal)
```
java -version
```

You should see something like 

```
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.3) (ArchLinux-6.b20_1.9.3-1-x86_64)
OpenJDK 64-Bit Server VM (build 17.0-b16, mixed mode)
```

thank you, that worked and installed 64 bit java. i appreciate the help :)

---

