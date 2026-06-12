---
title: "file transfer through samba"
date: 2012-09-11
forum: General Help
---

### Post by saders on 2012-09-11
Hello all,


           i have written scrot script to take screen shot as mentioned below but i want to move the screen shots to a NETWORK folder so any suggestions on how to do it?


SCROT to take screen shot per 20secs :

i wanna move this address :

192.168.1.111 : my IP

hitachi (d)\BANG -1\1st Floor\Sys-27 : sub folders to categorize
 
>>>> \\192.168.1.111\hitachi (d)\BANG -1\1st Floor\Sys-27 <<<<


tfsystemseven_dir='tfsystemseven';
seconds='30';
if [ ! -d "$tfsystemseven_dir" ]; then
mkdir $tfsystemseven_dir;
fi
while true; do
sleep 20;
(scrot -q 40 $tfsystemseven_dir/user7-$(date +%k.%M.%S_%d.%m.%Y|sed -e 's/^ *//').jpg) &
done


to move the screen logs to a folder within computer :

          #!/bin/bash
while true; do
sleep 0;
mv /home/user7/tfsystemseven/*.jpg /home/pc7/Downloads/tfsystemseven/ &
done


thanks in advance..

---

