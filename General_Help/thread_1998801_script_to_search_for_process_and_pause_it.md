---
title: "script to search for process and pause it"
date: 2012-06-07
forum: General Help
---

### Post by essential1 on 2012-06-07
hi guys,

i am looking to create a script which looks for starting kvm/qemu processes (which are virtual machines), and immediately to pause that process.

ps aux | grep kvm 

is able to produce a list of the running processes of kvm and their pids, and i can use:

kill -s CONT <pid> to pause the process.

however i need to extract the pids from the ps aux command output. i'm not experienced with scripting in any language, and am unsure how i would do that. any help please, or point me in the direction of a tutorial which can help?

---

### Post by fbicknel on 2012-06-07
I think the glue you're looking for is 'awk'.  For example:


```
bick-ubtu3:~$ ps aux | grep sleep 
root     12057  0.0  0.0   4300   352 ?        SN   07:35   0:00 sleep 1744
root     14411  0.0  0.0  11368   608 ?        SN   07:57   0:00 sleep 10
fbicknel 14417  0.0  0.0  13596   924 pts/3    S+   07:57   0:00 grep --color=auto sleep
bick-ubtu3:~$ ps aux | grep sleep  | awk '{print $2}'
12057
14424
14437
bick-ubtu3:~$ 
```You can refine this a bit by using a r.e. in your grep pattern:
```
bick-ubtu3:~$ ps aux | grep [s]leep
root     12057  0.0  0.0   4300   352 ?        SN   07:35   0:00 sleep 1744
root     14628  0.0  0.0  11364   600 ?        SN   07:59   0:00 sleep 10
bick-ubtu3:~$ ps aux | grep [s]leep  | awk '{print $2}'
12057
14628
bick-ubtu3:~$ 
```That removes the 'grep sleep' process so you're only left with the real sleep processes.

---

### Post by essential1 on 2012-06-07
that looks like exactly what i was looking for. i really need to learn some more about linux commands. thanks!

---

