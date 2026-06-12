---
title: "All a Newbie must know"
date: 2011-08-22
forum: General Help
---

### Post by mmsltni on 2011-08-22
Hello.
I am a newcomer for Ubuntu,I just install it two weeks ago.
Up to now , I have much interested in that.
But I have many question... that I can't find their answer by googling.
I want to know about apt-get and aptitude commands,I don't know what these are?now,I just type them to install or remove a software!I don't know what these commands mean?can you explain,for example when we command " apt-get install ...." what is apt-get and what is install?!
second , how can we know which process  are running ? something like task manager in windows?
third,how can we find installed or un installed drivers?I just find my graphic card in hardware drivers!
then,can you show a procedure to learn Ubuntu completely?
BTW,I face with these problem much,suppose,in terminal we are download and install a software(by apt-get)then we interrupt it by clicking "X",then does it really stop?because when  i use e.g. synaptic package manager it said that other package manger are running?
Thanks,and excuse me if my question may be irelevant and a  lot.( because i have many question and so motivated to learn)thanks again.

---

### Post by Josep CA on 2011-08-22
First of all, welcome to Ubuntu!
apt-get is a packaging tool. Ubuntu programs come "packed" as packages. I mean inside a package there are all the files that will be needed to install a program. With this packaging tool you can call many comands as "isntall". If you want more information about any comand in ubuntu just type the command "man" (manual) in terminal and following the commnd you want to get info. For instance:
```

man apt-get

``` 
To know wich processes are running you can use "top" comand.
If you want to kill one of them just type "k" and its PID (Process Identifier).

---

### Post by marin123 on 2011-08-22
> **mmsltni said:**
> Hello.
I am a newcomer for Ubuntu,I just install it two weeks ago.
Up to now , I have much interested in that.
But I have many question... that I can't find their answer by googling.
I want to know about apt-get and aptitude commands,I don't know what these are?now,I just type them to install or remove a software!I don't know what these commands mean?can you explain,for example when we command " apt-get install ...." what is apt-get and what is install?!
second , how can we know which process  are running ? something like task manager in windows?
third,how can we find installed or un installed drivers?I just find my graphic card in hardware drivers!
then,can you show a procedure to learn Ubuntu completely?
BTW,I face with these problem much,suppose,in terminal we are download and install a software(by apt-get)then we interrupt it by clicking "X",then does it really stop?because when  i use e.g. synaptic package manager it said that other package manger are running?
Thanks,and excuse me if my question may be irelevant and a  lot.( because i have many question and so motivated to learn)thanks again.

first - apt-get is the name of the program and install, remove are commands what that program should do, and in the end there's name of the package that need to be installed or removed. it needs to be run as root (sudo) so it can access restricted areas of the filesystem.

hardware drivers are a program (its called jockey-gtk) that finds proprietary (not open-source) drivers for hardware on your system, ie graphic cards and wireless modules.

in natty narwhal press super button (the one with windows logo) and type system monitor, thats your task manager, just select Processes tab.

what do you mean with "learn ubuntu completely"??? there's no such thing. no one knows ubuntu completely.

and finally, don't close terminal with X button. you can stop process in terminal with ctrl+c and then type exit. to exit from man pages use q (if you type man apt-get).

---

### Post by mmsltni on 2011-08-22
Thanks for your answer.May  explain about columns in 'top'?

---

### Post by sanderd17 on 2011-08-22
Learing the terminal might be a good idea for you:

[http://linuxcommand.org]("http://linuxcommand.org")

---

### Post by Josep CA on 2011-08-22
```

man top

```

From manual:
> 
2a. DESCRIPTIONS of Fields

Listed below are top's available fields. They are always associated with the letter shown, regardless of the position you may have established for them with the 'o' (Order fields) interactive command.

Any field is selectable as the sort field, and you control whether they are sorted high-to-low or low-to-high. For additional information on sort provisions see topic 3c. TASK Area Commands.
a: PID -- Process Id
    The task's unique process ID, which periodically wraps, though never restarting at zero. 
b: PPID -- Parent Process Pid
    The process ID of a task's parent. 
c: RUSER -- Real User Name
    The real user name of the task's owner. 
d: UID -- User Id
    The effective user ID of the task's owner. 
e: USER -- User Name
    The effective user name of the task's owner. 
f: GROUP -- Group Name
    The effective group name of the task's owner. 
g: TTY -- Controlling Tty
    The name of the controlling terminal. This is usually the device (serial port, pty, etc.) from which the process was started, and which it uses for input or output. However, a task need not be associated with a terminal, in which case you'll see '?' displayed. 
h: PR -- Priority
    The priority of the task. 
i: NI -- Nice value
    The nice value of the task. A negative nice value means higher priority, whereas a positive nice value means lower priority. Zero in this field simply means priority will not be adjusted in determining a task's dispatchability. 
j: P -- Last used CPU (SMP)
    A number representing the last used processor. In a true SMP environment this will likely change frequently since the kernel intentionally uses weak affinity. Also, the very act of running top may break this weak affinity and cause more processes to change CPUs more often (because of the extra demand for cpu time). 
k: %CPU -- CPU usage
    The task's share of the elapsed CPU time since the last screen update, expressed as a percentage of total CPU time. In a true SMP environment, if 'Irix mode' is Off, top will operate in 'Solaris mode' where a task's cpu usage will be divided by the total number of CPUs. You toggle 'Irix/Solaris' modes with the 'I' interactive command. 
l: TIME -- CPU Time
    Total CPU time the task has used since it started. When 'Cumulative mode' is On, each process is listed with the cpu time that it and its dead children has used. You toggle 'Cumulative mode' with 'S', which is a command-line option and an interactive command. See the 'S' interactive command for additional information regarding this mode. 
m: TIME+ -- CPU Time, hundredths
    The same as 'TIME', but reflecting more granularity through hundredths of a second. 
n: %MEM -- Memory usage (RES)
    A task's currently used share of available physical memory. 
o: VIRT -- Virtual Image (kb)
    The total amount of virtual memory used by the task. It includes all code, data and shared libraries plus pages that have been swapped out. (Note: you can define the STATSIZE=1 environment variable and the VIRT will be calculated from the /proc/#/state VmSize field.)

    VIRT = SWAP + RES. 
p: SWAP -- Swapped size (kb)
    The swapped out portion of a task's total virtual memory image. 
q: RES -- Resident size (kb)
    The non-swapped physical memory a task has used.

    RES = CODE + DATA. 
r: CODE -- Code size (kb)
    The amount of physical memory devoted to executable code, also known as the 'text resident set' size or TRS. 
s: DATA -- Data+Stack size (kb)
    The amount of physical memory devoted to other than executable code, also known as the 'data resident set' size or DRS. 
t: SHR -- Shared Mem size (kb)
    The amount of shared memory used by a task. It simply reflects memory that could be potentially shared with other processes. 
u: nFLT -- Page Fault count
    The number of major page faults that have occurred for a task. A page fault occurs when a process attempts to read from or write to a virtual page that is not currently present in its address space. A major page fault is when disk access is involved in making that page available. 
v: nDRT -- Dirty Pages count
    The number of pages that have been modified since they were last written to disk. Dirty pages must be written to disk before the corresponding physical memory location can be used for some other virtual page. 
w: S -- Process Status
    The status of the task which can be one of: 'D' = uninterruptible sleep 'R' = running 'S' = sleeping 'T' = traced or stopped 'Z' = zombie

    Tasks shown as running should be more properly thought of as 'ready to run' -- their task_struct is simply represented on the Linux run-queue. Even without a true SMP machine, you may see numerous tasks in this state depending on top's delay interval and nice value. 
x: Command -- Command line or Program name
    Display the command line used to start a task or the name of the associated program. You toggle between command line and name with 'c', which is both a command-line option and an interactive command.

    When you've chosen to display command lines, processes without a command line (like kernel threads) will be shown with only the program name in parentheses, as in this example: ( mdrecoveryd )

    Either form of display is subject to potential truncation if it's too long to fit in this field's current width. That width depends upon other fields selected, their order and the current screen width.

    Note: The 'Command' field/column is unique, in that it is not fixed-width. When displayed, this column will be allocated all remaining screen width (up to the maximum 512 characters) to provide for the potential growth of program names into command lines. 
y: WCHAN -- Sleeping in Function
    Depending on the availability of the kernel link map ('System.map'), this field will show the name or the address of the kernel function in which the task is currently sleeping. Running tasks will display a dash ('-') in this column.

    Note: By displaying this field, top's own working set will be increased by over 700Kb. Your only means of reducing that overhead will be to stop and restart top. 
z: Flags -- Task Flags
    This column represents the task's current scheduling flags which are expressed in hexadecimal notation and with zeros suppressed. These flags are officially documented in <linux/sched.h>. Less formal documentation can also be found on the 'Fields select' and 'Order fields' screens. 


---

### Post by mmsltni on 2011-08-22
> **marin123 said:**
> 

in natty narwhal press super button (the one with windows logo) and type system monitor, thats your task manager, just select Processes tab.

what do you mean with "learn ubuntu completely"??? there's no such thing. no one knows ubuntu completely.
  (if you type man apt-get).

:D in system monitor I saw my memory is 2.2GiB,although my Ram is 4GiB,Memory is my Ram?
then,I mean that i want to start a way of linux and end it if even end was infinity!:D,
how can i upgrade 10.04 to 11.04?
Thanks very much!

---

### Post by Josep CA on 2011-08-22
> 
how can i upgrade 10.04 to 11.04?


You can't update directly from 10.04 to 11.04.
You should update first to 10.10, and then to 11.04 but I don't know how to update to an old Ubuntu release if it's possible. Maybe a good idea would be a fresh install (anyway I would recomend to make a fresh install every two-three releases but it's just my opinion).
Another option would be waiting for Ubuntu 12.04 LTS. You will be able to directly upgrade to the next LTS version (12.04) because you are using a LTS version (Long Term Support).

---

### Post by marin123 on 2011-08-22
> **mmsltni said:**
> :D in system monitor I saw my memory is 2.2GiB,although my Ram is 4GiB,Memory is my Ram?
then,I mean that i want to start a way of linux and end it if even end was infinity!:D,
how can i upgrade 10.04 to 11.04?
Thanks very much!

are you sure you have 4 GB of RAM? are you using 32 or 64 bit version of ubuntu?

if you plan on upgrading to 11.04, forget it, you will only break your system. my suggestion: keep 10.04 until 12.04, or backup your data and do a fresh install od 11.04.

EDIT: if you are willing to give ubuntu a fair try, dont worry, you will love it once you get into it. and in few months, you wont be able to go back (you know where ;) ).

---

### Post by elliotn on 2011-08-22
I have been using Ubuntu for about 4-5 years now and still don't know much commands. so I normally use the graphical alternatives

---

### Post by mmsltni on 2011-08-22
Is it worth to change 10.04 to Ubuntu 11.04 Natty,
What are differences?

---

### Post by marin123 on 2011-08-22
> **mmsltni said:**
> Is it worth to change 10.04 to Ubuntu 11.04 Natty,
What are differences?

newer packages, integration of some open source drivers, libreoffice instead of open office, and UNITY of course :)

---

### Post by Idefix82 on 2011-08-22
I say never touch a running system. This is even more true for beginners. Once you become familiar and comfortable with Ubuntu and think that you might be able to resolve an issue, should one arise in the process of upgrading, then you can go ahead. If your hardware is recognised and you have no specific problems, then stick with 10.04 for the time being.

Once you do decide to upgrade, I would also recommend a clean install. When you make a clean install, create a separate partition for /home. This way, whenever you install a new version of Ubuntu, you can leave that partition alone and you will never lose your data (documents, music, photos, even firefox bookmarks, etc).

By the way, it is not a great idea to interrupt an install. Better let it run through and then remove again if you have changed your mind. You *can* interrupt almost any command in the middle, but you don't know what it was doing when you interrupted and what inconsistencies it has left in the system (imagine something like a librarian who puts a new book into the shelf and just as he is about to update the catalogue, you tell him to go home. This book is lost forever, since nobody will find it if it is not in the catalogue).

As for the commands, it is true that one can get by reasonably well without the terminal. But the terminal is for many tasks the most efficient way of getting things done. The best way to learn it is not to start reading thick books and lengthy tutorials, but to ask specific questions here, on the forums. Even for mundane tasks like installing software or copying a file, people will give you instructions using the terminal, since it's much easier and less ambiguous than "click on the second pixel from the right, find a buttom that says "button", it is somewhere in the lower left corner" and so on. At some point, you will want to resize 50 pictures, or rename 5000 files, or remove all the commas from a text file, or do some other batch job, and then there will be no sensible alternative to the terminal (all of the above can be done in 3 seconds if you know the right commands).

Take it slowly. Don't try to learn everything at once, just make sure you are comfortable moving around on your computer. If you do want to learn, you will eventually become the king of your machine in a way you have not known before. I mean you will know everything your system is doing, you will be able to tweak every single setting deep inside the system. Unlike windows, Ubuntu will not try to shield you from knowledge about its inner working. You will be able to write your own scripts that improve your efficiency, or gedit plugins that do exactly what you want. Just don't rush it. As somebody else has said, if you don't leave within the next month, you will never want to go back.

---

### Post by mmsltni on 2011-08-22
Ok , thanks a lot for all...

---

