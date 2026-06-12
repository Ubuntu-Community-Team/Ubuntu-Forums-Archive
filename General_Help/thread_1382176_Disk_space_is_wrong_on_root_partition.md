---
title: "Disk space is wrong on root partition"
date: 2010-01-15
forum: General Help
---

### Post by jmz2 on 2010-01-15
Hello,

My root partition seems to be full bur is wrong because I have a partition with 15Gb space and the data is arround 7.5Gb

I have:

> ~$ [PHP]sudo df -lha
S.ficheros            Tamaño Usado  Disp Uso% Montado en
/dev/sda5              15G   14G  660M  96% /
proc                     0     0     0   -  /proc
/sys                     0     0     0   -  /sys
varrun               1014M  244K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M  108K 1014M   1% /dev
devshm               1014M   48K 1014M   1% /dev/shm
devpts                   0     0     0   -  /dev/pts
lrm                  1014M   40M  975M   4% /lib/modules/2.6.24-24-generic/volatile
/dev/sdc5             384G  379G  4,9G  99% /media/COMPARTIDO
/dev/sdb1              30G   19G   11G  64% /media/W2K3
/dev/sda7             171G   28G  143G  17% /media/rsyncBACKUP
securityfs               0     0     0   -  /sys/kernel/security
overflow              1,0M  1,0M     0 100% /tmp
truecrypt                0     0     0   -  /tmp/.truecrypt_aux_mnt1
/dev/mapper/truecrypt1
                       34G   30G  3,0G  91% /home
truecrypt                0     0     0   -  /tmp/.truecrypt_aux_mnt2
/dev/mapper/truecrypt2
                      119G   93G   21G  82% /media/BACKUP
binfmt_misc              0     0     0   -  /proc/sys/fs/binfmt_misc[/PHP]


When I look for specific info about what is taking the space using du command I get that the space used by the root system is 7.2Gb. I get to the same conclusion when checking the space with Nautilus.

this seems some kind of error. Can somebody help me with this?

Thanks

---

### Post by oldfred on 2010-01-15
I have these notes:

HouseKeeping:
sudo apt-get update 
sudo apt-get upgrade 
sudo apt-get autoremove
# removes .deb
sudo apt-get autoclean
Sometimes this does more?
sudo apt-get dist-upgrade

 How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

[URL="http://ubuntuforums.org/showthread.php?t=898573"]
[/URL]

---

### Post by jmz2 on 2010-01-17
> **oldfred said:**
> I have these notes:

HouseKeeping:
sudo apt-get update 
sudo apt-get upgrade 
sudo apt-get autoremove
# removes .deb
sudo apt-get autoclean
Sometimes this does more?
sudo apt-get dist-upgrade

 How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

[URL="http://ubuntuforums.org/showthread.php?t=898573"]
[/URL]


Thanks.

I already followed those steps before posting. What it is surprising is that my partition should be no more than 7.5Gb /as 'du' command says and 'df' command is saying 100% full.

Is this a bug or something?

---

