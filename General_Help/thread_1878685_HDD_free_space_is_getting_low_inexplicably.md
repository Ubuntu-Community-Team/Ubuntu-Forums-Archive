---
title: "HDD free space is getting low inexplicably"
date: 2011-11-10
forum: General Help
---

### Post by Dimas on 2011-11-10
In our company we've an Ubuntu Server 10.10 64bits as a Apache and MySQL server.

We have a serious problem. Our free space is getting low! Every time I check it is lower, and we don't know what is wasting this space.

I think something is wrong with our Ubuntu. If I check the space with _df_ it shows us that we have about 70Gb in use (92%). But when I try du _--max-depth=1 -h_ to check which folder is the big one it says that in total we have 13G occuped. ?¿?¿?¿

And one last thing... if we reboot the server, surprise! _df_ now says we only have 13G occuped! We did a reboot one month ago, and now we are at 92% already. Reboot the server every month isn't a good solution for us.

Any help?

**_df_ output**
S. fitxers         Blocs   1K     En Ãºs   Lliures  %Ãs Muntat a
/dev/sda1             79616888  68863628   6708872  92% /

**_du --max-depth=1 -h_ output**
23M     ./boot
63M     ./mnt
6,0M    ./sbin
4,0K    ./selinux
7,7M    ./bin
2,3M    ./build
172M    ./root
4,0K    ./srv
1,3G    ./usr
du: no sâha pogut accedir a Â«./proc/8474/task/8474/fd/3Â»: El fitxer o directori no existeix
du: no sâha pogut accedir a Â«./proc/8474/task/8474/fdinfo/3Â»: El fitxer o directori no existeix
du: no sâha pogut accedir a Â«./proc/8474/fd/3Â»: El fitxer o directori no existeix
du: no sâha pogut accedir a Â«./proc/8474/fdinfo/3Â»: El fitxer o directori no existeix
0       ./proc
12K     ./media
173M    ./lib
3,6M    ./home
11G     ./var
1,1G    ./opt
96K     ./tmp
152K    ./dev
16K     ./lost+found
25M     ./etc
0       ./sys
4,0K    ./stage
13G     .

---

### Post by dcstar on 2011-11-11
> **Dimas said:**
> In our company we've an Ubuntu Server 10.10 64bits as a Apache and MySQL server.

We have a serious problem. Our free space is getting low! Every time I check it is lower, and we don't know what is wasting this space.


Look at the size** and** content of the log files.

---

### Post by mcduck on 2011-11-11
There's 13 GB of data i root directory itself. Make sure you haven't configured any backup solution or similar to save data there.

...actually anything saving directly to / is probably misconfigured. ;)

and of course you should run the du command with sudo, otherwise it won't have the permissions required to scan everything.

Also reboot clearing that much space could indicate that the space was either used by something stored in /tmp, or that there might have been some error that has caused lots of messages in some log file, and the old insanely large log file was deleted on the reboot by the normal log rotation mechanism clearing the space. Since it's a web server the 11GB size of /var alone doesn't tell if that's the case or not, you might want to check the size of /var/log and of course monitor it over time (or just check that none of the log files there is too large).

---

### Post by Dimas on 2011-11-11
I don't think so :(

root@zeus:/var/log# du --max-depth=1 -h
4,0K    ./news
92K     ./mysql
4,0K    ./dist-upgrade
100K    ./apt
4,0K    ./apparmor
12K     ./fsck
64K     ./ConsoleKit
22M     ./samba
1,2M    ./installer
285M    ./apache2
531M    .

I entered some of these folders and I can't view nothing strange.

Today we have only 3gb free, yesterday 7gb!! :-(((

---

### Post by dcstar on 2011-11-11
> **Dimas said:**
> I don't think so :(

root@zeus:/var/log# du --max-depth=1 -h
4,0K    ./news
92K     ./mysql
4,0K    ./dist-upgrade
100K    ./apt
4,0K    ./apparmor
12K     ./fsck
64K     ./ConsoleKit
22M     ./samba
1,2M    ./installer
285M    ./apache2
531M    .

I entered some of these folders and I can't view nothing strange.

Today we have only 3gb free, yesterday 7gb!! :-(((

**You** have to look at the individual log files, **you** have to look in any large log files to find out why they may be large.

No one else is going to do this for you.

---

### Post by Dimas on 2011-11-11
> **mcduck said:**
> There's 13 GB of data i root directory itself. Make sure you haven't configured any backup solution or similar to save data there.

...actually anything saving directly to / is probably misconfigured. ;)

Not really. The root directory is empty, the 13Gb of data are the sum of all other folders (man _du_)

> **mcduck said:**
> and of course you should run the du command with sudo, otherwise it won't have the permissions required to scan everything.

I made it with user root, no problem with that.

> **mcduck said:**
> Also reboot clearing that much space could indicate that the space was either used by something stored in /tmp, or that there might have been some error that has caused lots of messages in some log file, and the old insanely large log file was deleted on the reboot by the normal log rotation mechanism clearing the space. Since it's a web server the 11GB size of /var alone doesn't tell if that's the case or not, you might want to check the size of /var/log and of course monitor it over time (or just check that none of the log files there is too large).

/tmp directory is almost empty. du says is 96k, and it's true.

The 11gb of /var is normal, we store many webs, intranets and a lot of files. But that's normal!

In /var/log I can't view nothing strange. I checked various big log files with no recursive or strange errors. And as big files I mean files over 200mb, and that's acceptable.

---

### Post by Dimas on 2011-11-11
> **dcstar said:**
> **You** have to look at the individual log files, **you** have to look in any large log files to find out why they may be large.

No one else is going to do this for you.

Yes, I **looked **the big files, but there isn't nothing strange there. All log files are 500mb, the big one is 200mb. That doesn't explain the 60gb occuped reported by _df_ and the only 13gb reported by _du_.

---

