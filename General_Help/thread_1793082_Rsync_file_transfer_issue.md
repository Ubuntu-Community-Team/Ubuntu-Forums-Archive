---
title: "Rsync file transfer issue"
date: 2011-06-28
forum: General Help
---

### Post by Tillman32 on 2011-06-28
I xfered a video file from my laptop to my server, I directed it to my home folder using 

rsync --progress --partial -avz home/brandon/Downloads/Little\ Fockers.mkv brandon@192.168.1.106:home/

But when I look in my home folder, and its not there, then I use the command find, to search for it, its not there.

But if I hit find and hit enter this is what happens


./brandon
./brandon/interfaces
./brandon/.viminfo
./brandon/.vim
./brandon/.vim/.netrwhist
./brandon/.ssh
./brandon/.ssh/known_hosts
./brandon/.ssh/id_rsa
./brandon/.ssh/id_rsa.pub
./brandon/.sudo_as_admin_successful
./brandon/.profile
./brandon/.bash_history
./brandon/.bash_logout
./brandon/.cache
./brandon/.cache/motd.legal-displayed
./brandon/home
./brandon/home/Little Fockers.mkv
./brandon/.bashrc

It shows up there as its own home directory, quite odd. I can't move the file out of it or anything, I want to move it to a different folder. 

Any idea?

---

### Post by sam_delta on 2011-06-29
"home" is not the appropriate path of your home directory on your server (it means a folder called "home" inside the server, assuming that the default path is your home, it would end as a folder called home inside your home), if you want the file to go to your home directory in the server, try this
```
brandon@192.168.1.106:~/
```
"~/" means your home directory, or you could specify the whole path as follows
```
bradon@192.168.1.106:/home/brandon/
```

about not being able to move the file, it might be permissions problem, what you get when you try to move the file? 

sam

---

### Post by papibe on 2011-06-29
The simplest way to move the file is to ssh to the server and use regular mv to move it.

Regards.

---

### Post by Tillman32 on 2011-06-30
Thanks for the input, with being able to figure out where the hell that second /home was, I was able to sudo mv the file to where I wanted, thanks for the clarification!

---

### Post by sam_delta on 2011-06-30
you might also want to change the owner of the file to yourself (to stop having to use sudo each time you want to move or write to it)
```
sudo chown brandon:brandon file
``` just replace file with the file path.

sam

---

