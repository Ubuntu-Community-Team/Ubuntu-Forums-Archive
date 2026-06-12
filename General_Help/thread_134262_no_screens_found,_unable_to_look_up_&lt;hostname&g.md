---
title: "no screens found, unable to look up &lt;hostname&gt; via gethostbyname(), lotsa problems"
date: 2006-02-21
forum: General Help
---

### Post by Chimona on 2006-02-21
here's my specs:
athlon 64 3000+ venice
asus A8N-SLI 
ATI radeon x800 pro


I basically have two problems: I can't get into ubuntu 64 bit, and I can't get back into windows xp.

When I installed Ubuntu, I put it on the C: drive (someone told me it wouldn't be a problem). but it, of course deleted the ntldr and ntdetect.com files for windows to boot. Windows doesn't show up as an option in GRUB (although i don't know if it should). So i can't figure out how to get to it. 

Ubuntu has a few errors going on. I can't load x server i get this error:

(EE) No devices detected.

Fatal server error:
no screens found, 

i also can't execute sudo commands when i'm logged in I get this error:

unable to look up <hostname> via gethostbyname()

 so i can't do anything unless i'm in recovery mode. 

When i boot into recovery mode i get a fail at "Error : Temporary failure in name resolution" 
When i reboot i get an error that says "Stopping Deferred Execution Scheduler"

but eventually i get the prompt root@ubuntu:~#, and i can execute commands without sudo.

Also, even when I'm in recovery mode i can't get to the log file for x server "/var/log/xorg.0.log" it says access denied.

I ran dpkg-reconfigure xserver-xorg, and picked the vesa driver. Then did /etc/init.d/gdm restart, the screen just went to black. then when i hit the reboot button, it ran all the scripts then just went to a screen with a little white thing at the top left of the screen, like the underline of a single character. 

i also just tried startx after configuring and it just goes straight to black.

I hope i was specific enough, please help!:confused:

---

### Post by dcstar on 2006-02-21
[QUOTE=Chimona]
......
unable to look up <hostname> via gethostbyname()
......[/quote]
When you do get a login via Recovery mode, type:

mv /etc/hosts /etc/hosts.org

Save the following as a new /etc/hosts file and see if it fixes that problem:

```
127.0.0.1 localhost.localdomain localhost

# The following lines are desirable for IPv6 capable hosts
# (added automatically by netbase upgrade)

::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
Also, do:

chmod 644 /etc/hosts

after you save the file.

---

### Post by Chimona on 2006-02-21
I don't know how to:

 "Save the following as a new /etc/hosts file and see if it fixes that problem:"

and when i type in "mv /etc/hosts /etc/hosts.org" it just gives me a new prompt line, no errors or confirmations or anything

---

### Post by RAOF on 2006-02-21
[QUOTE=Chimona]I don't know how to:

 "Save the following as a new /etc/hosts file and see if it fixes that problem:"

and when i type in "mv /etc/hosts /etc/hosts.org" it just gives me a new prompt line, no errors or confirmations or anything[/QUOTE]
mv will (by default) not give any indication that it's finished.  But it has.

You can run "nano" from the recovery console, so you'd go:
```
nano /etc/hosts
```
then enter those lines.  Save it by pressing Ctrl-O, quit by pressing Ctrl-X

---

