---
title: "92% usage on &quot;/var/lib/ureadahead/debugfs&quot;"
date: 2010-04-13
forum: General Help
---

### Post by tuxulin on 2010-04-13
i was running ubuntu 9.4 previously and a few days ago i upgraded to 10.04
everything appears to be perfect.
however i ran df -h and was surprised that i had 3.7G remaining on 
the /
i went to my home directory and moved out 15Gig and executed df -h again
the result is the same 3.7G remaining.

i went to "/var/lib/ureadahead/debugfs" only to find nothing in there
and at one level up "/var/lib/ureadahead" there is a file called "pack"
which is 768.6Kb in size.

after moving files from the home directory i did a property check on it
and the home folder is 3.8Gg used

im confused as to 
1, what is eating my HDD space ?
2, is "/var/lib/ureadahead/debugfs" misleading the sytem
3, is this a bug ?

**_PLEASE NOTE_**
yes i did search this and other sites but nothing that is concrete 
to help in my situation.

yes im using ubuntu 10.04 but up till a few days ago it has been
9.4 so im guessing this problem didn't suddenly appear since the 
installation of 10.04
 

after running a df -h this the results i get
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb6              49G   43G  3.7G  92% /
none                  940M  304K  939M   1% /dev
none                  944M  184K  944M   1% /dev/shm
none                  944M  328K  943M   1% /var/run
none                  944M     0  944M   0% /var/lock
none                  944M     0  944M   0% /lib/init/rw
none                   49G   43G  3.7G  92% /var/lib/ureadahead/debugfs
/dev/sdb2              74G   16G   55G  22% /media/Lin80g
/dev/sda1              37G   12G   25G  33% /media/082C02262C020EFE

thanks any help will do
Tuxulin

---

### Post by tuxulin on 2010-04-13
up

---

