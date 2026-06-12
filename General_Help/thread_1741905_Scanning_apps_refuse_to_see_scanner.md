---
title: "Scanning apps refuse to see scanner"
date: 2011-04-28
forum: General Help
---

### Post by Objekt on 2011-04-28
I have a Brother MFC-7440N, which includes a scanner.  I used it under Ubuntu - first 9.10 and more recently 10.04 - many times, both to print and scan.  But suddenly, starting a few weeks ago, I can't scan.

Whenever I try to do scanning, with Skanlite or GScan2pdf for example, I get an error message stating something to the effect of "cannot find any scanners."  

This is a ridiculous error message.  The scanner is most definitely present, and I installed the Brother drivers for it.  The scanner works fine from a scanning app running on a Windows XP virtual machine under Virtualbox.

What is going on here, and how do I fix it?

---

### Post by Leppie on 2011-04-28
are you still able to print to the brother 7440N?
could you post the output of the following command:
```
scanimage -L
```

---

### Post by wizard10000 on 2011-04-28
saned is disabled by default - did you enabled it?

Look at /etc/default/saned - that's all I got.  Maybe someone else has something else.

```
# Defaults for the saned initscript, from sane-utils

# Set to yes to start saned
RUN=no

# Set to the user saned should run as
RUN_AS_USER=saned
```

Good luck -

---

### Post by Objekt on 2011-04-28
> **Leppie said:**
> are you still able to print to the brother 7440N?

Yes.


> **Leppie said:**
> could you post the output of the following command:
```
scanimage -L
```

```
user4@user4-desktop:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
user4@user4-desktop:~$
```

I used the scanner plenty of times before without having to enabled saned (at least as far as I know, it could have occurred as part of a script).  That is, I've changed nothing, but now scanning doesn't work.

I expect one of the many updates in the last few months has broken scanning.  It wouldn't be the first time an "update" wrecked something that had been working.

---

### Post by Leppie on 2011-04-28
could you post the output of the following commands:
```
id saned
dpkg -l | grep -i brother
lsusb
```

---

### Post by Objekt on 2011-04-28
```
user4@user4-desktop:~$ cd /etc/default/saned
bash: cd: /etc/default/saned: Not a directory
user4@user4-desktop:~$ id saned
uid=112(saned) gid=118(saned) groups=118(saned)
user4@user4-desktop:~$ dpkg -l | grep -i brother
ii  brmfc7440nlpr                        2.0.2-1                                         Brother MFC-7440N LPR driver
ii  cupswrappermfc7440n                  2.0.2-1                                         Brother MFC7440N CUPS wrapper driver
```

This is a networked device, so it has a local IP address but would not show up in a USB scan.

It might be something really stupid, like I forgot to reinstall the scanner driver.  I uninstalled/reinstalled the other drivers a few weeks ago, because I suddenly could not print (which turned out to not be the solution).

update: Yes, that was it.  I had to reinstall the scanner driver and do a couple of other things.  Instructions here: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html")

For those finding this thread in the future, there are a couple of pitfalls in those instructions, if you want to set your MFC-7440N up networked as I did.  The page gives the command you should use as:
```
    5-1. Add network scanner entry

        Command  :  brsaneconfig2  -a  name=(name  your  device)  model=(model  name)  ip=xx.xx.xx.xx 
```

Two points:
1) (name your device) should be replaced entirely.  It can be any name you want.  Likewise for (model name) but it would probably be best to use the actual model name.  My command looked like this:
```
user4@user4-desktop:~$ sudo brsaneconfig3 -a  name=BrotherMFC  model=MFC-7440N  ip=192.168.1.18
```

2) Note that it is brsaneconfig**3** you want, not brsaneconfig**2** as in the instructions.

---

### Post by Leppie on 2011-04-28
so you are scanning over ip?
try the following command:
```
sudo adduser saned lp
```

---

### Post by plucky on 2011-04-28
This command should tell you if the scanner driver is installed ```
 dpkg -l | grep Brother
```

note the capital B in Brother as the lowercase b will just show the printer drivers.

Good Luck

---

### Post by Leppie on 2011-04-28
> **plucky said:**
> This command should tell you if the scanner driver is installed ```
 dpkg -l | grep Brother
```note the capital B in Brother as the lowercase b will just show the printer drivers.

Good Luck
he already posted the output:
```
user4@user4-desktop:~$ dpkg -l | grep -i brother
ii  brmfc7440nlpr                        2.0.2-1                                         Brother MFC-7440N LPR driver
ii  cupswrappermfc7440n                  2.0.2-1                                         Brother MFC7440N CUPS wrapper driver
```
fyi, the -i option makes the search case insensitive

---

### Post by plucky on 2011-04-28
> **Leppie said:**
> he already posted the output:
```
user4@user4-desktop:~$ dpkg -l | grep -i brother
ii  brmfc7440nlpr                        2.0.2-1                                         Brother MFC-7440N LPR driver
ii  cupswrappermfc7440n                  2.0.2-1                                         Brother MFC7440N CUPS wrapper driver
```
fyi, the -i option makes the search case insensitive

That means the scanner driver is not installed.

---

### Post by roger_1960 on 2011-04-28
Hi

When you reinstalled drivers, did you remember to do this:

    1. Open "/lib/udev/rules.d/40-libsane.rules" file.
    2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):


    The lines to be added--------------------------- 


    # Brother scanners
    ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
     

    3. Restart the OS. 

(Taken from the Brother website)  Its a common reason for just the scanner not to work.

---

