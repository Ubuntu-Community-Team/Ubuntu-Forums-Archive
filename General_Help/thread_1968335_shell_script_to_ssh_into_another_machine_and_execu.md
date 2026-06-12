---
title: "shell script to ssh into another machine and execute commands"
date: 2012-04-28
forum: General Help
---

### Post by olithraz on 2012-04-28
So have a problem that I thought would be easy to solve. It isn't apparently. I have 6 machines all linux based that back up to a centralized NAS using rsync. This is all fine and dandy, but doesn't give me versioned backups.

Currently my backup scripts look like this:

```

rsync -e ssh -varuzP --delete --exclude ".*" --exclude "Ubuntu\ One" /home/olithraz olithraz@192.168.1.123:/home/olithraz/NAS/machinename/day1/

```This works great and I haven't had any problems. It uses chron to run it every 24 hours. 

What I want to do, is before it gets to the rsync part of the script is the following:

```

ssh olithraz@192.168.1.123 (uses rsa keys so no password needed)
cd NAS/machinename
rm -rf day7/
mv day6/ day7
mv day5/ day6/
mv day4/ day5/
mv day3/ day4/
mv day2/ day3
cp day1/ day2/
exit

```In effect giving me 7 days of backups. However, I cannot seem to get it to execute commands after sshing... How would I go about doing this or is there an easier way to accomplish this?


What I have considered is on the NAS, just having it run a script to take everything within /NAS/ and copy it for 7days, but I would much rather have it be individual.


Thanks for the help!

---

### Post by codemaniac on 2012-04-29
Hello olithraz ,
Welcome to the Ubuntuforums !!!

try adding some sleep after your ssh command .
```

ssh olithraz@192.168.1.123 (uses rsa keys so no password needed)
sleep 5000(try out different numbers)
cd NAS/machinename
rm -rf day7/
mv day6/ day7
mv day5/ day6/
mv day4/ day5/
mv day3/ day4/
mv day2/ day3
cp day1/ day2/
exit
```

---

### Post by olithraz on 2012-04-29
I tried that, but it did not work. 

I neglected to put it into my post that what is happening is upon running the script, it simply drops me at the terminal logged onto the remote machine. 

Really what I need is a way to pipe the copying and moving into an ssh session, then exit.

Right now running it gets me to olithraz@192.168.1.123:~$

When I type exit to close this it then attempts to move the folders and can't find them because it is executing it locally rather than remotely.

I think what I need is one well placed 'echo', but I have no idea where.

---

### Post by codemaniac on 2012-04-29
> **olithraz said:**
> I tried that, but it did not work. 

I neglected to put it into my post that what is happening is upon running the script, it simply drops me at the terminal logged onto the remote machine. 

Really what I need is a way to pipe the copying and moving into an ssh session, then exit.

Right now running it gets me to olithraz@192.168.1.123:~$

When I type exit to close this it then attempts to move the folders and can't find them because it is executing it locally rather than remotely.

I think what I need is one well placed 'echo', but I have no idea where.

put your commands you want to execute on the remote machine , on a bash script .and try below locally .
```
ssh olithraz@192.168.1.123 'bash -s' < your_script.sh
```

contents of your_script.sh
```
cd NAS/machinename
rm -rf day7/
mv day6/ day7
mv day5/ day6/
mv day4/ day5/
mv day3/ day4/
mv day2/ day3
cp day1/ day2/
exit
```

---

### Post by olithraz on 2012-04-29
> **codemaniac said:**
> put your commands you want to execute on the remote machine , on a bash script .and try below locally .
```
ssh olithraz@192.168.1.123 'bash -s' < your_script.sh
```


so what you are saying, is make two scripts? 

script1.sh and script2.sh?

where script1 is ```
ssh olithraz@192.168.1.123 'bash -s' < script2.sh
```
and script 2 is the copying one?

---

### Post by codemaniac on 2012-04-29
```
ssh olithraz@192.168.1.123 'bash -s' < your_script.sh
```

your_script.sh is the container of all the commands you want to execute on remote machine  192.168.1.123 .Please note that your_script.sh is the script name and there are no spaces in between .

---

### Post by olithraz on 2012-04-29
> **codemaniac said:**
> ```
ssh olithraz@192.168.1.123 'bash -s' < your_script.sh
```your_script.sh is the container of all the commands you want to execute on remote machine  192.168.1.123 .Please note that your_script.sh is the script name and there are no spaces in between .


Brilliant! That worked perfectly! Thank you so much!

---

