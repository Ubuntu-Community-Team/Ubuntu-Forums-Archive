---
title: "Problem with dpkg limewire install"
date: 2009-08-08
forum: General Help
---

### Post by rawr_a_Zombie on 2009-08-08
I got the message "Error broken count >0" after a limewire install locked up my 9.04. Is there a terminal code i could enter to delete the corrupted package? I also cannot log into the synaptic package program. It creates a error box telling me to run "sudo dkpg configure -a". When i enter this the result is

sudo: unable to resolve host Eee PC
[sudo] password for zombie: 
Sorry, try again.
[sudo] password for zombie: 
dpkg: unknown option --configure-a

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
zombie@Eee PC:~$ sudo dpkg--configure-a
sudo: unable to resolve host Eee PC
sudo: dpkg--configure-a: command not found
zombie@Eee PC:~$ sudo --configure -a
sudo: please use single character options
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
zombie@Eee PC:~$ 


any thoughts?

---

### Post by michy99 on 2009-08-08
First, make sure your spaces are right.```
sudo dpkg --configure -a
```Second, you seem to have a problem with your hostname, which is preventing you from using sudo.

---

