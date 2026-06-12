---
title: "How to start Firestarter on login w/o entering password every time?"
date: 2006-02-13
forum: General Help
---

### Post by Red Knuckles on 2006-02-13
How do I get Firestarter to not ask for a password every time I login?

---

### Post by kaamos on 2006-02-13
It starts at boot if you have selected that in firestarters preferences. The gui does not start, but the firewall is running. The gui is needed only for looking at logs and changing settings.

Hope this helps.

---

### Post by gremlin hunter on 2006-02-13
Don't know if it what you wan't but you can disable all password requests.

Type in "*sudo visudo*"

My sudoers file looks like this:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) NOPASSWD: ALL
```

---

### Post by kaamos on 2006-02-13
I thinks thats a pretty unsafe thing to do..

---

### Post by sbassett on 2006-02-13
How about:

username ALL= NOPASSWD: /usr/bin/firestarter

This will let the specified user start firestarter ONLY without a password prompt.

---

### Post by SWAT on 2006-02-13
This is REALLY unsafe, I DO NOT recommend it!

---

### Post by Red Knuckles on 2006-02-13
I tried to change 'sudo visudo' so the last line reads:

%admin  ALL=(ALL) NOPASSWD: /usr/bin/firestarter

Now firestarter won't start at all and now when I execute 'sudo visudo' I get:

zzz@ubuntu:~$ sudo visudo
Sorry, user zzz is not allowed to execute '/usr/sbin/visudo' as root on localhost.localdomain.

User zzz is the administrative user on this computer. For what it's worth this is a 1 person box in a 1 person household. I can live with entering a password for firestarter but I need to undo what I've done to "sudo visudo'. Help please???

---

### Post by Red Knuckles on 2006-02-13
Oh, The error message for Firestarter on login or when I try to start Firestarter is:

Failed to run /usr/sbin/firestarter as user root:
 No password was supplied and sudo needs it. Please Help!!!

---

### Post by Red Knuckles on 2006-02-13
Oh boy, I've really screwed the pooch. I was going to try to run Synaptic and remove Firestarter and reinstall and got this error message:

Failed to run /usr/sbin/synaptic as user root:
 No password was supplied and sudo needs it.

I probably can't do anything as root till I get this fixed.

---

### Post by sbassett on 2006-02-13
[QUOTE=Red Knuckles]Oh boy, I've really screwed the pooch. I was going to try to run Synaptic and remove Firestarter and reinstall and got this error message:

Failed to run /usr/sbin/synaptic as user root:
 No password was supplied and sudo needs it.

I probably can't do anything as root till I get this fixed.[/QUOTE]

Ack, no that needed to be added at the end, not replacing what was there. Do you have the install cd, you should be able to correct this if you boot into rescue mode. 

And as stated above, this is not very secure.

---

### Post by byen on 2006-02-13
If you are trying to install firestarter-gui during startup without the sudo error...this is what you do
Step1:
System>Preferences>Sessions>Startup Programs>Add
Startup Command: sudo firestarter --start-hidden 
Order: 20
(Notes: this will add firestarter to your start-up)

Step2:
Open terminal and type:
sudo gedit /etc/sudoers (this will open a file)
Add this to the bottom of that page 
username ALL=NOPASSWD:/usr/sbin/firestarter
([COLOR="Blue"]insert your login user name in place of the username[/COLOR])
(This would tell the computer not to ask for a password for the user specified)
save

thats it.. it should work. Let me know if you have any problems.
Goodluck! Hope that helps.

---

### Post by Red Knuckles on 2006-02-13
[QUOTE=byen]If you are trying to install firestarter-gui during startup without the sudo error...this is what you do
Step1:
System>Preferences>Sessions>Startup Programs>Add
Startup Command: sudo firestarter --start-hidden
Order: 20
(Notes: this will add firestarter to your start-up)

Step2:
Open terminal and type:
sudo gedit /etc/sudoers (this will open a file)
Add this to the bottom of that page
username ALL=NOPASSWD:/usr/sbin/firestarter
([COLOR="Blue"]insert your login user name in place of the username[/COLOR])
(This would tell the computer not to ask for a password for the user specified)
save

thats it.. it should work. Let me know if you have any problems.
Goodluck! Hope that helps.[/QUOTE]

The current problem is that because of the change made to 'sudo visudo' I can't do anything as root or sudo. Until I learn how to correct that I'm really stuck here.

---

### Post by sbassett on 2006-02-13
Red -

Do you have access to your install cd? You should be able to boot from CD, and enter rescue at the prompt.

Also a live ubuntu CD should also do the the trick.

---

### Post by Red Knuckles on 2006-02-13
[QUOTE=sbassett]Ack, no that needed to be added at the end, not replacing what was there. Do you have the install cd, you should be able to correct this if you boot into rescue mode. 

And as stated above, this is not very secure.[/QUOTE]

I do have the rescue CD and can boot into rescue mode. It then gives a choice of "discs" 1 thru 4 and I don't know which to pick. Then I'll probably get a sh run level 3 and I don't know what to type.
At least not yet. I assume I'm trying to get to 'sudo visudo' in a location where I can change it and change it back to original settings. This means I have to learn how to login to 'username@ubuntu' in sh???

---

### Post by Red Knuckles on 2006-02-14
I was unable to resolve my login issue so I reinstalled Ubuntu. On first boot I did Ubuntu update then rebooted. I then installed Automatix and ran it selecting the packages/updates I wanted. Reboot again. All has gone well/normal so far no unexpected error messages. Here is a link that resolved for me the issue of how to start Firestarter on login without entering password. Thanks one and all for the help tips. I have learned a LOT the last 2 days!!!:) 

The link:

[http://www.ubuntuforums.org/showthread.php?t=129798&highlight=firestarter](http://www.ubuntuforums.org/showthread.php?t=129798&highlight=firestarter)

The only problem I have with firestarter now is that I need to open ports for Azureus. When I run >Firestarter>policy>Inbound Traffic Policy the 'Add' button is grayed out. Wonder what I'm doing wrong there???:confused:

---

### Post by Red Knuckles on 2006-02-14
[QUOTE=Red Knuckles]I was unable to resolve my login issue so I reinstalled Ubuntu. On first boot I did Ubuntu update then rebooted. I then installed Automatix and ran it selecting the packages/updates I wanted. Reboot again. All has gone well/normal so far no unexpected error messages. Here is a link that resolved for me the issue of how to start Firestarter on login without entering password. Thanks one and all for the help tips. I have learned a LOT the last 2 days!!!:) 

The link:

[http://www.ubuntuforums.org/showthread.php?t=129798&highlight=firestarter](http://www.ubuntuforums.org/showthread.php?t=129798&highlight=firestarter)

The only problem I have with firestarter now is that I need to open ports for Azureus. When I run >Firestarter>policy>Inbound Traffic Policy the 'Add' button is grayed out. Wonder what I'm doing wrong there???:confused:[/QUOTE]


Duh, Red Knuckles you blithering idiot. Go to >Firestarter>policy>Inbound Traffic Policy and right click anywhere in the allow service area and add ports till your hands fall off!!!\\:D/

---

### Post by spookygeek on 2006-02-19
I followed the steps above and got everything working fine.  Sure its nice not to have to type the password in everytime on startup.  Makes it "wife-proof" too.

Thanks,

-Brent

---

