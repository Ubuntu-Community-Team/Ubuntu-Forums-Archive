---
title: "Thunderbird 5 will not load"
date: 2011-08-07
forum: General Help
---

### Post by Robbyx on 2011-08-07
I can not make the upgrade from 3.11 to 5 load. When I run it from the terminal this is what I get:

```
robin@robin-EP35-DS3L:~$ thunderbird
Traceback (most recent call last):
  File "/usr/lib/thunderbird-5.0/xulapp-profilemigrator", line 457, in <module>
    migrator = ProfileMigrator (options)
  File "/usr/lib/thunderbird-5.0/xulapp-profilemigrator", line 193, in __init__
    this.profile = ProfileFolder (options.profile)
  File "/usr/lib/thunderbird-5.0/xulapp-profilemigrator", line 119, in __init__
    this.build_list_of_subprofiles ()
  File "/usr/lib/thunderbird-5.0/xulapp-profilemigrator", line 133, in build_list_of_subprofiles
    profiles_ini.read (os.path.join (this.path, 'profiles.ini'))
  File "/usr/lib/python2.7/ConfigParser.py", line 297, in read
    self._read(fp, filename)
  File "/usr/lib/python2.7/ConfigParser.py", line 504, in _read
    raise MissingSectionHeaderError(fpname, lineno, line)
ConfigParser.MissingSectionHeaderError: File contains no section headers.
file: /home/robin/.thunderbird/profiles.ini, line: 1
'\xef\xbb\xbf[General]\n'
robin@robin-EP35-DS3L:~$ 

```

Does anyone recognise what I should do to get TB working?

---

### Post by Robbyx on 2011-08-07
Can someone please comment as to how to correct this problem.

---

### Post by Robbyx on 2011-08-08
I can not get TB5 it install in ubuntu so that it starts and sees my old messages. In fact it does not load. Could someone with more experience than me,  please suggest what I should do now.

---

### Post by magic8ball on 2011-08-08
I'm not very experienced with Ubuntu and can't provided much (or maybe any) help, but I just upgraded my Ubuntu 10.04 64-bit to Thunderbird 5 using the instructions in the following link (see post #572 and #573):

[http://ubuntuforums.org/showthread.php?p=10690985&highlight=thunderbird#post10690985](http://ubuntuforums.org/showthread.php?p=10690985&highlight=thunderbird#post10690985)

I also added the 4th step of doing "sudo apt-get install thunderbird", but I don't know if that is really required.

That's all I know.  Good Luck!

---

### Post by Robbyx on 2011-08-08
Thank you. It did not make any difference for me. Same problem.

---

### Post by SpkrBox850 on 2011-08-10
I was having the same problem 
Im NOT an expert and i dont know if this was the "correct" way to do it but it defiantly worked:

1. I uninstalled Thunderbird via the software center

2. From terminal i ran:
> sudo add-apt-repository ppa:mozillateam/thunderbird-stable 

3. Then i installed this manually via web browser to package installer:
[https://launchpad.net/~mozillateam/+archive/thunderbird-stable/+files/thunderbird-dev_5.0%2Bbuild1%2Bnobinonly-0ubuntu0.10.04.1%7Emts1_i386.deb]("https://launchpad.net/%7Emozillateam/+archive/thunderbird-stable/+files/thunderbird-dev_5.0%2Bbuild1%2Bnobinonly-0ubuntu0.10.04.1%7Emts1_i386.deb")

>At this point version 5.0 was installed and working great but when i went to the software center, it was showing that the developers version was installed (Email, RSS, and newsgroup client - development files, thunderbird-dev) and the regular one was not so...

4. From the software center I removed that development package and installed the regular Thunderbird. Thats it... its showing up as 5.0 in 'Help>About' and running awesome. 

Does anybody know why that worked? 

-Good luck

---

### Post by Robbyx on 2011-08-11
Thank you for your reply. I have deteriorated from no email program to no operating system. When I can get back into Ub I will try your solution. I am waiting for replies to other threads for help to get into Ub.

---

