---
title: "process in ubuntu"
date: 2011-05-07
forum: General Help
---

### Post by mortez28 on 2011-05-07
hello
i have some question about linux(last kernel)
1.what time scheduling & page replacement algorithm have been used in linux
2.how to create a process
3.how to kill a process
4.how to send information to a process
5.how to see a process
6.how to increase priority of a process
7.how to decrease priority of a process
excuse me about my english
i need the answers as soon as possible
thanks a lot...

---

### Post by mortez28 on 2011-05-07
plz someone help me...:(

---

### Post by mortez28 on 2011-05-07
please i need help!!!
is there anyone???

---

### Post by lakosshoots on 2011-05-08
If you use the Graphical User Interface you can use the system monitor to check processes. By right clicking in one, you 'll get most of the things you ask for.

If you are interested in terminal, you can type:

top

it will show the running processes in real time with memory and CPU info.

Then press 'h' (the button) and the help menu will get you the answers you seek.

Good luck.

---

### Post by idoitprone on 2011-05-08
calm down mortez28, you realize there is not alot of kernel hackers scanning the forums. You also realize there is a 24 hour bump rule?

THe current kernel scheduling algorithm is cfs (Completely Fair Scheduler [http://en.wikipedia.org/wiki/Completely_Fair_Scheduler](http://en.wikipedia.org/wiki/Completely_Fair_Scheduler)), written by Ingo Molnar of Red Hat who was inspired by Con Kolivas, author of the ck patches. There is a flame war between Con Kolivas vs Linus and Ingo. You should read about it. Con proclaim there isn't emphasis on the linux desktop and the current algorithm at the time O(1) was slow. 

[http://kerneltrap.org/node/14008](http://kerneltrap.org/node/14008) one of the flame war links


I do not know about the rest, since the linux kernel does everything so well already that I not need to prioritized processes. 

I cannot say anything else since I am not a kernel hacker

---

