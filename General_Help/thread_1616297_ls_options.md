---
title: "ls options"
date: 2010-11-08
forum: General Help
---

### Post by alin19 on 2010-11-08
I have this piece of code from a bash script
<div class="codetop">[PHP]
        while [ $i -lt $numberofprocess ]
                do
                   if [ `ps ax | grep  index | grep php | grep -c $i` -lt 1 ]; then

                   /home/alin/NetBeansProjects/Fragger2/index.php $i &

                   fi;
                   i=`expr $i + 1`

                   sleep 1
        done[/PHP]I run the php script with an argument and depending of that it saves some data in different files

when i run px axn | grep php | grep index | grep $i, i see that it searches for the php , index and $i in the whole row so it will take the pid and the 2 from the Fragger2 also:

<div class="codetop">[PHP]root@alin-laptop:~# ps axn | grep php | grep index | grep 4
root@alin-laptop:~# ps axn | grep php | grep index | grep 5
 8925 ?        S      0:00 /server/php/bin/php /home/alin/NetBeansProjects/Fragger2/index.php 0
root@alin-laptop:~# ps axn | grep php | grep index | grep 6
root@alin-laptop:~# ps axn | grep php | grep index | grep 7
root@alin-laptop:~# ps axn | grep php | grep index | grep 8
 8925 ?        S      0:00 /server/php/bin/php /home/alin/NetBeansProjects/Fragger2/index.php 0
root@alin-laptop:~# ps axn | grep php | grep index | grep 9
 8925 ?        S      0:00 /server/php/bin/php /home/alin/NetBeansProjects/Fragger2/index.php 0[/PHP]How can i do to get only the index.php $i ?

thanks

---

### Post by alin19 on 2010-11-08
> **alin19 said:**
> I have this piece of code from a bash script
<div class="codetop">[PHP]
        while [ $i -lt $numberofprocess ]
                do
                   if [ `ps ax | grep  index | grep php | grep -c $i` -lt 1 ]; then

                   /home/alin/NetBeansProjects/Fragger2/index.php $i &

                   fi;
                   i=`expr $i + 1`

                   sleep 1
        done[/PHP]I run the php script with an argument and depending of that it saves some data in different files

when i run px axn | grep php | grep index | grep $i, i see that it searches for the php , index and $i in the whole row so it will take the pid and the 2 from the Fragger2 also:

<div class="codetop">[PHP]root@alin-laptop:~# ps axn | grep php | grep index | grep 4
root@alin-laptop:~# ps axn | grep php | grep index | grep 5
 8925 ?        S      0:00 /server/php/bin/php /home/alin/NetBeansProjects/Fragger2/index.php 0
root@alin-laptop:~# ps axn | grep php | grep index | grep 6
root@alin-laptop:~# ps axn | grep php | grep index | grep 7
root@alin-laptop:~# ps axn | grep php | grep index | grep 8
 8925 ?        S      0:00 /server/php/bin/php /home/alin/NetBeansProjects/Fragger2/index.php 0
root@alin-laptop:~# ps axn | grep php | grep index | grep 9
 8925 ?        S      0:00 /server/php/bin/php /home/alin/NetBeansProjects/Fragger2/index.php 0[/PHP]How can i do to get only the index.php $i ?

thanks

fix it :

root@alin-laptop:~# ps axo cmd | grep index | grep 0

---

