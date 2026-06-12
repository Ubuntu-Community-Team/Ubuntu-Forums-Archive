---
title: "Adept opens in Read-only mode"
date: 2006-03-23
forum: General Help
---

### Post by kevin tough on 2006-03-23
I have just installed Kubuntu. The package manager opens first with a warning window "The APT Database wil be opened in read-only mode,... cannot install...anything. You have to...as root to be able to do that.

well I've tried "sudo adept" and got the same message.  I can add and remove packages that are listed.

I cannot change repositories or should I say "fetch" from a new repository.:(   Enable and disable of the repositories seems to work in so far as the highlighted lines change.

Hoping to find a home with Kubuntu,

Kevin Tough

---

### Post by Barrakketh on 2006-03-23
[QUOTE=kevin tough]I have just installed Kubuntu. The package manager opens first with a warning window "The APT Database wil be opened in read-only mode,... cannot install...anything. You have to...as root to be able to do that.

well I've tried "sudo adept" and got the same message.  I can add and remove packages that are listed.

I cannot change repositories or should I say "fetch" from a new repository.:(   Enable and disable of the repositories seems to work in so far as the highlighted lines change.

Hoping to find a home with Kubuntu,

Kevin Tough[/QUOTE]
"kdesu adept" should open it just fine.  Same with using KMenu -> Settings -> Package Manager (Adept)

---

### Post by ltmon on 2006-03-23
There might be something crashed in the background that has kept it's lock on the dpkg database.  That can happen occassionally.

Try

```

killall adept

```

and start again.  If you have used any other dpkg tools (synaptic, apt-get, dpkg, aptitude) make sure there are no left over processes from them either.

L.

---

### Post by kevin tough on 2006-03-30
Seems to be working now.

Thanks guys

---

### Post by hannes100 on 2006-04-04
Hi,

i have a similar problem but i think mine is more complicated.
If i start up adept, it also states, that it starts in read-only-mode because there is another process running  just like in the thread befor.
The big problem ist, that i cant kill any of the stated processes like adept, apt-get etc....
if i type
ps fax | grep adept

i get  a proces but everytime it has a different pid 
For example:
hannes@kenny:~$ ps fax |grep adept
 4917 ?        S      0:00  \_ kdesu -u root -c adept '-icon' 'adept' '-miniicon' 'adept' -caption "Adept"
 7218 pts/1    S+     0:00  |       \_ grep adept
hannes@kenny:~$ ps fax |grep adept
 4917 ?        S      0:00  \_ kdesu -u root -c adept '-icon' 'adept' '-miniicon' 'adept' -caption "Adept"
 7220 pts/1    S+     0:00  |       \_ grep adept
hannes@kenny:~$ ps fax |grep adept
 4917 ?        S      0:00  \_ kdesu -u root -c adept '-icon' 'adept' '-miniicon' 'adept' -caption "Adept"
 7222 pts/1    S+     0:00  |       \_ grep adept
hannes@kenny:~$                             


i repeated the instruction as fast as i could and repeating an instruction is really quite fast within the bash........
So i can't really locate the adept process and so i can't kill it by killall or kill (pid),
because kills responses, that there is no such process.
If i reboot, the same problem appears........

I am very happy for any help, because as mentioned before, i also can't install packages........
thnx
Hannes

---

### Post by mark² on 2006-06-17
In Kubuntu (breezy) Adept sometimes hangs (looks to me like a deadlock issue).
When having to kill the process, a lock file remains in place, preventing a restart in Read/Write modus.
It can be removed like this:

sudo rm  /var/lib/dpkg/lock

---

### Post by Eagle3386 on 2006-06-24
[QUOTE=mark²]In Kubuntu (breezy) Adept sometimes hangs (looks to me like a deadlock issue).
When having to kill the process, a lock file remains in place, preventing a restart in Read/Write modus.
It can be removed like this:

sudo rm  /var/lib/dpkg/lock[/QUOTE]

**[EDIT]**

OK, I've found the solution (thanks to the BASH ;)): "dpkg --configure -a" fixes the broken list or whatever was broken.. ;) :)

---

### Post by hannes100 on 2006-09-06
I had this problem a couple of times now , especially if i made distubgrades to other repositories, but in fact
killing adept if it hangs and after that 
dpkg --configure -a
always fixed the problem
cheers

---

