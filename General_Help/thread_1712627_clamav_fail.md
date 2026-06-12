---
title: "clamav fail"
date: 2011-03-23
forum: General Help
---

### Post by NoNameWill on 2011-03-23
I haven't been able to use clamav for a few weeks now. The problem I am having is the share library libclamav.so.6 won't open.

I have tried reinstalling it but that doesn't seem to work. This what I get in terminal. Any help will be appreciated. 

```
Setting up clamav-base (0.96.5+dfsg-1ubuntu1.10.04.2) ...

Setting up clamav-freshclam (0.96.5+dfsg-1ubuntu1.10.04.2) ...
 * Starting ClamAV virus database updater freshclam                            
 /usr/bin/freshclam: error while loading shared libraries: libclamav.so.6: cannot open shared object file: No such file or directory
                                                                         [fail]

Setting up clamav (0.96.5+dfsg-1ubuntu1.10.04.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
will@Mobile-laptop:~$ freshclam
freshclam: error while loading shared libraries: libclamav.so.6: cannot open shared object file: No such file or directory

```

---

### Post by uRock on 2011-03-23
Try running the following command. You have to give the application root privileges for it to run.```
sudo freshclam
```

---

### Post by NoNameWill on 2011-03-23
I get the same thing. I have been using clamav for a year now. It hasn't worked since Dec. actually.

---

### Post by NoNameWill on 2011-03-23
Anybody know how to fix this?

---

### Post by tredegar on 2011-03-23
It seems to me that if you are running windows, which is susceptable to viruses, trojans and malware, then run an anti-virus thing on windows. It should be fine-tuned to the OS.

If you are running linux, you (currently) do not need any this, though you do need common sense.

If your linux server is trying to abort windows viruses before they reach your windows clients, again I'd recommend you run such software on your windows clients, and not rely entirely on your linux server to protect windows.

Linux protects itself. Windows should do the same. It's probably best to use each OS's tools for protection, and not rely on cross-cover.

Hope this helps.

---

### Post by WorMzy on 2011-03-23
Try reinstalling libclamav6

```
sudo apt-get install --reinstall libclamav6
```

---

### Post by NoNameWill on 2011-03-24
No I am not using windows. Actually I have been using linux exclusively for almost a year. Ubuntu 10.4 popped my cherry. I like running the av every once in awhile. it takes about 15 minutes and runs without bogging anything down. Not a big deal. I had some funky stuff happen to my sourcelist. I actually had to manually fix some discrepancies. Maybe I was hacked. Don't know. 

I just tried the reinstall and still the same thing. I don't know what is going on. I have went digging around the bin file I believe that is the one. But anyway the libclam6 file is there. :confused:

---

### Post by WorMzy on 2011-03-24
If you're using Linux exclusively, then you really don't need an antivirus.

Still, if you want to fix it anyway, try purging all the clamav packages

```
sudo apt-get purge clamav clamav-base clamav-data clamav-docs clamav-freshclam libclamav6
```

Then reinstall them

```
sudo apt-get install clamav
```

If you use the GUI, you'll probably need to reinstall the clamtk package too.

```
sudo apt-get install clamtk
```

---

### Post by NoNameWill on 2011-03-24
Just did all that except the gui. Now synaptic crashes as soon as I open it. I tried this and this what I get

```
will@Mobile-laptop:~$ sudo apt-get -f install  synaptic
Reading package lists... Done
Segmentation faulty tree... 50%

```

I also got a warning that a man-db was missing

---

### Post by NoNameWill on 2011-03-24
never mind on the synaptic I did a ```
 sudo dpkg --configure -a 
``` 

so it works now

As for clam nada nothing.

---

### Post by WorMzy on 2011-03-24
I don't like how you ended up with a segmentation fault there. That could be a sign of bigger problems, like disk or memory failure.

I don't think that would cause this problem with clamav though. Have you added any custom repositories which could be interfering with the packages?

---

### Post by NoNameWill on 2011-03-24
Just Tor and FF betas

---

### Post by WorMzy on 2011-03-24
Could be that one of those repositories has a different version of clamav. What versions do you have installed?

```
dpkg -l "*clam*" | less
```

(stretch the terminal window until the full version number/id is visible, then copy-paste the whole lot here. (**in [CODE] tags, please**)

---

### Post by NoNameWill on 2011-03-25
I would like to say Thank you for helping me. WorMzy :D
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                      Version                           
                     Description
+++-=========================================-======================================================-============================================
un  clamav                                    <none>                                                 (no description available)
un  clamav-base                               <none>                                                 (no description available)
un  clamav-data                               <none>                                                 (no description available)
un  clamav-docs                               <none>                                                 (no description available)
rc  clamav-freshclam                          0.96.5+dfsg-1ubuntu1.10.04.2                           anti-virus utility for Unix - virus database
rc  clamtk                                    4.25-1                                                 graphical front-end for ClamAV
un  libclamav2                                <none>                                                 (no description available)
un  libclamav3                                <none>      
                      (no description available)
un  libclamav6                                <none>                                                 (no description available)
un  libclamunrar6                             <none>                                                 (no description available)
                 
```

This what I get. I think I did uninstall clamav through synaptic yesterday.

---

### Post by WorMzy on 2011-03-26
Could you reinstall clamav, then run that again, please.

---

### Post by NoNameWill on 2011-03-26
Ok here it is with clam installed.

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                      Version                           
                     Description
+++-=========================================-======================================================-====================================================
ii  clamav                                    0.96.5+dfsg-1ubuntu1.10.04.2                           anti-virus utility for Unix - command-line interface
ii  clamav-base                               0.96.5+dfsg-1ubuntu1.10.04.2                           anti-virus utility for Unix - base package
un  clamav-data                               <none>                                                 (no description available)
un  clamav-docs                               <none>                                                 (no description available)
ii  clamav-freshclam                          0.96.5+dfsg-1ubuntu1.10.04.2                           anti-virus utility for Unix - virus database update 
rc  clamtk                                    4.25-1                                                 graphical front-end for ClamAV
un  libclamav2                                <none>                                                 (no description available)
un  libclamav3                                <none>                                                 (no description available)
ii  libclamav6                                0.96.5+dfsg-1ubuntu1.10.04.2                           anti-virus utility for Unix - library
un  libclamunrar6                             <none>                                                 (no description available)
~
~

```

---

### Post by WorMzy on 2011-03-26
Okay, that looks fine. The only other thing that I can think of is that the permissions on the /usr/lib folder have been changed.

What does
```
ls -ld /usr/lib
```
say?

It should say something like:
```
drwxr-xr-x 173 root root 135168 Mar 26 09:32 /usr/lib
```

---

### Post by NoNameWill on 2011-03-26
Yes it says pretty much the same.
```
drwxr-xr-x 229 root root 73728 2011-03-26 09:11 /usr/lib

```

---

### Post by WorMzy on 2011-03-26
Well, I'm sorry to say that your problem has me stumped. The versions match up to the repo packages, the permissions look fine, and you've purged and reinstalled so config files should be fine (not that I'd expect a misconfigured config file to cause this behaviour in the first place).

All I have left to go on is that segmentation fault from before, which could signify that your disk is failing, but if that was the case I'd expect much more wide-spread problems, and not just a problem with a single application.

All I can suggest is that you stick around and hope that someone else can shed some light on to this. Sorry. :(

---

### Post by NoNameWill on 2011-03-27
Thank you for your time to help me. If anything if gave me more experience working with command line.

---

### Post by NoNameWill on 2011-05-24
WorMzy is right my drive is failing. At the time it didn't show up in SMART utility. I did do memtest and found some flaky RAM.  I have since updated to 11.04 and clam av is working fine. Haven't changed the drive yet. But is on the list. If it does just crap out there is always a live usb/sd. 

Will mark this as solved as I believe it to be related to a failing drive.

---

