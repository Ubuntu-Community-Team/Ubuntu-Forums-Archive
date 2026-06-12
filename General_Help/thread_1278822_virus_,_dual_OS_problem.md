---
title: "virus , dual OS problem"
date: 2009-09-30
forum: General Help
---

### Post by kane88 on 2009-09-30
what will happen if a .exe virus crepts into my system when i am using ubuntu. I ask this because it can do nothing in ubuntu but it can do something when i use windows . i use both OS . is there a solution or am i perceiving something wrong .

kane

---

### Post by lisati on 2009-09-30
Keep your AV software up to date, do regular scans, and don't open files you don't trust.

---

### Post by MelDJ on 2009-09-30
> **kane88 said:**
> what will happen if a .exe virus crepts into my system when i am using ubuntu. I ask this because it can do nothing in ubuntu but it can do something when i use windows . i use both OS . is there a solution or am i perceiving something wrong .

kane

if you dont open the file in windows then dont worry

---

### Post by bruno9779 on 2009-09-30
If you explain in more detail what do you mean by "i can't do anyuthing in ubuntu", and if it is a wubi dual boot or what, someone here will surely be able of helping you out

---

### Post by kane88 on 2009-09-30
i mean when my system starts in XP then the virus that had crept while i was surfing in ubuntu will become active.

i ask this because my friend was visiting a serial/crack website and he downloaded 2-3 keygens (all .exe file) at night and the very next day three things happened .
1. a message continuously displayed system antivirus out of date whereas he have a commercial kaspersky internet security.
2. 3 large folders in D:drive  were deleted.
3. nothing was working except task manager(which was only displaying)but some dll with size 1-2 MB were running(not remembered exact names).

so this means ubuntu  is less secure because instead of blocking virus at port , it disables then from running.

My friend & myself both are new to linux ubuntu . so i decided uninstalling ubuntu is better .
i need somehelp , please help me out , ubuntu really looks cool & i want to use it.
:(:(:(:(:(:(:(:confused:

---

### Post by mharrison on 2009-09-30
> **kane88 said:**
> i mean when my system starts in XP then the virus that had crept while i was surfing in ubuntu will become active.

i ask this because my friend was visiting a serial/crack website and he downloaded 2-3 keygens (all .exe file) at night and the very next day three things happened .
1. a message continuously displayed system antivirus out of date whereas he have a commercial kaspersky internet security.
2. 3 large folders in D:drive  were deleted.
3. nothing was working except task manager(which was only displaying)but some dll with size 1-2 MB were running(not remembered exact names).

so this means ubuntu  is less secure because instead of blocking virus at port , it disables then from running.

My friend & myself both are new to linux ubuntu . so i decided uninstalling ubuntu is better .
i need somehelp , please help me out , ubuntu really looks cool & i want to use it.
:(:(:(:(:(:(:(:confused:


It does not mean Ubuntu is less secure.  It means you practiced unsafe surfing.  The virus didn't "creep" into your Windows system, you put it there.  If he was downloding Keygens and Cracks on Ubuntu, the .EXE would be a file you could no nothing with (short of WINE).  Since the virus cannot be activated in Ubuntu, it would not have any affect on your Windows system unless you manually copied the file there, and even if you did, you would have to run the file in order to activate the virus in most cases....depending on the virus.

---

### Post by JigglyWiggly_ on 2009-09-30
Just a note of advice some viruses do work in wine and will do some weird things to your Linux system.Way to stop that is preventing Wine from accessing anywhere other than itself.

---

### Post by kane88 on 2009-09-30
> **mharrison said:**
> you would have to run the file in order to activate the virus in most cases....depending on the virus.

yeah i agree it was a mistake but the virus ran automatically even before kaspersky started , so what to do. it was a mistake but what if it crept sometime when my internet connection is idle . one more thing is there any firewall sort of thing in ubuntu .i am new so don't have any ideas on ubuntu's traffis monitering abilities.

explain in brief

---

### Post by seehymeh on 2009-09-30
[http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

Here's a great security post that I found a while back, I think it really applies here and you should check it out.  It's a little long, but very useful.  

> 
If you are coming from a windows background you are used to terms like antivirus, spyware, and firewalls. Linux is different and these are not as important

---

### Post by Commander_Keen on 2009-09-30
If you feel that you ahve a virus on your system.
You can download a linux Antivrus system and run on it your XP drive.
Also.. I would install Virutal box., Install XP. Creat a copy that install.
and then suff using that imaage of XP.
If you get a virus, you can always del that image fo XP and restart from a fresh copy.

---

### Post by badger_fruit on 2009-09-30
> **kane88 said:**
> i mean when my system starts in XP then the virus that had crept while i was surfing in ubuntu will become active.


Not quite.
Let's say you're in Ubuntu and download an EXE file which holds a virus.  Run it. Ubunutu goes "WTF is this" and refuses to run an EXE file as it's made for Windows.

The result is your PC is safe as nothing was executed.

Let's say you then boot into Windows and run the same file.
BANG, your Windows is infected.

Reboot back into Ubuntu and the virus is "gone", it's not active in your Linux booted OS.
Of course, go back into Windows and it's still going to be there.

Of course, if you DON'T RUN THE FILE IN WINDOWS then it won't infect it.

As others have said, ALWAYS make sure Windows has an up-to-date Anti-virus and anti-spyware tools installed and running. In linux you're safe as the virus writers only bother (so far!) with Windows.

Mainly because 95% of the worlds computers run it (that's like billions of machines) compared to only 3% which run *nix.

---

### Post by 3rdalbum on 2009-09-30
1. By and large, it's not likely that anything will "creep into" your Ubuntu system. You need to explicitly download it. Then give it execute permission. Then run it. If it's a Windows-based virus, it won't run without Wine (and probably won't run with it either).

2. If you download shady illegal software like cracks and keygens, DO NOT expose those things to your Windows. Full-stop. Because they *do* contain malware. It's safe to download them on Ubuntu, but not safe to run them in Wine or on Windows.

3. Ubuntu is not "less secure" than Windows, full-stop, I don't care how many anti-virus programs you have running on your Windows system.

> it was a mistake but what if it crept sometime when my internet connection is idle . one more thing is there any firewall sort of thing in ubuntu .i am new so don't have any ideas on ubuntu's traffis monitering abilities.

It's late, I don't want to have to explain what a firewall does again! :-)

Nothing can "creep in" while your internet connection is idle, unless you have programs that are listening to incoming connections and are not hardened for security. By default, on Ubuntu there is NOTHING that will listen to incoming connections, unless you install server software.

If anything tries to contact your computer on a port where no program is listening, they will get a reply the equivalent of "wrong number". Or, they will receive no reply, as though your computer was not there. They will not have the chance to push any data to your computer.

Are you aware that firewalls are not traffic-monitoring devices? They simply block all incoming connections except ones that you have authorised. They don't know the difference between an HTTP packet, a streaming video file, a virus, or anything. They just know what port number a connection is coming in on, and whether you have given permission for that port or not. If you haven't given permission for that port, then it destroys the connection and doesn't respond.

On a default installation of Windows, there is software that has known security problems, that listens to incoming connections, and can be tricked into recieving software and running it. Windows users run personal firewalls to block out those insecure programs. Of course, no such vulnerable software exists in a default install of Ubuntu, so you don't need a personal firewall.

If you really want to configure your firewall, you can download gUFW from the repositories.

Believe me, you're essentially safe on Ubuntu. Use your common sense and don't turn off any security features and you'll be safe. Be aware of phishing scams and things like that, too. And stop downloading warez.

---

### Post by mikewhatever on 2009-09-30
> **kane88 said:**
> i mean when my system starts in XP then the virus that had crept while i was surfing in ubuntu will become active.

i ask this because my friend was visiting a serial/crack website and he downloaded 2-3 keygens (all .exe file) at night and the very next day three things happened .
1. a message continuously displayed system antivirus out of date whereas he have a commercial kaspersky internet security.
2. 3 large folders in D:drive  were deleted.
3. nothing was working except task manager(which was only displaying)but some dll with size 1-2 MB were running(not remembered exact names).

Let's put things in order here. 
First, nothing has crept in, it was your friend who went to a questionable site and downloaded questionable files.
Second, had the downloaded files been on the Ubuntu partition, they would have remained harmless, since Windows doesn't recognize ext file system. This implies, that your friend took the effort to copy the files over to the Windows partition, and to the very specific places from were they could run at boot. 

> so this means ubuntu  is less secure because instead of blocking virus at port , it disables then from running.

Nothing can stop a fool from running malicious software, besides, why should Ubuntu care to protect Windows anyway.

> My friend & myself both are new to linux ubuntu . so i decided uninstalling ubuntu is better .
i need somehelp , please help me out , ubuntu really looks cool & i want to use it.
:(:(:(:(:(:(:(:confused:

Well, the choice is yours. Get the Windows bootloader restored, then delete the Ubuntu partition.

---

