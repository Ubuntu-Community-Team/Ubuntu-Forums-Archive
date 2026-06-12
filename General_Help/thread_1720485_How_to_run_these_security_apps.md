---
title: "How to run these security apps?"
date: 2011-04-03
forum: General Help
---

### Post by PCaddicted on 2011-04-03
Hello,
Due to being a little paranoid,I've installed rkhunter and chkrootkit on my Ubuntu 10.10 system.My question is:how to run these applications(I don't see them anywhere)?Shall I use the Terminal?

---

### Post by Frogs Hair on 2011-04-03
Both of the applications appear to run in the terminal . Try typing the application name in the terminal and press enter . I don't know if these applications require sudo or a password to use them.

---

### Post by PCaddicted on 2011-04-03
Does chkrootkit need updating?

---

### Post by bodhi.zazen on 2011-04-03
Linux is not windows and you almost certainly do not need those tools. Linux security is not about running antivirus tools and rootkit detection.

In addition both those tools are rather sophisticated and require you to understand your system and do additional reading on the output, most of which is false positives.

See : [http://ubuntuforums.org/showthread.php?t=1477662](http://ubuntuforums.org/showthread.php?t=1477662)

I highly suggest you read the security sticky

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by conradin on 2011-04-03
Latest version, 0.49,
released in 2009, 
```

chkrootkit -V

```

---

### Post by PCaddicted on 2011-04-03
These apps can remove threats if they find them,can't they?

---

### Post by cjsteele on 2011-04-03
> **PCaddicted said:**
> Hello,
Due to being a little paranoid,I've installed rkhunter and chkrootkit on my Ubuntu 10.10 system.My question is:how to run these applications(I don't see them anywhere)?Shall I use the Terminal?


Typically, no, but you'd be able to delete them manually.

One note: Linux does support "immutability", and an intelligent rootkit will protect itself using immutability, making it impossible for you to delete its files.  That said, if you don't disable immutability in advance, you won't be able to remove the files, even after a reboot.  If you do find yourself fighting an immutable file, you'll need help.

-C

---

### Post by d3v1150m471c on 2011-04-03
```

sudo chattr -i immutable_file_name && rm -f immutable_file_name

```

---

### Post by PCaddicted on 2011-04-03
How can I disable immutability in Ubuntu 10.10?

---

### Post by cjsteele on 2011-04-03
> **d3v1150m471c said:**
> ```

sudo chattr -i immutable_file_name && rm -f immutable_file_name

```

Yes, but some root kits disable the ability to remove the immutability.   I would have to look at my notes for the specific command, but when its used, simply foreseeing clearing the immutability bit doesn't work, and you can't do anything about it until you reboot... and if the root kit is worth a crap, it will re-enable that desire feature first thing at boot.  In my experience, the only means of recovering is to boot to safe media and disable the root kit there, and then reboot back to the compromised system to finish the cleanup effort.

I've done a lot of work with compromised systems, and have researched a lot of root kits.   Take my word for it, the first time you run up against something like this, you'll bang your head for a long time, and even contemplate a fresh install... then you'll remember this thread... and hopefully, you'll be thankful.

C

---

### Post by cjsteele on 2011-04-03
Another tool you should look at is trip wire.  That is a fortuitous marvel.   When properly configured, you can get a high degree of confidence that your system has not been compromised, and if it has been, it will typically tell you a lot about what was changed.  Lkm kits notwithstanding. 

C

---

### Post by PCaddicted on 2011-04-04
The command doesn't work on my PC,not even if I use the sudo su command in order to get root access and then type the command you gave to me.It says "No such file or directory".Do you suppose I have a rootkit?I've run a scan with rkhunter and the program displayed 2 warnings.In order to see what are they about,I have to view the log file.But I can't open this file,nor make it executable(the latter option is greyed out in the Properties window,at the Permissions tab,because "I was not the owner").If I try to open the log file,I will get "Permission denied",even If I use the Terminal with root access.Do I have to replace file_name with anything else?
I am very worried.I am gonna install a new GUI for IPtables in order to configure the firewall rules(I mean,set which apps can connect to the internet and which of them can't) thus preventing a rootkit(if I have such a thing) from sending my personal data to an attacker.Which GUI do you recommend?
And one more question:do Linux Ubuntu 10.10 users really have to concern about rootkits?

---

### Post by bodhi.zazen on 2011-04-04
Well, if you ask me, I think you are wasting your time.

Linux is not windows and linux security is not about running antivirus or rootkit detection or even a firewall.

Read the security sticky. Learn to read the logs (/var/log), they are critical to security.

From there, is you are not satisfied, learn to use apparmor.

Learn what ports are open (by default there are no significant open ports) and how to identify open ports ( sudo lsof -i -P -n is but one of many  commands).

I think there are much better tools the the ones mentioned in this thread. OpenVAS (still in development), Snort, and OSSEC would be where I would direct you.

The problem with rkhunter, chkrootkit, and tripwire is that they are not really new user friendly and will take you some time to learn. Although these tools are in the Ubuntu repositories, they are very generic and not really tailored to Ubuntu (thus resulting in false positives).

The other problems are :

1. Rootkits are rare, and honestly I have not seen one detected by rkhunter or chkrootkit ever. Intrusions are almost always detected by people observing unexpected behavior on their systems and checking various logs or with the assistance of a seasoned veteran "white hat".

2. Rootkits are complicated. Detecting, identifying, and removing a rootkit is a battle of skills, yours vs the intruder. Now it is true some intruders are sloppy, others are not. If you are new to linux you will likely be on the loosing end, and thus it is best (IMHO) to identify how you were compromised (weak passwords, VNC or other server, social engineering, etc), backing up your data, and performing a fresh install.

If you want to learn penetration testing or forensics analysis, you have a lot of reading ahead of you (sorry about that).

Here is some introductory information:

[http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-1](http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-1)

[http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-2](http://www.symantec.com/connect/articles/forensic-analysis-live-linux-system-pt-2)

[http://staff.washington.edu/dittrich/talks/blackhat/blackhat/forensics.html](http://staff.washington.edu/dittrich/talks/blackhat/blackhat/forensics.html)

Keep in mind, security starts with an understanding of what is "normal" for your system.

The vast majority of problems Linux users face is not viruses or rootkits, it is, in order of most frequent:

1. Weak passwords.

2. Physical access (family members, (ex) spouses, and roommates are most common).

3. Disabling security features. How many threads do you see where people want to disable a password for this or that ?

4. VNC. "Desktop sharing" is familiar to window users, but the VNC protocol is very insecure. Use ssh or FreeNX instead.

5. Social engineering.

6. Phishing.

7. Browser exploits (use noscript).

8. FTP with weak passwords.

9. SSH with a weak password.

10. Buffer overflows (these are very rare, I have seen more buffer over flow attempts the successful exploits).

Edit: I forgot to add physical access, thus changed the numbers.

Every "crack" I have seen over many years on these forums falls under one of those [s]9[/s] 10 with # 1-9 taking the lions share by far. #10 is solved, for the most part, not with rootkit detection by rather by **keeping your system up to date**. If you wish, use apparmor or learn to use grsecurity (which requires you to patch your kernel).

The "problem" I have with threads such as this one is that new users, often coming from windows, spin their wheels, running firewalls, antivirus, and worry about rootkits and and never taught "proper" Linux security. This problem is further magnified by the "Alerts", "Warnings" and false positives thrown by these tools onto users who have no idea how to interpret the output or what the "normal" output of these tools is on a fresh install and updated Ubuntu system.

Another problem you will have is that every now and then someone with years of experience chimes in on one of these threads. Yes, as with everything else, if you have years of experience in penetration testing and forensics these tools are "easy to use". Keep your own experience and limitations in mind when deciding to start down the path of penetration testing / forensics.

But if you are new to Linux, you are lacking this experience and will need to decide if you want to learn these "dark arts".

---

