---
title: "I want to make this to work ... Bash Scripting n00b ;)"
date: 2010-06-12
forum: General Help
---

### Post by nikkpap on 2010-06-12
I want to make this to work ... Bash Scripting n00b ;)

can someone help me... and correct this script i want to make !!!

i think its very useful and i don't know how to finish it. 

P.S. can some how make an a subtract of the "date" beginning of the prosses till the end "date" ...... date - date = total time ? i don't know how.

Thank's in Advance 
 nikkpap 
from Greece:lolflag:


#!/bin/bash
# with this little script and with the dselect command you can easyly back up and restore all the soft you install from the community (not the deb's)

date 
sudo apt-get install dselect
echo "
    ************************************************************
    **  N.ikkpap's    A.pplications    B.ackup    U.tility    **
    ************************************************************

          - to Backup all your Applications Press [1] 
          - to Restore all your Application Press [2] 
          - to Exit press                         [e]"  
read SEL1
 if [ $SEL1=1 ]
   then sudo dpkg --get-selections  >  allmysoft.txt
    elif [ $SEL1=2 ] 
     then sudo dpkg --set-selections < allmysoft.txt && sudo apt-get install dselect && sudo dselect update && sudo apt-get dselect-upgrade
   else 
    if [ $SEL1=e ] exit
     elif echo " Press the correct key... ;) "
 fi
date

---

### Post by Arand on 2010-06-12
This is likely the wrong way to go about it, but it works:```
D1=`date +%s`

# this is your script

D2=`date +%s`

# The following works due to bash truncating
SEC=$(( D2 - D1 - ( TIME / 60 ) ))
MIN=$(( TIME / 60 ))
echo "Execution took: "$MIN"min:"$SEC"s"
```- arand

---

### Post by nikkpap on 2010-06-12
sweet .....:popcorn:

thanks for the time messure ... what about the script can you help to fix it

---

### Post by nikkpap on 2010-06-16
This is it Finally i did it...you may use it and edit it thanks 

N.ikkpap's A.pplication B.ackup U.tility with this little script and with the dselect command you can easily back up and restore all the soft you install from the community (not the deb's)

the only think you have to do is to 
$ sudo chmod +x to make it executable 
and run it with double click or 
with $ sudo sh N.U.B.U.sh

[http://www.mediafire.com/?zmmmizymzmh](http://www.mediafire.com/?zmmmizymzmh)

i made all the corrections now it loops correct ;)

ver 1.2 and still going ... give a try its GUI 
[http://www.mediafire.com/file/87a3bgl013e2qgx/N.A.B.U.v.1.2](http://www.mediafire.com/file/87a3bgl013e2qgx/N.A.B.U.v.1.2)

---

### Post by nikkpap on 2010-06-17
@ arad this is the correct way mate yours it messure only in sec like 0min:430sec thanks anyway...
):P
# The following works due to bash truncating
SEC=$(((D2 - D1)%60))
MIN=$((( D2-D1)/60))
echo "Execution took: "$MIN"min:"$SEC"s"

---

