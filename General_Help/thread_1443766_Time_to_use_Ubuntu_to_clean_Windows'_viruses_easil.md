---
title: "Time to use Ubuntu to clean Windows' viruses easily and effectively"
date: 2010-03-31
forum: General Help
---

### Post by HotForLinux on 2010-03-31
I have encouraged many people to install and try Ubuntu by telling them, among other things, that in case of a failure in their windos system, they could, very likely,  boot their PC with Linux, work with an office suite, access their files, browse the internet, send mails, chat, IP phone or take it easy: listen to their favorite music and relax; then scan for viruses and, hopefully, even repair their stinky windos system.

Now I have windos infected with viruses. I installed and ran **clamav** which detected a whole family: grandparents, grand sons and cousins included. Here's the summary until now:

```
[B]
$ clamscan -ri /home[/B]
 - nothing -

**$ sudo clamscan -ir /windows/D**
 - nothing found -

**$ sudo clamscan -ir /windows/C/**
[COLOR=Red]/windows/C/Archivos de programa/Norton AntiVirus/Quarantine/4A113FA5.exe: Trojan.ShipUp-3 FOUND
/windows/C/Archivos de programa/Norton AntiVirus/Quarantine/4A9A230E.exe: Trojan.Backdoor-3 FOUND
/windows/C/Archivos de programa/Norton AntiVirus/Quarantine/4A9D4D0A.exe: Trojan.ShipUp-2 FOUND
/windows/C/Archivos de programa/Norton AntiVirus/Quarantine/4AAE1EF8.exe: Trojan.ShipUp-5 FOUND
/windows/C/Documents and Settings/Administrador/Configuración local/Temp/h8my7hut.dll: Trojan.Spy-33995 FOUND
/windows/C/Documents and Settings/user/Configuración local/Archivos temporales de Internet/Content.IE5/4I7QRV4E/help[1].exe: Trojan.Agent-22618 FOUND
/windows/C/Documents and Settings/user/Configuración local/Temp/7bpapp.dll: Trojan.Spy-40995 FOUND
/windows/C/Documents and Settings/user/Configuración local/Temp/m7.dll: Trojan.Spy-39970 FOUND
/windows/C/Documents and Settings/user/Configuración local/Temp/tru1.tmp: Worm.Autorun-790 FOUND
/windows/C/Documents and Settings/user/Configuración local/Temp/tru2.tmp: Trojan.Spy-33519 FOUND
/windows/C/Documents and Settings/user/Configuración local/Temp/h8my7hut.dll: Trojan.Spy-33995 FOUND
/windows/C/Documents and Settings/user/Configuración local/Temp/help.exe: Trojan.Agent-22618 FOUND
/windows/C/oq.cmd: Worm.Autorun-1328 FOUND
/windows/C/WINDOWS/system32/ActiveScan/pskavs.dll: Sirius.Annihilator.272 FOUND
/windows/C/WINDOWS/system32/amvo0.dll: Trojan.Spy-34024 FOUND[/COLOR]

----------- SCAN SUMMARY -----------
Known viruses: 750450
Engine version: 0.95.3
Scanned directories: 9957
Scanned files: 98661
Infected files: 15
Data scanned: 14201.36 MB
Data read: 20727.70 MB (ratio 0.69:1)
Time: 5765.640 sec (96 m 5 s)

** $ sudo clamscan -ir /windows/E**
[COLOR=Red]/windows/E/oq.cmd: Worm.Autorun-1328 FOUND[/COLOR]

----------- SCAN SUMMARY -----------
Known viruses: 750872
Engine version: 0.95.3
Scanned directories: 340
Scanned files: 3221
Infected files: 1
Data scanned: 612.14 MB
Data read: 13646.46 MB (ratio 0.04:1)
Time: 130.126 sec (2 m 10 s)


```.
The root Ubuntu's dir not scanned (haha ...  don't tell me that is really important?)

Now, **WHAT'S NEXT?**
What is the heuristic? what should be and should not be done to deal with it carefully and effectively as much as we can from Ubuntu?

---

### Post by 2hot6ft2 on 2010-03-31
Ok. First you want to enable the Delete bypassing the trash. Otherwise when you move them to the trash they will still be there (just in a trash bin).
Open a folder and click on Edit then Preferences
Behaviour tab and check the box for Include a delete command that bypasses trash.
The ones in the Norton Quarantine folder should be deleted using Norton to empty the quarantine folder contents.
But you can get rid of the rest first so it can't spread again when windows is started.

Then just browse to each one and right click on it and select Delete.

You can enable heuristic and scan it again that's best explained here:
[http://en.wikipedia.org/wiki/Heuristic_algorithm](http://en.wikipedia.org/wiki/Heuristic_algorithm)

I didn't see anything that looked like it would affect the windows operating system in the list so it should be ok to completely delete them.

---

### Post by 2hot6ft2 on 2010-03-31
Basically these are the main ones
> **HotForLinux said:**
> 

[COLOR=Red]
/windows/C/Documents and Settings/user/Configuración local/Archivos temporales de Internet/Content.IE5/4I7QRV4E/[COLOR="Black"]help[1].exe[/COLOR]: Trojan.Agent-22618 FOUND
/windows/C/[COLOR="Black"]oq.cmd[/COLOR]: Worm.Autorun-1328 FOUND
/windows/C/WINDOWS/system32/ActiveScan/[COLOR="Black"]pskavs.dll[/COLOR]: Sirius.Annihilator.272 FOUND
/windows/C/WINDOWS/system32/[COLOR="Black"]amvo0.dll[/COLOR]: Trojan.Spy-34024 FOUND[/COLOR]
[COLOR=Red]/windows/E/[COLOR="Black"]oq.cmd[/COLOR]: Worm.Autorun-1328 FOUND[/COLOR]


Several of the others are in temp folders but you may as well kill them too while you're at it.
And these are the ones in temp folders

> **HotForLinux said:**
> 
[COLOR=Red]/windows/C/Documents and Settings/Administrador/Configuración local/Temp/[COLOR="Black"]h8my7hut.dll[/COLOR]: Trojan.Spy-33995 FOUND
/windows/C/Documents and Settings/user/Configuración local/Temp/[COLOR="Black"]7bpapp.dll[/COLOR]: Trojan.Spy-40995 FOUND
/windows/C/Documents and Settings/user/Configuración local/Temp/[COLOR="Black"]m7.dll[/COLOR]: Trojan.Spy-39970 FOUND
/windows/C/Documents and Settings/user/Configuración local/Temp/[COLOR="Black"]tru1.tmp[/COLOR]: Worm.Autorun-790 FOUND
/windows/C/Documents and Settings/user/Configuración local/Temp/[COLOR="Black"]tru2.tmp[/COLOR]: Trojan.Spy-33519 FOUND
/windows/C/Documents and Settings/user/Configuración local/Temp/[COLOR="Black"]h8my7hut.dll[/COLOR]: Trojan.Spy-33995 FOUND
/windows/C/Documents and Settings/user/Configuración local/Temp/[COLOR="Black"]help.exe[/COLOR]: Trojan.Agent-22618 FOUND
[/COLOR]


---

### Post by HotForLinux on 2010-03-31
Hey thanks!.
That's what I thought to be the main problem: determining whether I can delete a file or not. I suppose that sometimes viruses are inside important files. Becasue often you see warnings regarding deleting infected files, besides the fact that they can survive to the delete operation. But how do you know if these files are not used by the system or any other program?

If I delete them with the file manager they would go (by default) to Ubuntu's trash can, not windos' trash, right?

After enabling the option, to bypass the trash can I can also do shift+delete, right?

or I can do it from the command line, like this

$cat <<EOF  |xargs rm 
...and paste here the list of infected files (except norton ones)
ctrl+D

or maybe rm -f
and check they are all deleted and not in the (which?) trash

am I right?

---

### Post by HotForLinux on 2010-03-31
It's the first time...
I decided to scan the Ubuntu's root directory too excluding some of them like /dev, /proc, ....

Obviously no virus found but apart from many:

```
WARNING: Can't open file ......file_name.....
```messages for write only files (they exist!?)

I also received many:
```

LibClamAV Error: cli_readn: read error: No such device
LibClamAV Error: cli_readn: read error: Input/output error
LibClamAV Error: cli_readn: read error: Function not implemented

```
So, I can't tell what happened.
At least this didn't happen when scanning Windos partitions.

---

### Post by dcstar on 2010-03-31
> **HotForLinux said:**
> It's the first time...
I decided to scan the Ubuntu's root directory too excluding some of them like /dev, /proc, ....

Obviously no virus found but apart from many:

```
WARNING: Can't open file ......file_name.....
```messages for write only files (they exist!?)

I also received many:
```

LibClamAV Error: cli_readn: read error: No such device
LibClamAV Error: cli_readn: read error: Input/output error
LibClamAV Error: cli_readn: read error: Function not implemented

```
So, I can't tell what happened.
At least this didn't happen when scanning Windos partitions.

Running programs in user mode does not allow access to system files.

Run with sudo if you want access to everything.

---

### Post by HotForLinux on 2010-04-02
> **dcstar said:**
> Running programs in user mode does not allow access to system files.

Run with sudo if you want access to everything.
.

Sudo, sudo,...  I have just double checked with ***history***. The syntaxis of the command I executed was:
  
```

**$for i in  initrd  initrd.img.old  lib64  etc mnt   sbin  sys  usr  vmlinuz boot initrd.img  lib root tmp vmlinuz.old var; do _sudo_ clamscan -ir $i; done**
```(I wanted to exclude some directories like  /home and /proc, for instance.) I had to introduce two or three times the passwd for sudo  because I still don't know how to sudo a whole succession of commands, nor a loop structure (like a **for)** in a single command line. Do you?

---

### Post by HotForLinux on 2010-04-02
I have just done it again (_WITH SUDO_.... Why not??... Have you tried it?)

**$sudo clamscan -ir / --exclude-dir='home'**

And receive the same messages. A bunch of each:

**Can't open file /../*file_name***

for files that are writable only.

**LibClamAV Error: cli_readn: read error: No such device**

which device?

**LibClamAV Error: cli_readn: read error: Input/output error**
[B]LibClamAV Error: cli_readn: read error: Input/output error
LibClamAV Error: cli_readn: read error: Input/output error
LibClamAV Error: cli_readn: read error: Input/output error
.... 

[/B]why/where?
[B]
LibClamAV Error: cli_readn: read error: Function not implemented
LibClamAV Error: cli_readn: read error: Function not implemented
LibClamAV Error: cli_readn: read error: Function not implemented[/B]
**....**

what function?

Am I doing something illegal?

---

### Post by KayakJim on 2010-04-02
If you are running Ubuntu from a Live CD then you do not need to scan it and you are wasting your time doing so.

Concentrate on removing the viruses from your Windows partitions.

---

### Post by theozzlives on 2010-04-02
try:
```
mkdir /windows/c/virus
clamscan -ri --move=/windows/c/virus /windows/c
sudo rm -rf /windows/c/virus
```
the only dangerous virus I've encountered (recently) is one that infects system32.dll. After the scan, boot Windows and run sfc.exe.

---

### Post by HotForLinux on 2010-04-03
> **KayakJim said:**
> If you are running Ubuntu from a Live CD then you do not need to scan it and you are wasting your time doing so.

Concentrate on removing the viruses from your Windows partitions.

From a Live-CD? ... I am not. 
I scanned the Linux partitions for curiosity, ... just to see what..., and to prove that were are no viruses living there. I never expected to find one. But anyway, the truth is that that's the output.

---

### Post by HotForLinux on 2010-05-25
OK. This is the bad (or sad) news:

After deleting all those files in Windos' partition ... two weeks later I booted windows for the first time; connected to the Internet, dowloaded and installed the free version of AVG antivirus. The AVG antivirus detected many other infected files that ClamAV didn't. And I'm talking about very old infected files here. When I ran ClamAV that windos system hadn't been used for a year or more.
I don't know... But I say it is sad because Clam doesn't seem to be reliable at all.

---

### Post by howefield on 2010-05-25
> **HotForLinux said:**
> OK. This is the bad news

Might be bad news but certainly not unusual or new.

There are huge variations in the detection rates of anti virus applications, just like anti spyware applications.

Some really are better than others., you just gotta do the research and use the one you believe will do the best job.

Nothing wrong in using more than one, as long as you don't run concurrent background scanners.

---

### Post by HotForLinux on 2010-05-25
> **howefield said:**
> Might be bad news but certainly not unusual or new.

There are huge variations in the detection rates of anti virus applications, just like anti spyware applications.

Some really are better than others., you just gotta do the research and use the one you believe will do the best job.

Nothing wrong in using more than one, as long as you don't run concurrent background scanners.


Yes , Ok. I supposed those variations were normal when talking about new viruses, but one year old ones..??!!

---

