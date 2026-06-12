---
title: "Updating etc hosts file using shell script fails"
date: 2009-10-20
forum: General Help
---

### Post by peterramesh on 2009-10-20
Hi, I'am trying to edit /etc/hosts file of some machine using shell script.

This following script works with a temporary file, but testing against /etc/hosts file instead of /home/hadoop/hosts/hosts fails, I'm getting permission denied error..  like ****sed: couldn't open temporary file /etc//sedegcf3f: Permission denied****

hadoop@master:sed$ cat applyhadoopcluster.sh
#!/bin/bash
for i in `cat clusternodes`
do
        # Remove the exiting entiries of Hadoop cluster, if any
        ssh hadoop@$i "sed '/#HADOOP_HOST_ENTRIES_STARTING/,/#HADOOP_HOST_ENTRIES_ENDING/d' /home/hadoop/hosts/hosts -i"

        # Insert the Hadoop cluster entries
        ssh hadoop@$i "sed '1i\#HADOOP_HOST_ENTRIES_STARTING' /home/hadoop/hosts/hosts -i"
        count=2
        while read j
        do
                #echo $j
                ssh -n hadoop@$i "sed '2i$j' /home/hadoop/hosts/hosts -i"
                count=`expr $count + 1`
                #echo $count
        done < clusterhostnames
        ssh hadoop@$i "sed ${count}i\#HADOOP_HOST_ENTRIES_ENDING /home/hadoop/hosts/hosts -i"
done

hadoop@master:sed$ cat clusterhostnames
172.25.149.37  master
172.25.149.38  slave2
172.25.149.66   slave1

hadoop@master:sed$ cat clusternodes
master
slave2
slave1

hadoop@master:sed$ ls -alt /home/hadoop/hosts/hosts 
-rw-r--r-- 1 hadoop hadoop 160 2009-10-20 17:00 /home/hadoop/hosts/hosts

hadoop@master:sed$ ls -alt /etc/hosts
-rw-rw-r-- 1 root root 551 2009-10-08 15:12 /etc/hosts

---

### Post by The Cog on 2009-10-20
The script needs to run as root in order to have the rights to edit that file. If running the script by hand, try:
**sudo applyhadoopcluster.sh**

---

