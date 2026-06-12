---
title: "any software installation problem"
date: 2012-03-20
forum: General Help
---

### Post by kabir96 on 2012-03-20
i get this message when i try to install any software 
please help i am new to ubuntu 

khan@khan-GA-73VM-S2:~$ sudo apt-get install synaptic
[sudo] password for khan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libept1
Suggested packages:
  dwww menu deborphan
The following NEW packages will be installed:
  libept1 synaptic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/2,284 kB of archives.
After this operation, 7,549 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package libept1.
(Reading database ... 30%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'liboil0.3' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
khan@khan-GA-73VM-S2:~$

---

### Post by cortman on 2012-03-20
Hi, and welcome to Ubuntu and the forums!

Please open a terminal and type the following commands

```
sudo rm -r /var/cache/apt/archives/*
sudo apt-get update
```

The try installing your software again.

---

### Post by kabir96 on 2012-03-20
> **cortman said:**
> Hi, and welcome to Ubuntu and the forums!

Please open a terminal and type the following commands

```
sudo rm -r /var/cache/apt/archives/*
sudo apt-get update
```

The try installing your software again.
thank you for your reply but i am stuck with the same error message again 
i dont know what to do ?
please help 

khan@khan-GA-73VM-S2:~$ sudo rm -r /var/cache/apt/archives/*
[sudo] password for khan: 
khan@khan-GA-73VM-S2:~$ sudo apt-get update
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                               
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric InRelease                             
                            
.
.
.
.
.
..
.
.
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Fetched 2,823 B in 49710d 1h 1min 19s (0 B/s)
Reading package lists... Done
khan@khan-GA-73VM-S2:~$ sudo apt-get install synaptic
sudo: timestamp too far in the future: Mar 21 01:27:53 2012
[sudo] password for khan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libept1
Suggested packages:
  dwww menu deborphan
The following NEW packages will be installed:
  libept1 synaptic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,284 kB of archives.
After this operation, 7,549 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) oneiric/main libept1 i386 1.0.5build1 [134 kB]
Get:2 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) oneiric/universe synaptic i386 0.75.2ubuntu8 [2,150 kB]
Fetched 2,284 kB in 39s (58.3 kB/s)                                            
Selecting previously deselected package libept1.
(Reading database ... 30%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'liboil0.3' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
khan@khan-GA-73VM-S2:~$

---

### Post by kabir96 on 2012-03-20
its just giving me a message 

Selecting previously deselected package libept1.
(Reading database ... 30%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'liboil0.3' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

for every application i try to install or uninstall i get the same message

---

### Post by cortman on 2012-03-20
Run

```
sudo apt-get install -f
```

And post the results.

---

### Post by kabir96 on 2012-03-21
this is the result:

khan@khan-GA-73VM-S2:~$ sudo apt-get install -f
[sudo] password for khan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
khan@khan-GA-73VM-S2:~$

---

### Post by kabir96 on 2012-03-21
> **cortman said:**
> Run

```
sudo apt-get install -f
```And post the results.




this is the result:

khan@khan-GA-73VM-S2:~$ sudo apt-get install -f
[sudo] password for khan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
khan@khan-GA-73VM-S2:~$

---

### Post by kabir96 on 2012-03-21
> **heldurd said:**
> Please open a terminal and type the following commands


i tried that and still the same message : 


Selecting previously deselected package libept1.
(Reading database ... 30%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'liboil0.3' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by cortman on 2012-03-21
Ok, in that case it looks like the script given in the first post of [this thread]("http://ubuntuforums.org/showthread.php?t=1319791") fixed that problem for others. Copy the script code into a text file and save it as listfix.py. Then open a terminal and type

```
chmod +x listfix.py
python listfix.py
```

---

### Post by raja.genupula on 2012-03-21
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

and try again

---

### Post by kabir96 on 2012-03-21
> **cortman said:**
> Ok, in that case it looks like the script given in the first post of [this thread]("http://ubuntuforums.org/showthread.php?t=1319791") fixed that problem for others. Copy the script code into a text file and save it as listfix.py. Then open a terminal and type

```
chmod +x listfix.py
python listfix.py
```


i got this error message: 

khan@khan-GA-73VM-S2:~$ chmod +x listfix.py
khan@khan-GA-73VM-S2:~$ python listfix.py
Traceback (most recent call last):
  File "listfix.py", line 18, in <module>
    f = open(path, 'a+')
IOError: [Errno 13] Permission denied: '/var/lib/dpkg/info/accountsservice.conffiles'
khan@khan-GA-73VM-S2:~$

---

### Post by kabir96 on 2012-03-21
> **raja.genupula said:**
> ```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```and try again

i tried it and still i cannot install any software :

khan@khan-GA-73VM-S2:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libept1
Suggested packages:
  dwww menu deborphan
The following NEW packages will be installed:
  libept1 synaptic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/2,284 kB of archives.
After this operation, 7,549 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package libept1.
(Reading database ... 30%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'liboil0.3' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
khan@khan-GA-73VM-S2:~$

---

### Post by matt_symes on 2012-03-21
Hi

Can we take a look at the file itself.

From a terminal 

```
cat /var/lib/dpkg/info/liboil*list
```

Pos tthe results back here.

Kind regards

---

### Post by kabir96 on 2012-03-21
> **matt_symes said:**
> Hi

Can we take a look at the file itself.

From a terminal 

```
cat /var/lib/dpkg/info/liboil*list
```Pos tthe results back here.

Kind regards

i got this message :

khan@khan-GA-73VM-S2:~$ cat /var/lib/dpkg/info/liboil*list
&#65533;P&#65533;v&#65533;&#65533;&#65533;E&#65533;
&#65533;
.P&#65533;&#65533;&#65533;&#65533;&#65533;F&#65533;&#65533;#&#65533;P
&#65533;P&#65533;[&#65533;2&#65533;G&#65533;&#65533;
&#65533;ZB&#65533;&#65533;&#65533;&#65533;H&#65533;u2
[P&#65533;7&#65533;&#65533;&#65533;J&#65533;,Cw
lP&#65533;K&#65533;c7&#65533;
khan@khan-GA-73VM-S2:~$

---

### Post by matt_symes on 2012-03-21
Hi

> **kabir96 said:**
> i got this message :

khan@khan-GA-73VM-S2:~$ cat /var/lib/dpkg/info/liboil*list
&#65533;P&#65533;v&#65533;&#65533;&#65533;E&#65533;
&#65533;
.P&#65533;&#65533;&#65533;&#65533;&#65533;F&#65533;&#65533;#&#65533;P
&#65533;P&#65533;[&#65533;2&#65533;G&#65533;&#65533;
&#65533;ZB&#65533;&#65533;&#65533;&#65533;H&#65533;u2
[P&#65533;7&#65533;&#65533;&#65533;J&#65533;,Cw
lP&#65533;K&#65533;c7&#65533;
khan@khan-GA-73VM-S2:~$

That will be the problem then ! It should look simliar to this.

```

matthew@matthew-Aspire-7540:~$ cat /var/lib/dpkg/info/liboil*list
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/liboil0.3
/usr/share/doc/liboil0.3/README
/usr/share/doc/liboil0.3/AUTHORS
/usr/share/doc/liboil0.3/copyright
/usr/share/doc/liboil0.3/NEWS.gz
/usr/share/doc/liboil0.3/changelog.Debian.gz
/usr/lib
/usr/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu/liboil-0.3.so.0.3.0
/usr/lib/x86_64-linux-gnu/liboil-0.3.so.0
matthew@matthew-Aspire-7540:~
```

Are you on 32 or 64 bit ?

From the terminal

```
uname -a
```

Kind regards

---

### Post by kabir96 on 2012-03-21
> **matt_symes said:**
> Hi



That will be the problem then ! It should look simliar to this.

```

matthew@matthew-Aspire-7540:~$ cat /var/lib/dpkg/info/liboil*list
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/liboil0.3
/usr/share/doc/liboil0.3/README
/usr/share/doc/liboil0.3/AUTHORS
/usr/share/doc/liboil0.3/copyright
/usr/share/doc/liboil0.3/NEWS.gz
/usr/share/doc/liboil0.3/changelog.Debian.gz
/usr/lib
/usr/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu/liboil-0.3.so.0.3.0
/usr/lib/x86_64-linux-gnu/liboil-0.3.so.0
matthew@matthew-Aspire-7540:~
```Are you on 32 or 64 bit ?

From the terminal

```
uname -a
```Kind regards



i got this message :

khan@khan-GA-73VM-S2:~$ uname -a
Linux khan-GA-73VM-S2 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:49:42 UTC 2012 i686 i686 i386 GNU/Linux

i am on 32 bit

---

### Post by cortman on 2012-03-21
> **matt_symes said:**
> Hi

Can we take a look at the file itself.

From a terminal 

```
cat /var/lib/dpkg/info/liboil*list
```

Pos tthe results back here.

Kind regards

Very good catch, Matt- I didn't think of the whole file being corrupted... Thanks for the input.

---

### Post by matt_symes on 2012-03-21
Hi

Thanks cortman :) I've seen this before though. The last time i saw it the package management system was very corrupted though.

@OP. Run these commands on your system. Post back the results.

```
dpkg -l | grep liboil
```

Small L above after dpkg

```
ls /usr/lib/*liboil*
```

```
ls /lib/*liboil*
```

Kind regards

---

### Post by kabir96 on 2012-03-21
> **cortman said:**
> Very good catch, Matt- I didn't think of the whole file being corrupted... Thanks for the input.


 					Originally Posted by **matt_symes** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11782538#post11782538") 				
 				[I]Hi

Can we take a look at the file itself.

From a terminal 

 	Code:
 	cat /var/lib/dpkg/info/liboil*list 
Pos tthe results back here.

Kind regards


[/I]

i tried opening the file in gedit:  and this is the result

\FA\00P\83\00v\C5\00\00\00\00\00\B4\E7\00E\93\00\00\00\00\00\00
\BF
\00\00\00\00\00\00\00\00\00\D1 \00\00\00\00\00\00.\00P\83\00\B2\C5\00\00\00\00\00\B4\E7\00F\93\00\00\80#\00\00\E2P\00\00\00\00\00\00\00\00\00\D2 \00\00\00\00\00\00\98\00P\83\00[\B2\00\00\00\00\002\D2\00G\93\00\00\96\00\00\CC
\00\00\00\00\00\00\00\00\00\D3 \00\00\00\00\00\00\DC\00ZB\00\00\FF\B1\00\00\00\00\00\B4\E7\00H\93\00\00u\00\002\00\00\00\00\00\00\00\00\00\D4 \00\00\00\00\00\00'\00P\83\00\8F\B1\00\00\00\00\00\F3\9B\00I\93\00\00F\00\00\00\00\00\00\00\00\00\00\00\00\00\00\D5 \00\00\00\00\00\00[\00P\83\007\C6\00\00\00\00\00\B4\E7\00J\93\00\00,C\00\00w\00\00\00\00\00\00\00\00\00\D6 \00\00\00\00\00\00l\00P\83\00\00\00\00\00\00\00\00\00\00\00\00\00K\93\00\00c7\00\00\81\CC
\00\00\00\00\00\00\00\00\00\D7 \00\00

is this what you are asking for ?

---

### Post by kabir96 on 2012-03-21
i tried opening the file in gedit:  and this is the result

\FA\00P\83\00v\C5\00\00\00\00\00\B4\E7\00E\93\00\00\00\00\00\00
\BF
\00\00\00\00\00\00\00\00\00\D1  \00\00\00\00\00\00.\00P\83\00\B2\C5\00\00\00\00\00\B4\E7\00F\93\00\00\80#\00\00\E2P\00\00\00\00\00\00\00\00\00\D2   \00\00\00\00\00\00\98\00P\83\00[\B2\00\00\00\00\002\D2\00G\93\00\00\96\00\00\CC
\00\00\00\00\00\00\00\00\00\D3  \00\00\00\00\00\00\DC\00ZB\00\00\FF\B1\00\00\00\00\00\B4\E7\00H\93\00\00u\00\002\00\00\00\00\00\00\00\00\00\D4   \00\00\00\00\00\00'\00P\83\00\8F\B1\00\00\00\00\00\F3\9B\00I\93\00\00F\00\00\00\00\00\00\00\00\00\00\00\00\00\00\D5   \00\00\00\00\00\00[\00P\83\007\C6\00\00\00\00\00\B4\E7\00J\93\00\00,C\00\00w\00\00\00\00\00\00\00\00\00\D6   \00\00\00\00\00\00l\00P\83\00\00\00\00\00\00\00\00\00\00\00\00\00K\93\00\00c7\00\00\81\CC
\00\00\00\00\00\00\00\00\00\D7 \00\00

is this what you are asking for ?

---

### Post by kabir96 on 2012-03-21
> **matt_symes said:**
> Hi

Thanks cortman :) I've seen this before though. The last time i saw it the package management system was very corrupted though.

@OP. Run these commands on your system. Post back the results.

```
dpkg -l | grep liboil
```Small L above after dpkg

```
ls /usr/lib/*liboil*
``````
ls /lib/*liboil*
```Kind regards


hey i got this result:

khan@khan-GA-73VM-S2:~$ dpkg -l | grep liboil
ii  liboil0.3                              0.3.17-2ubuntu1                         Library of Optimized Inner Loops
khan@khan-GA-73VM-S2:~$ ls /usr/lib/*liboil*
/usr/lib/liboil-0.3.so.0  /usr/lib/liboil-0.3.so.0.3.0
khan@khan-GA-73VM-S2:~$ ls /lib/*liboil*
ls: cannot access /lib/*liboil*: No such file or directory
khan@khan-GA-73VM-S2:~$

---

### Post by matt_symes on 2012-03-22
Hi

> **kabir96 said:**
> hey i got this result:

khan@khan-GA-73VM-S2:~$ dpkg -l | grep liboil
ii  liboil0.3                              0.3.17-2ubuntu1                         Library of Optimized Inner Loops
khan@khan-GA-73VM-S2:~$ ls /usr/lib/*liboil*
/usr/lib/liboil-0.3.so.0  /usr/lib/liboil-0.3.so.0.3.0
khan@khan-GA-73VM-S2:~$ ls /lib/*liboil*
ls: cannot access /lib/*liboil*: No such file or directory
khan@khan-GA-73VM-S2:~$

Let's try recreating the file. I am making some assumptions about what files are installed where and what's corrupted but i am hoping i am correct.

Open a terminal and type these commands.

First type

```
ls /var/lib/dpkg/info/liboil*list
```

You will see output similar (but not the same) as 

```
matthew@matthew-Aspire-7540:~$ ls /var/lib/dpkg/info/liboil*list
/var/lib/dpkg/info/**liboil0.3:amd64.list**
matthew@matthew-Aspire-7540:~$
```

Make a note of the file name. You will need it later. I have highlighted mine in bold above.

Next let's delete the corrupted file.

```
sudo rm /var/lib/dpkg/info/liboil*list
```

Now let's create a new file.

```
gksudo gedit /var/lib/dpkg/info/**<file_name_from_above>**
```

Use the filename from step 1 and replace <file_name_from_above> above.

Copy and paste this into the file.

```
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/liboil0.3
/usr/share/doc/liboil0.3/README
/usr/share/doc/liboil0.3/AUTHORS
/usr/share/doc/liboil0.3/copyright
/usr/share/doc/liboil0.3/NEWS.gz
/usr/share/doc/liboil0.3/changelog.Debian.gz
/usr/lib
/usr/lib/liboil-0.3.so.0.3.0
/usr/lib/liboil-0.3.so.0
```

Save the file and exit. Then type

```
sudo apt-get update
```

What traction does that give you ?

EDIT: I made a couple of typos so if you are subscribed by mail, please reread.

Kind regards

---

### Post by kabir96 on 2012-03-23
> **matt_symes said:**
> Hi



Let's try recreating the file. I am making some assumptions about what files are installed where and what's corrupted but i am hoping i am correct.

Open a terminal and type these commands.

First type

```
ls /var/lib/dpkg/info/liboil*list
```You will see output similar (but not the same) as 

```
matthew@matthew-Aspire-7540:~$ ls /var/lib/dpkg/info/liboil*list
/var/lib/dpkg/info/**liboil0.3:amd64.list**
matthew@matthew-Aspire-7540:~$
```Make a note of the file name. You will need it later. I have highlighted mine in bold above.

Next let's delete the corrupted file.

```
sudo rm /var/lib/dpkg/info/liboil*list
```Now let's create a new file.

```
gksudo gedit /var/lib/dpkg/info/**<file_name_from_above>**
```Use the filename from step 1 and replace <file_name_from_above> above.

Copy and paste this into the file.

```
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/liboil0.3
/usr/share/doc/liboil0.3/README
/usr/share/doc/liboil0.3/AUTHORS
/usr/share/doc/liboil0.3/copyright
/usr/share/doc/liboil0.3/NEWS.gz
/usr/share/doc/liboil0.3/changelog.Debian.gz
/usr/lib
/usr/lib/liboil-0.3.so.0.3.0
/usr/lib/liboil-0.3.so.0
```Save the file and exit. Then type

```
sudo apt-get update
```What traction does that give you ?

EDIT: I made a couple of typos so if you are subscribed by mail, please reread.

Kind regards




thank you soo sooo sooo much , that resolved my issue 
thanks to all the guys that helped me soo much .
i just started to use it and i got so much support
you rock guys

---

### Post by kabir96 on 2012-03-23
thanx a lot [matt_symes]("http://ubuntuforums.org/member.php?u=1067998")

---

