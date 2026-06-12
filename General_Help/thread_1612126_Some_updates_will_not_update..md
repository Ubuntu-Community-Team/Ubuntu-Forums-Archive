---
title: "Some updates will not update."
date: 2010-11-02
forum: General Help
---

### Post by Th3Professor on 2010-11-02
When I try to update the computer, like with the automatic updates, every time after it's done I get an error message stating that a number of the updates were unable to actually update:

"Errors were encountered while processing:
postfix
bsd-mailx
lsb-core
mailx
lsb-graphics
lsb
lsb-cxx
lsb-desktop"

What can I do to get those updates to actually update?

---

### Post by sanderd17 on 2010-11-02
can you run

```

sudo aptitude update

```

if there are errors, show them, if not, run

```

sudo aptitude upgrade

```

if you see errors here, show them.

---

### Post by Th3Professor on 2010-11-02
Is it a bad idea to upgrade without first backing things up? I have 3 terabytes of data that I need to sort through to select important data to back-up before I can make an actual upgrade. I'm running "9.10". I know it needs an upgrade, though really, this was a problem, at least on my computer, even when that version came out.

Edit - here is the output from the update -

```
Writing extended state information... Done
Hit http://security.ubuntu.com karmic-security Release.gpg
Ign http://security.ubuntu.com karmic-security/main Translation-en_US           
Hit http://us.archive.ubuntu.com karmic Release.gpg                             
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                  
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US            
Hit http://packages.medibuntu.org karmic Release.gpg                            
Ign http://packages.medibuntu.org karmic/free Translation-en_US                 
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US             
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US     
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US       
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US     
Hit http://security.ubuntu.com karmic-security Release                          
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US              
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US            
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg                     
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com karmic Release                                 
Hit http://packages.medibuntu.org karmic Release                                
Hit http://us.archive.ubuntu.com karmic-updates Release                         
Hit http://security.ubuntu.com karmic-security/main Packages                    
Hit http://packages.medibuntu.org karmic/free Packages                          
Hit http://us.archive.ubuntu.com karmic/main Packages                           
Hit http://us.archive.ubuntu.com karmic/restricted Packages                     
Hit http://us.archive.ubuntu.com karmic/main Sources                            
Hit http://us.archive.ubuntu.com karmic/restricted Sources                      
Hit http://us.archive.ubuntu.com karmic/universe Packages                       
Hit http://us.archive.ubuntu.com karmic/universe Sources                        
Hit http://us.archive.ubuntu.com karmic/multiverse Packages                     
Hit http://security.ubuntu.com karmic-security/restricted Packages              
Hit http://security.ubuntu.com karmic-security/main Sources                     
Hit http://security.ubuntu.com karmic-security/restricted Sources               
Hit http://security.ubuntu.com karmic-security/universe Packages                
Hit http://security.ubuntu.com karmic-security/universe Sources                 
Hit http://packages.medibuntu.org karmic/non-free Packages                      
Hit http://us.archive.ubuntu.com karmic/multiverse Sources                      
Hit http://us.archive.ubuntu.com karmic-updates/main Packages                   
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages             
Hit http://us.archive.ubuntu.com karmic-updates/main Sources                    
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources              
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages               
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources                
Hit http://security.ubuntu.com karmic-security/multiverse Packages              
Hit http://security.ubuntu.com karmic-security/multiverse Sources               
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages             
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources              
Get:1 http://dl.google.com stable Release.gpg [189B]                            
Ign http://dl.google.com stable/main Translation-en_US                         
Get:2 http://dl.google.com stable Release [2,544B]                         
Get:3 http://ppa.launchpad.net karmic Release.gpg [307B]
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Get:4 http://dl.google.com stable/main Packages [1,083B]
Get:5 http://ppa.launchpad.net karmic Release [66.0kB]
Ign http://ppa.launchpad.net karmic Release
Hit http://ppa.launchpad.net karmic/main Packages
Fetched 4,124B in 5s (722B/s)
Reading package lists... Done             
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A3018EFB7F931814

```

---

### Post by sanderd17 on 2010-11-02
> **Th3Professor said:**
> Is it a bad idea to upgrade without first backing things up? I have 3 terabytes of data that I need to sort through to select important data to back-up before I can make an actual upgrade. I'm running "9.10". I know it needs an upgrade, though really, this was a problem, at least on my computer, even when that version came out.

It's not a distribution upgrade, just an application upgrade. A way of doing the update manager.

---

### Post by Th3Professor on 2010-11-02
> **sanderd17 said:**
> It's not a distribution upgrade, just an application upgrade. A way of doing the update manager.

So, is it safe for me to use "sudo aptitude upgrade" without having to first create back-ups of important data?

(Just making sure I understand that.)

---

### Post by sanderd17 on 2010-11-02
> **Th3Professor said:**
> So, is it safe for me to use "sudo aptitude upgrade" without having to first create back-ups of important data?

(Just making sure I understand that.)

yep, it's 100% safe (well, not 100%: it can't stand fire, explosions ... :P ).

for your error, you have one repo that isn't authenticated.  Could you go to software center, to edit -> software sources, go to the other sources.

delete that source (do a aptitude update to be sure it's completely deleted) and add it again. Normally the adding should get the GPG key.

Then try again to run the commands from above.

---

### Post by sanderd17 on 2010-11-02
Oh, sorry, it seems that the aptitude upgrade command is deprecated in favor of 

```

sudo aptitude safe-upgrade

```

the old command still works (and will probably work forever) but the new command has a clearer name.

[I]
for **dist-upgrade**, the new command is

```

sudo aptitude full-upgrade

```
[/I]

---

### Post by sanderd17 on 2010-11-02
I'm going, if it doesn't help, I found a better (in terms of "less work") solution to your problem:

[http://ubuntuforums.org/showthread.php?t=1046158](http://ubuntuforums.org/showthread.php?t=1046158)


```


gpg --keyserver keyserver.ubuntu.com --recv 7f931814
gpg --export --armor 7f931814 | sudo apt-key add -


```

---

### Post by Th3Professor on 2010-11-02
> **sanderd17 said:**
> yep, it's 100% safe (well, not 100%: it can't stand fire, explosions ... :P ).

for your error, you have one repo that isn't authenticated.  Could you go to software center, to edit -> software sources, go to the other sources.

delete that source (do a aptitude update to be sure it's completely deleted) and add it again. Normally the adding should get the GPG key.

Then try again to run the commands from above.
Do you mean the synaptic package manager when you say software center? I didn't see a "software sources" within the "edit" menu. I checked other places in the synaptic package manager, found repositories, though wasn't sure where to go or what exactly to delete in them, it's kind of confusing.

> **sanderd17 said:**
> Oh, sorry, it seems that the aptitude upgrade command is deprecated in favor of 

```

sudo aptitude safe-upgrade

```

the old command still works (and will probably work forever) but the new command has a clearer name.

[I]
for **dist-upgrade**, the new command is

```

sudo aptitude full-upgrade

```
[/I]
Okay, that's actually the list of messages (from running "safe-upgrade") that I was looking for before when I ran the system's GUI-based Update application. Here's the output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  libjline-java{u} rhino{u} seamonkey-gnome-support{u} 
The following partially installed packages will be configured:
  bsd-mailx lsb lsb-core lsb-cxx lsb-desktop lsb-graphics mailx postfix 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 1,098kB will be freed.
Do you want to continue? [Y/n/?] {I selected Yes}
(Reading database ... 313381 files and directories currently installed.)
Removing rhino ...
Removing libjline-java ...
Removing seamonkey-gnome-support ...
Processing triggers for man-db ...
Setting up postfix (2.6.5-3) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: warning: valid_hostname: misplaced delimiter: {omitted}.
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: {omitted}.
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 75
dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing bsd-mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mailx:
 mailx depends on bsd-mailx; however:
  Package bsd-mailx is not configured yet.
dpkg: error processing mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-core:
 lsb-core depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
 lsb-core depends on mailx | mailutils; however:
  Package mailx is not configured yet.
  Package bsd-maNo apport report written because the error message indicates its a followup error from a previous failure.
                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                    No apport report written because MaxReports is reached already
                                                  No apport report written because MaxReports is reached already
                                No apport report written because MaxReports is reached already
              No apport report written because MaxReports is reached already
                                                                            No apport report written because MaxReports is reached already
                                                          ilx which provides mailx is not configured yet.
  Package mailutils is not installed.
dpkg: error processing lsb-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-graphics:
 lsb-graphics depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-graphics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-cxx:
 lsb-cxx depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-cxx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-desktop:
 lsb-desktop depends on lsb-graphics; however:
  Package lsb-graphics is not configured yet.
dpkg: error processing lsb-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb:
 lsb depends on lsb-core; however:
  Package lsb-core is not configured yet.
 lsb depends on lsb-graphics; however:
  Package lsb-graphics is not configured yet.
 lsb depends on lsb-cxx; however:
  Package lsb-cxx is not configured yet.
 lsb depends on lsb-desktop; however:
  Package lsb-desktop is not configured yet.
dpkg: error processing lsb (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
 bsd-mailx
 mailx
 lsb-core
 lsb-graphics
 lsb-cxx
 lsb-desktop
 lsb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up postfix (2.6.5-3) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: warning: valid_hostname: misplaced delimiter: {omitted}.
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: {omitted}.
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 75
dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing bsd-mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-core:
 lsb-core depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing lsb-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mailx:
 mailx depends on bsd-mailx; however:
  Package bsd-mailx is not configured yet.
dpkg: error processing mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-graphics:
 lsb-graphics depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-graphics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb:
 lsb depends on lsb-core; however:
  Package lsb-core is not configured yet.
 lsb depends on lsb-graphics; however:
  Package lsb-graphics is not configured yet.
dpkg: error processing lsb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-cxx:
 lsb-cxx depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-cxx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-desktop:
 lsb-desktop depends on lsb-graphics; however:
  Package lsb-graphics is not configured yet.
dpkg: error processing lsb-desktop (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
 bsd-mailx
 lsb-core
 mailx
 lsb-graphics
 lsb
 lsb-cxx
 lsb-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
```


> **sanderd17 said:**
> I'm going, if it doesn't help, I found a better (in terms of "less work") solution to your problem:

[http://ubuntuforums.org/showthread.php?t=1046158](http://ubuntuforums.org/showthread.php?t=1046158)


```


gpg --keyserver keyserver.ubuntu.com --recv 7f931814
gpg --export --armor 7f931814 | sudo apt-key add -


```
Okay, I ran those two commands. Here's the output...

Output from the keyserver/receive command:
```
gpg --keyserver keyserver.ubuntu.com --recv 7f931814
gpg: requesting key 7F931814 from hkp server keyserver.ubuntu.com
gpg: key 7F931814: public key "Launchpad PPA for Andrea Piccinelli" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
```

The output from the export/add command was simply:
```
OK
```

I ran another "update" and the GPG error message is now gone.

I ran another "safe-upgrade" and it appears to have the same errors as I copied/pasted in the safe-upgrade output above. At a glance, however, this time it did not include "Writing extended state information... Done" at the end. Though, the other errors are still there. :(

These specific things seem to not want to update:
postfix
bsd-mailx
mailx
lsb-core
lsb-graphics
lsb-cxx
lsb-desktop
lsb

---

### Post by sanderd17 on 2010-11-03
can you post the output of 

```

sudo aptitude update

```

again? so I can see if all repo's are still there.

---

### Post by Th3Professor on 2010-11-03
update output-
```
Get:1 http://dl.google.com stable Release.gpg [189B]
Hit http://ppa.launchpad.net karmic Release.gpg                                 
Ign http://ppa.launchpad.net karmic/main Translation-en_US                      
Hit http://us.archive.ubuntu.com karmic Release.gpg                             
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                  
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US            
Hit http://security.ubuntu.com karmic-security Release.gpg                      
Ign http://security.ubuntu.com karmic-security/main Translation-en_US           
Hit http://packages.medibuntu.org karmic Release.gpg                            
Ign http://packages.medibuntu.org karmic/free Translation-en_US                 
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US             
Ign http://dl.google.com stable/main Translation-en_US                          
Hit http://ppa.launchpad.net karmic Release                                     
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US              
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US            
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg                     
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com karmic Release                                 
Get:2 http://dl.google.com stable Release [2,544B]                              
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US     
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US       
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US     
Hit http://security.ubuntu.com karmic-security Release                          
Hit http://packages.medibuntu.org karmic Release                                
Hit http://us.archive.ubuntu.com karmic-updates Release                         
Get:3 http://dl.google.com stable/main Packages [1,079B]                        
Hit http://ppa.launchpad.net karmic/main Packages                               
Hit http://security.ubuntu.com karmic-security/main Packages                    
Hit http://us.archive.ubuntu.com karmic/main Packages                
Hit http://us.archive.ubuntu.com karmic/restricted Packages          
Hit http://us.archive.ubuntu.com karmic/main Sources                 
Hit http://us.archive.ubuntu.com karmic/restricted Sources           
Hit http://us.archive.ubuntu.com karmic/universe Packages            
Hit http://us.archive.ubuntu.com karmic/universe Sources             
Hit http://us.archive.ubuntu.com karmic/multiverse Packages          
Hit http://packages.medibuntu.org karmic/free Packages               
Hit http://security.ubuntu.com karmic-security/restricted Packages   
Hit http://security.ubuntu.com karmic-security/main Sources
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Packages     
Hit http://us.archive.ubuntu.com karmic/multiverse Sources           
Hit http://us.archive.ubuntu.com karmic-updates/main Packages        
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages  
Hit http://us.archive.ubuntu.com karmic-updates/main Sources         
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources   
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages    
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources     
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages  
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources   
Hit http://packages.medibuntu.org karmic/non-free Packages           
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Fetched 3,812B in 0s (4,193B/s)
Reading package lists... Done

```

---

### Post by sanderd17 on 2010-11-03
your sources list is OK, so the problem is with the installation itself.

can you try

```

sudo aptitude reinstall postfix

```

If that gives the same error, try

```

sudo aptitude remove postfix
sudo aptitude install postfix bsd-mailx mailx lsb-core lsb-graphics lsb-cxx lsb-desktop lsb

```

If that still doesn't work, do the following: 

**Warning: this will remove your postfix settings (mail server)**
```

sudo aptitude pruge postfix
sudo aptitude install postfix bsd-mailx mailx lsb-core lsb-graphics lsb-cxx lsb-desktop lsb

```

---

### Post by Th3Professor on 2010-11-03
> **sanderd17 said:**
> your sources list is OK, so the problem is with the installation itself.

can you try

```

sudo aptitude reinstall postfix

```
Same error.

> 
If that gives the same error, try

```

sudo aptitude remove postfix
sudo aptitude install postfix bsd-mailx mailx lsb-core lsb-graphics lsb-cxx lsb-desktop lsb

```
I received this on the remove command, part way through:
```
The following actions will resolve these dependencies:

Install the following packages:
nbsmtp [1.00-4 (karmic)]

Score is 41

Accept this solution? [Y/n/q/?] 

```
and:
```
The following NEW packages will be installed:
  nbsmtp{a} 
The following packages will be REMOVED:
  postfix 
The following partially installed packages will be configured:
  bsd-mailx lsb lsb-core lsb-cxx lsb-desktop lsb-graphics mailx 
0 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 32.4kB of archives. After unpacking 3,412kB will be freed.
Do you want to continue? [Y/n/?] 

```
I selected "Yes" on both.

After installing the string of things it now comes up with only one error:

```
Errors were encountered while processing:
 postfix

```

> If that still doesn't work, do the following: 

**Warning: this will remove your postfix settings (mail server)**
```

sudo aptitude pruge postfix
sudo aptitude install postfix bsd-mailx mailx lsb-core lsb-graphics lsb-cxx lsb-desktop lsb

```
Since I still had the postfix error I went ahead and did the purge and install. It popped up a set-up window, so I just went with default stuff like "Internet email" instead of "no configuration"/"local"/etc.

Anyway, so I did all of that and there is still an error on the "postfix". Here's the output after a safe-upgrade:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following partially installed packages will be configured:
  postfix 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up postfix (2.6.5-3) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: warning: valid_hostname: misplaced delimiter: {omitting this address}.
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: {omitted}.
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 75
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up postfix (2.6.5-3) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: warning: valid_hostname: misplaced delimiter: {I'm omitting this address from this output copy}.
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: {omitted}.
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 75
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```

---

### Post by sanderd17 on 2010-11-03
why did you install postfix if you don't use the mail server? If you don't use it, you can just purge or remove it without reïnstalling. I think the problem is the fact that you don't give right configuration options.

---

### Post by Th3Professor on 2010-11-04
Does postfix depend on mailserver? I'm not sure what's wrong with mailserver, I just set it to default settings. What's the connection there?

---

### Post by sanderd17 on 2010-11-06
postfix is a sendmail alternative:

```

aptitude show postfix

```

it's not in the default installation, if you don't need it, you can just delete it.

---

### Post by Th3Professor on 2010-11-09
postfix came default w/ this install. Getting rid of it won't solve the question of why it's not working. I'd like to keep using it.

---

### Post by Th3Professor on 2010-11-10
Any input from anybody on a postfix fix?

---

