---
title: "Need Scripting Help"
date: 2006-05-30
forum: General Help
---

### Post by deejross on 2006-05-30
Hello, I am having problems with the Wildfire IM Server. I will simply stop working without warning or error after a few days. Until recently, the only way to get it working again was to reboot the entire machine. Recently, however, I was given a tip that forces the port on which the server was using closed. But now I would like to script this action, so that anyone with access to the machine can kill and restart the process with the click of a button.

Here is what I do now:
Open Terminal and login as root

First I type:
# lsof -i | grep 5222

This returns the following line:
java     18197     root     16u    IPv6     323595      TCP *:5222 (LISTEN)

Then, I type:
# kill -9 18197

I have a little understanding as to what is happening here. The lsof gets the used ports and the PID's using them, then grep only shows entries that contain "5222". But my question is: How can I take the PID number from the above string and put it into a kill command? I know enough about linux to install it and configure a couple servers. I am getting to know the basics of console operations, but mostly, I use Webmin for everything.

Thanks in advance for you help! :D

---

### Post by IYY on 2006-05-30
kill -9 `lsof -i | grep 5222 | cut -d\  -f2`

The cut command takes two arguments: -d is the delimiter (in our case, it is space), and -f is the field number. So, we take field #2 of the result of lsof -i | grep 5222. Field #2 would be the PID.

---

### Post by nanotube on 2006-05-30
well, first, since you are only interested in tcp ports, you might want to use "netstat -pluant" instead of lsof, it outputs only tcp information.
now, here is how you can get the pid isolated.
now, the following line will get the PID isolated:

```
sudo netstat -pluant |grep ":5222" | awk '{print $7}' |sed -e 's@/.*@@'
```
(note the colon in front of 5222 - this is to make sure we just match the port 5222, but not a pid 5222, if there does happen to be one)

and now all you need to do is shove it into a kill
so put it together, and you have
```
kill -9 `sudo netstat -pluant |grep ":5222" | awk '{print $7}'|sed -e 's@/.*@@'`
```

---

### Post by nanotube on 2006-05-30
[QUOTE=IYY]kill -9 `lsof -i | grep 5222 | cut -d\  -f2`

The cut command takes two arguments: -d is the delimiter (in our case, it is space), and -f is the field number. So, we take field #2 of the result of lsof -i | grep 5222. Field #2 would be the PID.[/QUOTE]
much simpler than mine :) but won't work if the server process is running as root... first, lsof wont output it without sudo, second, kill wont kill it without sudo, even if lsof did output it. :) but this does remind me that i probably should have used cut rather than breaking out sed. but oh well. also, cut -d\ will break on every space - so if there is more than one space, it will count that many fields. not very convenient. (so in your case, -f2 would give you an empty field. at least that's the way cut works on breezy).

---

### Post by IYY on 2006-05-30
Well, he did say that he logs in as root when he does this. And of course, he could just run

sudo kill -9 `lsof -i | grep 5222 | cut -d\ -f2`

---

### Post by deejross on 2006-05-30
Wow, thanks for responding so quickly and with great examples. I probably should have mentioned that I would putting this command into a script button into Webmin that runs commands as root ;)

---

### Post by nanotube on 2006-05-30
[QUOTE=IYY]Well, he did say that he logs in as root when he does this. And of course, he could just run

sudo kill -9 `lsof -i | grep 5222 | cut -d\ -f2`[/QUOTE]

note what i said (after an edit, admittedly...) about cut -d\ . multiple spaces count. so it still wouldn't work. is that not the same on your machine?

---

### Post by deejross on 2006-05-30
When running the

```
kill -9 `lsof -i | grep 5222 | cut -d\ -f2`
```

script, I get the error "cut: the delimiter must be a single character"
and I also get the "kill: usage" message

---

### Post by nanotube on 2006-05-30
[QUOTE=deejross]When running the

```
kill -9 `lsof -i | grep 5222 | cut -d\ -f2`
```

script, I get the error "cut: the delimiter must be a single character"[/QUOTE]
yea, first of all (i found out after some testing... i havent used cut to cut on space before) you need to put two spaces after the \. that way, the first space goes into the delimiter, and the second space separates it from the second parameter -f. that will take care of your error.
but anyway, delimiting with space is not a great idea, for reason i stated in earlier post. :)

instead, try 
kill -9 `netstat -pluant |grep ":5222" | awk '{print $7}' | cut -d/ -f1`

---

### Post by IYY on 2006-05-30
Should be two spaces after the \. I think the forum software automatically converted it to one space because I forgot the code tag.

Anyway, -f2 seems to work for me.

---

### Post by nanotube on 2006-05-30
[QUOTE=IYY]Should be two spaces after the \. I think the forum software automatically converted it to one space because I forgot the code tag.

Anyway, -f2 seems to work for me.[/QUOTE]
strange... well, maybe it will work for him, too :)

---

### Post by deejross on 2006-05-30
ok, guess I need to install awk for the other command to work. It says "grep: awk: No such file or directory", "grep: {print $7}: No such file or directory".

---

### Post by deejross on 2006-05-30
Well, there seems to be a bigger problem now...the entire machine just down a few minutes ago and I won't be able to reboot it until some time tomorrow. This is the second time in the last couple weeks it has just stopped working. Anyone have any ideas as to why this is happening?

---

### Post by nanotube on 2006-05-30
[QUOTE=deejross]ok, guess I need to install awk for the other command to work. It says "grep: awk: No such file or directory", "grep: {print $7}: No such file or directory".[/QUOTE]
well, if it says "grep: awk" that means the error is in grep, not in awk. which means that you probably mistyped/mispasted the command. awk and grep are both present on a standard install of ubuntu.

---

### Post by nanotube on 2006-05-30
[QUOTE=deejross]Well, there seems to be a bigger problem now...the entire machine just down a few minutes ago and I won't be able to reboot it until some time tomorrow. This is the second time in the last couple weeks it has just stopped working. Anyone have any ideas as to why this is happening?[/QUOTE]
hmm, you should probably start another thread for this issue... but anyway, check your logs in /var/log and see if you see anything suspicious there. specifically /var/log/dmesg...

---

### Post by deejross on 2006-05-30
Well, I might have solved all the problems, but I will won't find out for a few days (until is breaks again). I tried both commands when the IM server crashed. Linux froze at the command line when trying either command. I let it sit for 10 minutes, and nothing. Eventually, I just rebooted the machine. I found a problem in the BIOS, that said the voltage for the 3.3V was fluctuating between 3V and 5V, so I replaced the power supply on the box. Maybe this will fix. Do you think it is related to the problem of the commands freezing...(btw, I tried doing a netstat, lsof -i, and a couple others that also froze. Doing an nmap, didn't freeze, however).

---

### Post by nanotube on 2006-05-30
[QUOTE=deejross]Well, I might have solved all the problems, but I will won't find out for a few days (until is breaks again). I tried both commands when the IM server crashed. Linux froze at the command line when trying either command. I let it sit for 10 minutes, and nothing. Eventually, I just rebooted the machine. I found a problem in the BIOS, that said the voltage for the 3.3V was fluctuating between 3V and 5V, so I replaced the power supply on the box. Maybe this will fix. Do you think it is related to the problem of the commands freezing...(btw, I tried doing a netstat, lsof -i, and a couple others that also froze. Doing an nmap, didn't freeze, however).[/QUOTE]
hmm, well, the psu change should fix the random freezing problems... i don't know why netstat or lsof would freeze though. they run really fast on my comp... but hey, you never know what the computer will do when the power supply is being flaky... so maybe. :)

---

### Post by deejross on 2006-05-30
Well, even though I don't know if it works yet, I'll go ahead and thank you guys anyways. If anything, you put me in the right direction....Thanks ;)

---

