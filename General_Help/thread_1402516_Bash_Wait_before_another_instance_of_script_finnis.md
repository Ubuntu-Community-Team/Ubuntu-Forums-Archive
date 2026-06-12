---
title: "Bash: Wait before another instance of script finnishes"
date: 2010-02-09
forum: General Help
---

### Post by tolanri on 2010-02-09
Hi, I wrote quick script that is quite heavy on system resources and sometimes another is executed before the first one is done. For this reason I would like to implement simple while loop that would check if current instance of this script is in progress, and to script continue after the previous instance is done (queue)

I thought of writing PID number into .pid file and add this loop in beginning on the script

```

while [ `ps -e | grep rs.sh` == `cat ~/rs.pid` ]
do
    sleep 5
done

echo "How to write PID of this instance into file?"

```Would it work? Do you know of some other more elegant way? I still don't know how to store PID of this instance into file, though.

Thanks!

---

### Post by bluefrog on 2010-02-09
command1 && command2

command2 will be run only if first command completed successfully

---

### Post by tolanri on 2010-02-09
Thanks, but it is not possible.

The bash script will be executed after every download is complete, so I need checking like I mentioned in original post.

---

### Post by rnerwein on 2010-02-09
hi
if you start that script by yourself you can start the main part in the background 
my_backup_start &
bg_pid = $!
wait $!
do what you want with your pid in $bg_pid

ciao

---

### Post by tolanri on 2010-02-09
Hi, thanks for your post. Unfortunately I am not manually starting this script. Otherwise I would do what bluefrog suggested.

---

### Post by tolanri on 2010-02-09
Bump. Anyone?

---

### Post by john newbuntu on 2010-02-09
If you are not starting this script manually, how is it being kicked off?  I am still not sure on what you are trying to achieve.  But I have a vague feeling that something like this could get it to work(assuming you have only one instance of the script running).  Otherwise, you need to combine it with what rnerwein suggested:

      /bin/pidof rs.sh
      if ($? -ne 0); then
         rs.sh&
         echo "started rs.sh"
      else
         sleep 10
      fi

The other option is to have trap command in the rs.sh script that kick off another script when it ends.
If I am completely off in my understanding of the issue, just ignore this post.

---

### Post by tolanri on 2010-02-09
Thanks john, you're not very far from what I need to achieve.

Basically, I am writing script for rTorrent, which will perform various actions after the download is complete. So it is rTorrent program that is starting the script.

Your idea of having two scripts, where one would execute the other would work, so I'll try it, however I'd prefer only one script :)

Launcher script would probably look like this:

```
#!/bin/bash

while [ `ps -e | grep rs.sh | wc -l` -ge 1 ]
  do
    sleep 5
done

/home/tolanri/rs.sh
```If anyone have other idea how to get it to work in just one script, please post it :)

Thanks!

---

### Post by tolanri on 2010-02-09
Ok, finally managed to solve that problem, using:

```
while [ 1 ]
do
  if [ `pidof -x rs.sh | grep -c $(cat ~/.rs.pid)` -ne 1 ]; then
    echo $$ > ~/.rs.pid
    break
  fi
    sleep 5
done
```

---

