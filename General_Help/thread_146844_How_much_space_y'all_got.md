---
title: "How much space y'all got?"
date: 2006-03-19
forum: General Help
---

### Post by Rick069 on 2006-03-19
This question just popped into my head and I was just curious. Since some or most of you probably have ubuntu as the only os on you computer, I just wanted to know how much space is it occupying on your hard drive including all your apps? Right now, my installation its taking up about 3.5gb of a 160gb hard drive.

---

### Post by dermotti on 2006-03-19
I think around 3.5 also, but that with like 200 megz of kernels

---

### Post by Digidiz on 2006-03-19
i think mine is taken a smidgen more than that since i installed a lot of thing on mine, but i put mine on one part of a multi partition of at least 25Gb

---

### Post by geekphreak on 2006-03-19
Mine takes up 4.29 GB. Got a lot of Java stuff and it takes more space than most other packages.

---

### Post by towsonu2003 on 2006-03-19
2.9G including 4 kernels (old 386&686 and new 386&686) but excluding home (5G and growing as I use qemu as well).

PS. dual-booting but didn't boot to windows for past 2 months.

---

### Post by Yagisan on 2006-03-19
I do a bit of development work for Ubuntu and Debian, so mine is a bit bigger then usual.
```
(amd64)jamie@doomguy:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/eyagi-root
                       20G  335M   19G   2% /
tmpfs                 752M  8.0K  752M   1% /dev/shm
tmpfs                 752M   14M  739M   2% /lib/modules/2.6.12-10-amd64-k8/volatile
/dev/md0              177M   21M  147M  13% /boot
/dev/mapper/eyagi-home
                      233G  194G   40G  84% /home
/dev/mapper/eyagi-opt
                       80G   18G   63G  22% /opt
/dev/mapper/eyagi-temp
                       10G  9.9M   10G   1% /tmp
/dev/mapper/eyagi-usr
                       20G  9.2G   11G  46% /usr
/dev/mapper/eyagi-var
                      6.0G  447M  5.6G   8% /var

```

---

### Post by public_void on 2006-03-19
My Ubuntu install is on a 6.1 GB partition, with 0.9 GB left.

---

### Post by Yagisan on 2006-03-19
I have an ubuntu install on a test box. It's rather cramped only a 2GB disk.
```
jamie@imp:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             1.9G  1.5G  453M  77% /
tmpfs                  70M     0   70M   0% /dev/shm
tmpfs                  70M   13M   58M  18% /lib/modules/2.6.12-10-386/volatile
```
Otherwise a rather usable system.

---

### Post by hyg53 on 2006-03-19
/ is about 4.5GB, after one year installing and unistalling softwares.

---

### Post by Jedeye on 2006-03-19
```
jon@dapper:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              48G  4.3G   42G  10% /
varrun               1014M  136K 1014M   1% /var/run
varlock              1014M  4.0K 1014M   1% /var/lock
udev                 1014M  220K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
/dev/hda1              56G  4.5G   49G   9% /media/Breezy
/dev/hdb1             151G   23G  121G  16% /media/Alpha

```

---

### Post by Ramses de Norre on 2006-03-19
I have used 105gig out of 320.
But almost half of it are music files.

---

### Post by christhemonkey on 2006-03-19
I use about 2 gigs on a 10gb partition for ubuntu, all on an 80 gig harddrive.
(bloated windows taking up 65 gigs....though to be fair it is mainly music)

---

### Post by jerrykenny on 2006-03-19
2.7 Gb, out of a possible 5 Gb on my root partition . . . . 

But were all carrying a certain amount of extra space with our downloaded package files . . . which may not be flushed yet . . . 

I cant remember the command now, I think its

sudo apt-get clean


Public Void, you definitely want to check that out . . . .

---

