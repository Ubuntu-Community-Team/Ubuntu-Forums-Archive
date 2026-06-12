---
title: "Firestarter to run when starting Ubuntu"
date: 2009-09-14
forum: General Help
---

### Post by sopadeajo on 2009-09-14
I have installed what seems to be an excellent firewall (still learning to use it): Firestarter.
It shows me , at this moment a bunch of attacks against Dcom (port 135). I do not know if the firewall protection is sufficient or if i should do something more.

I want Firestarter to be running every time I start Ubuntu.
Using chkconfig i see : firestarter S
What should be changed to chkconfig and how?

---

### Post by NoaHall on 2009-09-14
How do you know that it's being attacked? It's probably not.

The firewall always starts up anyway, but the gui doesn't.

---

### Post by sopadeajo on 2009-09-14
If it&#347; not an attack then it&#347; people playing with insistance on port 135 and i do not have enough knoweledge to protect myself further than does the firewall.I do not know if hiding behind a proxy would be a solution.
I want the gui and the firewall to start when Ubuntu starts.How to do it?

---

### Post by NoaHall on 2009-09-14
It's probably a program/website. It's very unlikely to be attack. The firewall always starts up.

---

### Post by sopadeajo on 2009-09-14
25 (marked as serious) attempts on port 135 and 1 on port 22 (SSH) from 15 or 17 different IP adresses. Doesn't seem to be a website alone..

---

### Post by sopadeajo on 2009-09-14
I found this on Firestarter help files:

Open up your GNOME menu, select *Preferences* followed by *Sessions*. Switch to the *Startup programs* tab, pictured right. 
  Click *Add* and enter
[FONT=georgia]sudo firestarter --start-hidden[/FONT]
as the startup command. Click *OK* and you're done. 
  To stop Firestarter from loading on login, simply remove its entry from the startup programs listing. 



But i do not find the gnome menu.
Any help to find it?

---

### Post by CoolHand on 2009-09-14
> **sopadeajo said:**
> I found this on Firestarter help files:

Open up your GNOME menu, select *Preferences* followed by *Sessions*. Switch to the *Startup programs* tab, pictured right. 
  Click *Add* and enter
[FONT=georgia]sudo firestarter --start-hidden[/FONT]
as the startup command. Click *OK* and you're done. 
  To stop Firestarter from loading on login, simply remove its entry from the startup programs listing. 



But i do not find the gnome menu.
Any help to find it?

I do this on my PC.  I like to see it running so I can catch the access attempts.  There is a little more to it though.  If you just add the sudo command it still wants a password to open.  Here is everything I do to get it to start auto:

First edit your sudoers file with command:  "sudo visudo"
(I suggest not opening everything but allow just the command you want with no pass - Add the following in the noted locations)
# Cmnd alias specification
Cmnd_Alias      SAFE=/usr/sbin/firestarter

(Last line add)
yourusername  ALL= NOPASSWD: SAFE

I have a simple script that I call multiple startup commands from so I can add a delay to some.  The firewall is one of them.  If you try to start it before you have a net connection it fails.  It's not entirely safe to wait either but technically it is already running.  The applet is just a monitoring and config tool.  I call my script from the -Preferences-Startup Applications menu.  I just added a pointer to it from there and done.  The script portion for the firewall looks like this:

```
#!/bin/sh
#
# Startup script for Ubuntu
# This way I can control better the timing 
# and behavior of auto started applications

# Detect network interface and adjust
# firewall and desktop monitor
#ifconfig eth0 | grep -q "inet addr"
#if [ $? = 0 ]
#then
#    sudo sed -i 's/eth1/\eth0/' /etc/firestarter/configuration
#else
#    sudo sed -i 's/eth0/\eth1/' /etc/firestarter/configuration
#fi
# Start the firewall applet after a delay
# to allow for network association
sleep 15
/usr/bin/xhost + local:root
/usr/bin/sudo /usr/sbin/firestarter --start-hidden &

```

I left in there a commented out bit that I used to use on my laptop to auto reconfigure the firewall for the switch to my wifi interface.  Haven't used that with the new version so it might need tweeking.

Forgot to mention, if you try to use that sed clip in the script you will also need to add sed to your sudoers file as a safe app.  Just add a ", /bin/sed" to that command alias list.

---

### Post by sopadeajo on 2009-09-14
Thant you CoolHand, but i am too new to Linux to fully understand all you said.I'll wait until i learn more.


I googled for DCOM-scm hits on port 135 and found this:

"DCOM-scm is the DCOM interface to the Service Control Manager, which
allows for the starting, stopping, etc. of the background services on a
Windows system.  Unfortunately, Microsoft didn't get the security quite
right in this subsystem.

This is an attempt by a compromised Windows box to compromise your Linux
system by scanning the local blueyonder IP address range, hoping it will
find another open Windows system."

I was aware that this could be a windows machine or a windows-Zombie machine 
(Zombie:the user of this machine does not know what his machine is doing)
 trying to infect a windows system. We are Linux and are safer, but i do not
 feel too well knowing that a zombie machine is trying to get to you (a non Zombie machine would be
 worse, since the attacker would be a human and probably know very fast this 
is Linux and do smarter hacks).
I am sill getting  attempts on port 135 from distinct IP adresses (20 different IP's)
 (70 considered as serious by the firewall in 3 hours).


But it could be as well that all these scans are part of a normal process between windows networked machines; but then i do not understand why they scan port 135 of people who do not belong to their network...

---

### Post by Paqman on 2009-09-14
Since Firestarter runs as root you're actually slightly *less* secure when it's running than when it isn't. The more code is running as root, the more chance there is for a breach of security. That's especially true in the case of a package like Firestarter which isn't being actively maintained.

---

### Post by CoolHand on 2009-09-14
Fair statement Paqman and I should have noted that.  I have looked at ufw and the gui frontend for it but like the original poster I do see value in seeing the alerts as they happen and Firestarter will show you.  The disigners of ufw are so adamant that you don't need to see it on your desktop that I abandoned it as I could find no way to start it without it annoying me with some sort of nonsense.  They need to realize that there is value in having a way to monitor the FW in real time on the desktop.  I'm a network engineer.  I have my reasons.  Does it need to be there...no.  Do many users like to have it...yes.  I would go with it as it is maintained but Firestarter doesn't try to tell me off for wanting to configure it my way.  It would be nice if you could monitor it non-root.

sopadeajo, good luck.  It really is easier than it sounds.  If you want me to walk you through it better just ask I can give step by step details.

---

### Post by sopadeajo on 2009-09-14
If you have time enough, yes, CoolHand.

---

### Post by kitchenguy on 2009-09-18
> **sopadeajo said:**
> I have installed what seems to be an excellent firewall (still learning to use it): Firestarter.
It shows me , at this moment a bunch of attacks against Dcom (port 135). I do not know if the firewall protection is sufficient or if i should do something more.

I want Firestarter to be running every time I start Ubuntu.
Using chkconfig i see : firestarter S
What should be changed to chkconfig and how?

I recently had the some questions about whether it was running or not and there is a lot of people asking the same question on the net..
Once you have installed and configured Firestarter it is always running in the background even though it does not show up as active in System-->Administration-->System Monitor

To test:

1.Configure firestarter to be restrictive by default - that is, Whitelist what you want it to allow

2.Don't let it allow anything - that is add no rules to the whitelist

3.Reboot

4.Try and browse - you will see nothing and get a page load error

Next,now that you know it is running: set up some logical rules so it will allow stuff through, same as you do for Guardog in KDE.  Note you even need to allow POP etc for email as well.  A good link is:
[http://www.linuxforums.org/articles/locking-down-ubuntu_256.html](http://www.linuxforums.org/articles/locking-down-ubuntu_256.html)

---

