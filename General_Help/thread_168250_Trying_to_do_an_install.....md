---
title: "Trying to do an install...."
date: 2006-04-30
forum: General Help
---

### Post by styven on 2006-04-30
Hi all,

I am trying got install vmware from a coverdisc of linux format magazine.

I have extracted the file, it is sat on my desktop.

The magazine then tells me to run vmware-install.pl in a terminal window as root.

I find this file and double click, a box comes up with options, one being to "run in terminal", i click this and a terminal flashes up and dissapears.

As i understand vmware should then run.

Any ideas anyone?

Steve

---

### Post by Ramses de Norre on 2006-04-30
do sudo /path/to/file/vmware-install.pl
If it gives errors try chmod +x /path/to/file/vmware-install.pl first.

---

### Post by styven on 2006-04-30
Hi thanks for that,

I am still struggling, not sure that I am putting the path to file bit in right, ihave now moved it to my home folder. 

I get this...............
styven@edubuntu:~$ sudo /styven/home/vmware-player-distrib/vmware-install.pl
Password:
sudo: /styven/home/vmware-player-distrib/vmware-install.pl: command not found
styven@edubuntu:~$

if i try chmod..........i get this................

styven@edubuntu:~$ sudo /styven/home/vmware-player-distrib/vmware-install.pl
Password:
sudo: /styven/home/vmware-player-distrib/vmware-install.pl: command not found
styven@edubuntu:~$ chmod +x /styven/home/vmware-install.pl first.
chmod: cannot access `/styven/home/vmware-install.pl': No such file or directorychmod: cannot access `first.': No such file or directory
styven@edubuntu:~$ chmod +x /home/vmware-install.pl first.
chmod: cannot access `/home/vmware-install.pl': No such file or directory
chmod: cannot access `first.': No such file or directory
styven@edubuntu:~

not convinced i am entering the command right!

---

