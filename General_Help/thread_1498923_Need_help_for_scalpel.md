---
title: "Need help for scalpel"
date: 2010-06-01
forum: General Help
---

### Post by Byb on 2010-06-01
Hi all
Please could somebody help me with scalpel to recover a file I just removed from my .ssh?
At this time it finds 24 matches for the header footer pattern.
```
#/etc/scalpel/scalpel.conf
NONE y 2000 -----BEGIN\sRSA\sPRIVATE\sKEY----- -----END\sRSA\sPRIVATE\sKEY-----
``````
sudo scalpel -c /etc/scalpel/scalpel.conf -o /recup /dev/sdb1
```2 files are ~1500~1700 bytes , all the other are ~900
I'm afraid my ext3 /home/myself partition have been writen by the firefox cache since the remove when I searched how to recover the deleted file.

I'm highly puzzled because I only have a corrupted  backup and several remote routers that only allow ssh+key login from my own private IP address. The strange is that they accept yet the loggin, but the authentication seems longuer than usual. Maybe the private key is yet in some RAM cache on my computer and I am afraid of a power failure.

---

### Post by sedawk on 2010-06-01
Are you sure you had a personal key?
E.g. did you do something like

ssh -i my_pub_idfile user@router in the past?

Or did you do a simple

ssh user@router which uses the system keys that
are stored at /etc/ssh (and not in your home folder under .ssh)?

(I not 100% sure if ssh picks a personal key first if it is
 found in your .ssh folder - if there is such a default
 behaviour I never  used it!).

The (crypted) RSA key is around 1600 bytes and the public key
around 400 bytes.

---

### Post by Byb on 2010-06-01
Yes I'm sure
In the routers' authorized_keys I have only my pub key and they are set to refuse password authentication.

The thing I did yesterday which ran me into trouble: I wanted to begin learning how to enable secure connection like ssh root@routerIP -L port:localhost:port then browse [http://localhost:port](http://localhost:port) instead of my current https+password way or ssh root@routerIP
I couldn't reach to do it with a local test router so I was completly lost and tried to re read all the stuff I forgot since 2 years about ssh. At a time I issued a ```
ssh-keygen -t dsa
``` and I saw the 2 new files id-dsa & id_dsa.pub added to my .ssh folder beside the id_rsa id_rsa.pub and known_hosts. Further as I couldn't still login with ssh -L I decide to forgive with dsa because I supposed errors with ssh -vv -L where related to the presence of the dsa files in my .ssh folder. When I wanted to remove the dsa files with rm, I read the rm help and man and schred also, and I misunderstood the rm -v like "will show what would happen" plus I made the error in the command: rm -v ./id_rsa instead of rm -v ./id_dsa I wanted to test. THis is the problem with english and me, I should I have use the GUI.

Please tell me: I think scapel finds all files (deleted or not) on the drive. I launched a search on the drive to know why he found so many files (up to 77 when I first set max size to 10000 in scalpel conf) I found a lot of binary files with the -----BEGIN RSA PRIVATE KEY inside that are config backups of routers
My aim was to find in which files scalpel could find the full pattern I set in the conf file```
-----BEGIN\sRSA\sPRIVATE\sKEY----- -----END\sRSA\sPRIVATE\sKEY-----
``` that could be ~900 bytes to exclude them from the possible recovered "good files"
How could I check there is something that retained the private key in memory?

What does mean Chop in the audit.txt I saw when maxsize was 10000?

---

