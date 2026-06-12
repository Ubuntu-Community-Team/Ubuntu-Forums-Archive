---
title: "Ubuntu 10.10"
date: 2011-04-04
forum: General Help
---

### Post by kahamorf on 2011-04-04
Hi guyz. I'm new in ubuntu and i have a "noob" question. The programs from Ubuntu Software Center have no difference with the packages from the Synaptic Package Manager?

---

### Post by ~Plue on 2011-04-04
> **kahamorf said:**
> The programs from Ubuntu Software Center have no difference with the packages from the Synaptic Package Manager?
yes, they both are frontends to APT and access the same repositories

---

### Post by kahamorf on 2011-04-04
Ok. If i want to keep ubuntu 10.10 for a long time and i dont want to upgrade to ubuntu 11.04 my downloaded packages will upgrade to another newest version?

---

### Post by DeMus on 2011-04-04
> **kahamorf said:**
> Ok. If i want to keep ubuntu 10.10 for a long time and i dont want to upgrade to ubuntu 11.04 my downloaded packages will upgrade to another newest version?

Using 10.10 for a long time is not possible. (well what is a long period?) The 10.10 version has a life-time of 18 months so it will end April 2012. This means no more updates.
Before that it might be that some programs get an update which you can install, but most of the programs in Synaptic package manager will stay the same. So if you want to have the newest, latest, coolest versions you have to update your OS and hope the latest versions are included in there.
On the other hand, what is wrong with keeping a solid version for a longer period of time. I use 10.04 in the LinuxMint 9 version and it is updated until April 2013 since it is an LTS (Long Term Support) version. All the first bugs are gone and now it is rock solid. I don't need the latest version because I know it will have bugs. Installing an OS can be nice but doing it day after day might get boring.
I hope I could have helped you in some way.

---

### Post by ~Plue on 2011-04-04
> **kahamorf said:**
> Ok. If i want to keep ubuntu 10.10 for a long time and i dont want to upgrade to ubuntu 11.04 my downloaded packages will upgrade to another newest version?
not exactly. each ubuntu release has a separate repository and canonical doesn't always keep the software up to date  with already released versions, they usually only provide security updates and such.

// so if you really want the newest/latest software from the repos, then you'll need to use unofficial repositories or switch to a rolling distro

---

### Post by kahamorf on 2011-04-04
I will keep the updates and the programs that i use until that day and i will keep ubuntu 10.10 because it is stable for my laptop.

---

### Post by Dupointx on 2011-04-04
> **kahamorf said:**
> I will keep the updates and the programs that i use until that day and i will keep ubuntu 10.10 because it is stable for my laptop.

If you know a particular program that has updates that you want you may be able to add a PPA (Personal Package Archive) that will keep it updated.

---

### Post by kahamorf on 2011-04-04
Ok,thank you guyz. If i need somethink else i will post here.

---

### Post by kahamorf on 2011-04-04
Guyz when i was formating my hard disk to install ubuntu i choose to Specify partitions manually and no the option Erase and use entire disk. My hard disk is 320 gb. I use 4gb for swap, 500mb for /boot and the rest space for /. Should i use the option Erase and use the entire disk for better hdd speed or i am ok? I'm asking this because i think when i restart my laptop is a little bit slower than the other time.I just want a better opinion.Thanks.

---

### Post by Dupointx on 2011-04-04
> **kahamorf said:**
> Guyz when i was formating my hard disk to install ubuntu i choose to Specify partitions manually and no the option Erase and use entire disk. My hard disk is 320 gb. I use 4gb for swap, 500mb for /boot and the rest space for /. Should i use the option Erase and use the entire disk for better hdd speed or i am ok? I'm asking this because i think when i restart my laptop is a little bit slower than the other time.I just want a better opinion.Thanks.

I use ext4 for / since its the fastest. /boot should be ext2, 3, or 4 I typically only specify /; I don't care about separating boot from /. It is a good idea to separate /home from /. that way if your install gets broken you can just re-install and keep /home intact. What really matters is where your install is on the drive platter. The faster side of the drive is the left while the right is slower.

To see your platter open Gparted. The graphical representation is what I'm talking about. Ideally you want /boot to be the very left, then /, and then /home. / should be about 20Gb and /home should be the rest of the space. 

linux-swap should be the last on the platter. For swap space you only need 2 times your RAM ***at the most***. Your computer will probably never use swap unless you have less than 512mb RAM or you tell Ubuntu to hibernate.

---

### Post by kahamorf on 2011-04-04
So i have to reinstall ubuntu?

---

### Post by Dupointx on 2011-04-04
> **kahamorf said:**
> So i have to reinstall ubuntu?
If you want to.

Your set up should work the way it is right now according to what you just said. I'm just stating what would be the fastest ***in my opinion***.

It could be possible that my way is faster, or it may not be noticeably faster for you (I don't know your hardware or how this would affect it). I cannot predict what will be the outcome, but I do know that the partition scheme I just laid out works well for me.

---

### Post by linuxnewb2 on 2011-04-04
I agree with [DeMus]("http://ubuntuforums.org/member.php?u=576559")

Partly because what she said makes perfect sense. Also partly cuz Im running LinuxMint 10. lol ... Which imo, is so much better in terms of user friendly linux, than ubuntu 10.10 ... Which I tried it and found it to be a horrid layout by default.

---

### Post by kahamorf on 2011-04-04
Aha ok. I will see if its ok for some dayz and i will reinstall if i have to. I have one more question for now :). What ever i download from Synaptic package manager in /var/cache/apt/archive can be deleted by itself? In Settings - Preferences - Files i choose the option "Leave all downloads packages in the cache".

---

### Post by ezsit on 2011-04-04
> So i have to reinstall ubuntu?

Only if you want to. You can run 10.10 well past the EOL (end of life) - it will continue to function just fine whether receiving updates or not. You can easily get away with running any Linux far past its expiration date - it's not Windows and will not go sour after a certain point.

Certain peeps my tell you never to run an OS that is not currently supported, but that is totally subjective. If you are running a home system and keep backups of your data, run however you want and most likely will never experience a security breach. If you are the truly paranoid, then change your underwear every 6 months like the majority.

---

### Post by kahamorf on 2011-04-10
Can someone tell me how to partition my 320GB hdd for ubuntu?

---

### Post by ~Plue on 2011-04-10
> **kahamorf said:**
> Can someone tell me how to partition my 320GB hdd for ubuntu?
depends on your preference.

 if you'd like to keep a separate /home and store the data there
~15-20 gb - mount point /
X1.5 the amount of ram  - swap (or you could use a swap file)
the rest of the space -   mount point /home

or if you want to keep the data on a separate partition, instead of making a separate /home, make a data partition once installed and make symlinks in your home folder to folders/files on that partition

you could make indivudual mount points for /tmp , /boot, /usr etc.. but that would make little or no difference for a normal desktop user

---

### Post by kahamorf on 2011-04-10
15-20 GB for / is for the programs and installs?

---

### Post by ~Plue on 2011-04-10
> **kahamorf said:**
> 15-20 GB for / is for the programs and installs?
yes, that would be plenty if you aren't planning to install everything in the repos ;)
but since it's just a preference, increasing/decreasing the size wouldn't hurt

(however the applications/games that you install using wine/cedega would be in your home directory)

---

### Post by kahamorf on 2011-04-10
I put 4GB swap, 20GB / and the rest from 320GB for /home and after format i was having 3.7GB swap, 15.4GB / and 257.4GB for /home. Why? The rest of GBs where are they?

---

### Post by ~Plue on 2011-04-10
> **kahamorf said:**
> I put 4GB swap, 20GB / and the rest from 320GB for /home and after format i was having 3.7GB swap, 15.4GB / and 257.4GB for /home. Why? The rest of GBs where are they?
could you post the terminal output of[I];
df -h [/I][I]
sudo fdisk -l [/I]
free -m

edit: its worth noting that even if the harddrive is labeled as 320gb, the actual capacity would be lower
1 gigabytes = 1 073 741 824 bytes
320 000 000 000 bytes (how the manufacturers calculate 320 gb) divided by 1 073 741 824 bytes** = **298gb
[check here]("http://en.wikipedia.org/wiki/Megabyte")

but even some of that seems to be lost..

---

### Post by kahamorf on 2011-04-10
After simple format with option Erase and use entire disk:
df -h   Filesystem            Size  Used Avail Use% Mounted on
           /dev/sda1             290G  2.1G  273G   1% /
          none                  741M  252K  740M   1% /dev
          none                  746M  324K  746M   1% /dev/shm
          none                  746M   88K  746M   1% /var/run
          none                  746M     0  746M   0% /var/lock
          none                  290G  2.1G  273G   1% /var/lib/ureadahead/debugfs

---

### Post by ~Plue on 2011-04-10
> **kahamorf said:**
> Size  Used Avail Use% Mounted on
           /dev/sda1             *290G*  2.1G  273G   1% /
          
thats looks the right amount, minus the space that would be taken by swap

to know what went wrong when you partitioned manually, the output then would've been helpful

---

