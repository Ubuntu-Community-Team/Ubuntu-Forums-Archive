---
title: "Kismet &amp; ipw3945"
date: 2006-06-12
forum: General Help
---

### Post by freddo on 2006-06-12
Hi, anyone got this to work with the built in drivers that comes with 2.6.15-23?

when sudo kismet:

Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'ipw3945' in source 'ipw3945,eth1,addme'


kismet.conf:
# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=ipw3945,eth1,addme

Bit new on this one, what am I doing wrong. Could it be that kismet only works with the "old" separate drivers and not the in-kernel-ones?

/fred

---

### Post by senzapadroni on 2006-06-14
Hi fred,
if you're using pre-built kismet you can't use ipw3945 as capture source!
You've got to compile it [from sources]("http://www.kismetwireless.net/code/kismet-2006-04-R1.tar.gz") to do that.
Cheers

---

### Post by armware on 2006-06-17
i'm in the same boat, and what i've got so far is that the message:
FATAL: Unknown capture source type 'ipw3945' in source

means that this version of kismet was built before support for that capture source came about. check the kismet version, came out to be 2005.08.R1. just a tad old. so, as posted, you need to compile kismet from source. i started doing that. ran the first command:
./configure

and got an error reguarding gcc, meaning i needed to run:
sudo apt-get install build-essentail

once that finished, running ./configure got a bit further before it gave me this one:
checking for initscr in -lncurses.... no
configure: WARNING: Unable to find libncurses or libcurses

so i:
sudo apt-get install libncurses

and got:
E: Couldn't find package libncurses

so i:
sudo apt-get install libcurses

and got the same error. so i:
sudo apt-get install libncurses5

and got a new one:
libncurses5 is already the newest version

that's where i'm stuck.

---

### Post by senzapadroni on 2006-06-18
Hi armware,
since you're compiling from sources you need *-dev libraries, so do this:
```
sudo apt-get install libncurses5-dev
```
;)

---

### Post by armware on 2006-06-18
awesome. thank you.

---

### Post by unLog!c on 2006-09-15
> **senzapadroni said:**
> Hi armware,
since you're compiling from sources you need *-dev libraries, so do this:
```
sudo apt-get install libncurses5-dev
```
;)

Please help, this is not working for me :(

I get this:
```
root@IBM:~# sudo apt-get install libncurses5-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libncurses5-dev: Depends: libncurses5 (= 5.4-9ubuntu4) but 5.5-1ubuntu3 is to be installed
E: Broken packages
root@IBM:~#       
```

NOTE: I'm on Kubuntu...

---

### Post by freddo on 2006-09-29
Ho, I have some problems to compile kismet-2006-04-R1:

Output from ./configure

configure: WARNING: uclibc++ not available on this system
checking for main in -lstdc++... no
configure: WARNING: libstdc++ not available on this system
configure: error: Neither uclibc uClibc++ or standard gcc stdc++ libraries found

But, gcc is installed, uclibc is installed

can't find uClibc++ in synaptic, only stdc++ i can find is libstdc++ where i have the libstdc++5 and dev + libstdc++6 installed.

What could be the problem...?

/Freddo

---

### Post by armware on 2006-09-29
try installing uclibc-dev

---

### Post by freddo on 2006-09-30
Is installed, reinstalled but no difference. 

Would really be appreciated if someone could help me on this one.

/Freddo

---

### Post by freddo on 2006-09-30
Solved - tried  sudo apt-get install build-essential
 and this added some needed packag

/Freddo

---

### Post by TutoWRM on 2007-06-30
Hi, after googling all day, i'm gonna give up and ask for help, i've done everything that it's said but i still got the FATAL ERROR, i've build kismet over and over and as suid and not, i've cheked that my driver it's ipw3945, under the hardware information, but still i won't get it work.
after the make install of kismet, i've edited the kismet.conf.
and in the source part, i have this. source=ipw3945,eth1,Intel
and when i tried to run kismet i have the following output:

Server options:  none
Client options:  none
Starting server...
Will drop privs to tuto (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Support for capture source type 'ipw3945' was not built.  Check the output from 'configure' for more information about why it might not have been compiled in.
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}
Waiting for server to start before starting UI...

dunno what else i should do, i'm using ubuntu feisty, i've remembered that at my first time on this flavor, a warning notice came up, and it has to do with the wireless card, saying something like my card is using and not supported driver, or so, i really don't remember rigth now, it's been quite a while :/ but as i said before i've checked which is my driver under the hardware information and the driver it's the ipw3945.
please if anyone has a clue.

---

### Post by obitori on 2007-08-30
I was able to follow this thread and some other googled info to successfully produce a .deb of the Kismet source with the Intel PRO/Wireless driver built into it.  My Dell D820 works fine with Kismet now.  I listed the steps I took at the bottom of this thread:

[http://ubuntuforums.org/showthread.php?p=3284030#post3284030](http://ubuntuforums.org/showthread.php?p=3284030#post3284030)

Good luck!

---

### Post by sudomakemeasandwich on 2008-01-22
hi, 

i know the threat is old but i think i have the reason why kismet from the official rep dosnt work. 

take a look in the ./configure log, if theres a message like 

*"configure: WARNING: Compiling without libpcap support.  Many capture sources will be disabled."*

install *libpcap-dev*.

and sorry for my poor english ;)

---

