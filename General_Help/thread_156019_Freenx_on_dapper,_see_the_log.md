---
title: "Freenx on dapper, see the log"
date: 2006-04-06
forum: General Help
---

### Post by manatlan on 2006-04-06
I've got an ubuntu dapper up-to-date, with freenx (frome seveas breezy respository) on my home machine

From work, on winXP, i've got the latest nomachine client, which is tunelled via shh on my home. But it don't want to connect to my home ;-( (it was working on breezy)

here is the log :
```
NX> 203 NXSSH running with pid: 2936
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 127.0.0.1 on port: 443
ssh_exchange_identification: Connection closed by remote host
```

and here is the nx client log :
```
ddxProcessArgument - Initializing default screens
winInitializeDefaultScreens - w 1280 h 1024
winInitializeDefaultScreens - Returning
ddxProcessArgument - screen - Found ``WxD'' arg
_XSERVTransmkdir: Owner of /tmp/.X11-unix should be set to root
(EE) Unable to locate/open config file
InitOutput - Error reading config file
winDetectSupportedEngines - Windows NT/2000/XP
winDetectSupportedEngines - DirectDraw installed
winDetectSupportedEngines - Allowing PrimaryDD
winDetectSupportedEngines - DirectDraw4 installed
winDetectSupportedEngines - Returning, supported engines 0000001f
InitOutput - g_iNumScreens: 1 iMaxConsecutiveScreen: 1
winSetEngine - Using Shadow DirectDraw NonLocking
winAdjustVideoModeShadowDDNL - Using Windows display depth of 32 bits per pixel
winCreateBoundingWindowWindowed - User w: 1162 h: 1024
winCreateBoundingWindowWindowed - Current w: 1162 h: 1024
winAdjustForAutoHide - Original WorkArea: 0 0 1024 1162
winAdjustForAutoHide - Adjusted WorkArea: 0 0 1024 1162
winCreateBoundingWindowWindowed - WindowClient w 1156 h 999 r 1156 l 0 b 999 t 0
winCreateBoundingWindowWindowed -  Returning
winCreatePrimarySurfaceShadowDDNL - Creating primary surface
winCreatePrimarySurfaceShadowDDNL - Created primary surface
winCreatePrimarySurfaceShadowDDNL - Attached clipper to primary surface
winAllocateFBShadowDDNL - lPitch: 4624
winAllocateFBShadowDDNL - Created shadow pitch: 4624
winAllocateFBShadowDDNL - Created shadow stride: 1156
winFinishScreenInitFB - Masks: 00ff0000 0000ff00 000000ff
winInitVisualsShadowDDNL - Masks 00ff0000 0000ff00 000000ff BPRGB 8 d 24 bpp 32
winCreateDefColormap - Deferring to fbCreateDefColormap ()
winFinishScreenInitFB starting winInitWM
winFinishScreenInitFB After winInitWM
color offset: 10 8 0
winFinishScreenInitFB - returning
winScreenInit - returning
InitOutput - Returning.
error opening security policy file /usr/X11R6/lib/X11/xserver/SecurityPolicy
(EE) No primary keyboard configured
(==) Using compiletime defaults for keyboard
names.keymap=(null)Rules = "xfree86" Model = "pc101" Layout = "us" Variant = "(null)" Options = "(null)"
Couldn't load XKB keymap, falling back to pre-XKB keymap
Could not init font path element /cygdrive/C/Program Perso/NX Client for Windows/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /cygdrive/C/Program Perso/NX Client for Windows/X11R6/lib/X11/fonts/Speedo, removing from list!
Could not init font path element /cygdrive/C/Program Perso/NX Client for Windows/X11R6/lib/X11/fonts/Type1, removing from list!
Could not init font path element /cygdrive/C/Program Perso/NX Client for Windows/X11R6/lib/X11/fonts/75dpi, removing from list!
Could not init font path element /cygdrive/C/Program Perso/NX Client for Windows/X11R6/lib/X11/fonts/100dpi, removing from list!
Could not init font path element /cygdrive/C/Program Perso/NX Client for Windows/usr/X11R6/lib/X11/fonts/TTF, removing from list!
Could not init font path element /cygdrive/C/Program Perso/NX Client for Windows/usr/X11R6/lib/X11/fonts/base, removing from list!
Could not init font path element /cygdrive/C/Program Perso/NX Client for Windows/usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /cygdrive/C/Program Perso/NX Client for Windows/usr/X11R6/lib/X11/fonts/Speedo, removing from list!
Could not init font path element /cygdrive/C/Program Perso/NX Client for Windows/usr/X11R6/lib/X11/fonts/Type1, removing from list!
Could not init font path element /cygdrive/C/Program Perso/NX Client for Windows/usr/X11R6/lib/X11/fonts/75dpi, removing from list!
Could not init font path element /cygdrive/C/Program Perso/NX Client for Windows/usr/X11R6/lib/X11/fonts/100dpi, removing from list!
winBlockHandler - Releasing pmServerStarted
winBlockHandler - pthread_mutex_unlock () returned
```

Why the connexion is closed by the host ?
[LIST]
[*]"(EE) Unable to locate/open config file" , but what config file ?
[*]"(EE) No primary keyboard configured", where to configure that ?
[*]"error opening security policy file /usr/X11R6/lib/X11/xserver/SecurityPolicy", can this block the access ?!
[*] or it's because it can't find font path on client ("Could not init font path element ....")
[/LIST]

freenx, ssh and nomachine client works well in local on my ubuntu box.
but why it doesn't work well from my work ?

---

### Post by Fisslefink on 2006-04-12
[SIZE="4"][B]Installing FreeNX server on Kubuntu Dapper Drake Flight 6
[/B][/SIZE]
I was having trouble getting NX to work on a clean installation of Kubuntu Dapper Drake Flight 6, so I fiddled with it for an hour, and now I have it working from inside Kubuntu.  I'm using the NX Client from nomachine.com, and when I access 127.0.0.1 with my normal username and password, it now authenticates fine, and I get a graphical interface.  But it wasn't easy.  

[COLOR="Red"]DISCLAIMER:  I have not yet tested this from a remote NX client, but I'm confident that will work.  If it does not, I'll be sure to edit this post with an addendum.[/COLOR]

[COLOR="Red"]UPDATE 4/13/06:  I just tested it from a computer across town (over the internet), and it works flawlessly.  I haven't tried to configure sound or SAMBA sharing yet, but that is not important to me, as I use sftp for file transfers, and sound is just sound.  Good luck with this HOWTO -- it does work.[/COLOR]

Here are the steps I took.

1) Add the following repository to /etc/apt/sources.list, or from inside Adept or Synaptic (current as of 4/12/2006 ... this repository tends to jump around, so Google it if you get errors.  The current seveas HowTo is incorrect!):

deb [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) breezy-seveas freenx

2) Install all of the packages with "nx" in the name.  Install the "ssh" package as well, if you haven't already.  If you do this in Adept, be sure to click Details so you can respond to the prompts.  I would highly recomend NOT using the default NX key!  You do not need the -dev packages.  I have installed:

freenx version 0.4.4+0.4.5-3ubuntu0
nxclient version 1.5.0-141
libxcomp1 version 1.4.92+1.5.0-4ubuntu0
libxcompext1 version 1.4.92+1.5.0-4ubuntu0
nxagent version 1.4.92+1.5.0-4ubuntu0
nxdesktop version 1.4.92+1.5.0-4ubuntu0
nxlibs version 1.4.92+1.5.0-4ubuntu0
nxproxy version 1.4.92+1.5.0-4ubuntu0
nxviewer version 1.4.92+1.5.0-4ubuntu0

3) If running 'nxclient' from the console does not work, download it from [www.nomachine.com](www.nomachine.com)

4) go to your /usr/lib/nx directory and make sure it contains the following:

nxagent
nxclient
nxdesktop (link -- I had to add this link!)
nxkeygen
nxloadconfig
nxnode
nxnode-login
nxpasswd
nxprint
nxproxy
nxserver (link)
nxsetup (link)
nxviewer

5) If anything is missing, search for it with "sudo find /|grep MISSINGFILE"

... if you find the binary, link to it with "sudo ln -s /path/to/binary /usr/lib/nx/."
(I had to do this with nxdesktop, which was in /usr/bin/nxdesktop)

... if you don't find the binary, try reinstalling that package using "sudo dpkg -i /var/cache/apt/archives/MISSINGBINARY*"
(I had to do this with nxagent: nxagent_1.4.92+1.5.0-4ubuntu0_i386.deb)

**IMPORTANT:**  In a text editor, open the file /usr/lib/nx/nxloadconfig.
On lines 498 and 501, change "strings" to "cat".  Save and close.


6) edit your /etc/nxserver/node.conf to reflect the changes you see fit.  Mine is **attached** here for reference (basically default settings, except encryption is required and local users can log in).


7) run "sudo nxsetup"
-> hit "Y" to say yes, you're sure you want to do this
-> hit "n" because you want to use a custom key.
NOTE:  At this point, it may ask you 

```
Setting up /var/lib/nxserver/db ...done
Setting up /var/log/nxserver.log ...done
Setting up known_hosts and authorized_keys2 ...done
Setting up permissions ...done

----> Testing your nxserver configuration ...
Warning: Invalid value "COMMAND_START_GNOME=gnome-session"
         Users will not be able to request a Gnome session.
Warning: Invalid value "COMMAND_START_CDE=cdwm"
         Users will not be able to request a CDE session.
Warning: Invalid value "COMMAND_SMBMOUNT=smbmount". You'll not be able to use SAMBA.
Warning: Invalid value "COMMAND_SMBUMOUNT=smbumount". You'll not be able to use SAMBA.
```

**THESE ERRORS ARE OKAY**

continued...```


  Warnings occured during config check.
  To enable these features please correct the configuration file.

<---- done

----> Testing your nxserver connection ...
The authenticity of host '127.0.0.1 (127.0.0.1)' can't be established.
RSA key fingerprint is yadayadayadayadayada.
Are you sure you want to continue connecting (yes/no)? yes
```

**TYPE IN YES VERY QUICKLY OR IT WILL FAIL**

**You should then get..........**

```
Warning: Permanently added '127.0.0.1' (RSA) to the list of known hosts.
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 quit
Quit
<--- done

Ok, nxserver is ready.

PAM authentication enabled:
  All users will be able to login with their normal passwords.

  PAM authentication will be done through SSH.
  Please ensure that SSHD on localhost accepts password authentication.

  You can change this behaviour in the /etc/nxserver/node.conf file.
Have Fun!
```

**If you get this, you may have been too slow, so try again:**

```
Are you sure you want to continue connecting (yes/no)? Fatal error: Could not connect to NX Server.

Please check your ssh setup:

        - Make sure "nx" is one of the AllowUsers in sshd_config. **or you don't have an "AllowUsers" line**
        - Make sure your sshd allows public key authentication. ** mine already was**
        - Make sure your sshd is really running on port 22.** set this to be the same in node.conf and sshd_config **
        - Make sure your sshd_config AuthorizedKeysFile in sshd_config is set to authorized_keys2.**I did have to do this. See below**
```
[/CODE]


8) As I mentioned above, I did have to edit the AuthorizedKeysFile in sshd_config... 
```
grep AuthorizedKeysFile /etc/ssh/sshd_config
** you should get...**
AuthorizedKeysFile /var/lib/nxserver/home/.ssh/authorized_keys2
```
...if not, find your 'authorized_keys2' file, and add a line similar to the one above to sshd_config by doing the following:
```
sudo echo "AuthorizedKeysFile /var/lib/nxserver/home/.ssh/authorized_keys2" >> /etc/ssh/sshd_config
``` (if your authorized_keys2 is in a different place, you will want to edit this command accordingly)

9) Reset sshd with:
sudo /etc/init.d/ssh restart

10) Finally, run:
sudo cat /var/lib/nxserver/home/.ssh/client.id_dsa.key
... this is your key that you MUST paste into the Configuration section of the NX client you want to use to access your nx server.

11) In the nx client, set up the following:

Host: 127.0.0.1
User:  your local username
Password: your normal password

------------

Configure...
 --->  Key...
         *Replace the default key with the contents of "sudo cat /var/lib/nxserver/home/.ssh/client.id_dsa.key"*

If you used the attached node.conf, you must also set:.
Enable SSL encryption for all traffic = Yes

12) Save, and hit Login... If you get authentication errors, check your sshd_config and make sure you pasted the current client.id_dsa.key.  Try the command "sudo nxserver --history" to see if the client is even talking to the server OK.  Good luck!

-- Fisslefink

PS: I rarely check the forum for replies, so if you need me, be sure to PM me.
PPS:  Thanks to the FreeNX team for this kickass software, and to NoMachine for their generosity with the code!

---

### Post by manatlan on 2006-04-24
thanx for your long and good tutorial ...

but my trouble is not here ...
i can use freenx/nomachine on local. I can start a session from another user of my local accounts, it works great ...
but it doesn't work from a distant box ...

---

### Post by Fisslefink on 2006-04-24
Salut manatlan,

I'm sorry the tutorial was not more helpful.  Did you dist-upgrade to Dapper, or perform a fresh installation?  Are you using Dapper Flight 6?

Things to check:

sshd_config (verify port #)
node.conf (verify port #)
iptables (check that you are not blocking incoming ssh -- not likely if SSH works as you say)
client.id_dsa.key (make sure that you are copying this to the remote client's machine, and loading it into the NX client configuration -- SSH is useful for this)

Try posting a new reply with the files I mentioned above (except client.id_dsa.key)

Erin



[QUOTE=manatlan]thanx for your long and good tutorial ...

but my trouble is not here ...
i can use freenx/nomachine on local. I can start a session from another user of my local accounts, it works great ...
but it doesn't work from a distant box ...[/QUOTE]

---

### Post by notecreim on 2006-04-25
Good tutorial. ;)

---

### Post by scadieux on 2006-05-17
I confirm that it works as well on Ubuntu (not Kubuntu) Dapper as of today... for gnome sessions.

---

### Post by n00bWillingToLearn on 2006-05-18
Why is it not secure to use the default keys with ssh?

---

### Post by johnsd8 on 2006-05-24
Very nice. Works great. Thanks for taking the time to write this up!

---

### Post by ElijahLofgren on 2006-05-26
**Thanks to Fisslefink for writing this tutorial!** :) I was able to login to my Ubuntu box from my mom's Windows 98 PC.  :D 

[QUOTE=Fisslefink]
...
5) If anything is missing, search for it with "sudo find /|grep MISSINGFILE"
...
[/QUOTE]
I have found found that doing the following is faster and easier:
```
whereis MISSINGFILE
```
I.E.
```
whereis nxdesktop
``` 

[QUOTE=Fisslefink]
...
7) run "sudo nxsetup"
-> hit "Y" to say yes, you're sure you want to do this
-> hit "n" because you want to use a custom key.
...
[/QUOTE]
I got different questions, so I had to hit "N" then "y".
> 
Do you want to abort now? [y/N] N
...
Do you want to use your own custom KeyPair? [y/N] y


Hope this helps someone.

---

### Post by ElijahLofgren on 2006-05-26
[QUOTE=n00bWillingToLearn]Why is it not secure to use the default keys with ssh?[/QUOTE]
I'm pretty sure it's because if somone tries to connect to your computer and tries using the default key, then they will easily have access to your computer. It would be much better to have a key that will be *much* harder to guess.

I'm guessing reasons for not using default SSH keys is similar to reasons for not using default passwords.

---

### Post by kthuno on 2006-05-30
Very useful tips. I had my FreeNX running on dapper in 10 minutes! Awesome!!!
Thanks a lot!...

---

### Post by jdmpike on 2006-06-01
I have been banging my head on this ](*,)  for a while now and just can't seem to get it.

I had a perfect working copy of freenx in breezy, but in Dapper, that is no more...

So far here is what I have done...

I have updated **/etc/apt/sources.list** to include the following:
```
deb http://mirror.ubuntulinux.nl/ dapper-seveas custom extras freenx java seveas-meta all
```

I have installed the following packages (I assume from the seveas repo):
```
sudo apt-get install freenx nxclient libxcomp1 libxcompext1 nxagent nxdesktop nxlibs nxviewer
```

***NOTE:** I couldn't find the nxproxy package... probably not good...

Modified my **/etc/ssh/sshd_config** to look like the following:

```

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile   /var/lib/nxserver/home/.ssh/authorized_keys2

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
PasswordAuthentication yes
AllowUsers nx

# To change Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#AFSTokenPassing no
#KerberosTicketCleanup no

# Kerberos TGT Passing does only work with the AFS kaserver
#KerberosTgtPassing yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
KeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

```

***NOTE:** I removed the "AllowUsers nx" because it didn't work...

Modified my **/etc/nxserver/node.conf** and attached the file

Can anyone help me figure out what I have done???

P.S. I sincerely am so happy that Dapper is here! It is a great improvement

God bless you all!

jdmpike

---

### Post by n00bWillingToLearn on 2006-06-01
[QUOTE=ElijahLofgren]I'm pretty sure it's because if somone tries to connect to your computer and tries using the default key, then they will easily have access to your computer. It would be much better to have a key that will be *much* harder to guess.

I'm guessing reasons for not using default SSH keys is similar to reasons for not using default passwords.[/QUOTE]

I am probably misunderstanding this but arent the default keys just the public keys anyways? I thought that your password for logging in was your private key and the keys we are talking about are the public keys? Isn't that the way it works with ssh at least?

---

### Post by jdmpike on 2006-06-01
The default keys are the one generated by freenx that are already set up on the NX Client by default. That means that if some random person has your username/password they will be able to login to your system.

By generating a new key, the nxserver will encrypt the traffic so that people who don't have the shared key can't login. This randomly generated key is huge - really hard to guess for those would be hackers out there...

Hope that explains how generating keys helps!

Now if I can just get my precious nxserver set up once again...

Peace, love and ubuntu!

jdmpike

---

### Post by n00bWillingToLearn on 2006-06-01
[QUOTE=jdmpike]The default keys are the one generated by freenx that are already set up on the NX Client by default. That means that if some random person has your username/password they will be able to login to your system.

By generating a new key, the nxserver will encrypt the traffic so that people who don't have the shared key can't login. This randomly generated key is huge - really hard to guess for those would be hackers out there...

Hope that explains how generating keys helps!

Now if I can just get my precious nxserver set up once again...

Peace, love and ubuntu!

jdmpike[/QUOTE]

Thank you for that explanation. And just curious is FreeNX currently being developed or has the project died? FreeNX is amazing and I don't want to see it just die off:cry: .

---

### Post by EngiBenchi on 2006-06-06
**Update**
It seems that the dist-upgrade was not complete after a new apt-get command it works as it did before






On kubuntu Breezy i had a fine working freenxserver. 
yesterday i updated the distro to dapper including the freenx server. But unfortunely the kde desktop wont come up if i start the nxclient. 
i only work remote on that pc (there is no monitor connetcted) so i'm not sure kde or xserver works at all. 
I do have some logs that may give a clu. 

server side:
```
ddxProcessArgument: WARNING: "never" value for -bs option is disabled.
ddxProcessArgument: WARNING: Setting default value "when_requested".

NXAGENT - Version 1.5.0

Copyright (C) 2001, 2005 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Agent running with pid '11840'.
/usr/lib/nx/nxagent: symbol lookup error: /usr/lib/nx/nxagent: undefined symbol: NXUnsetLibraryPath
xsetroot:  unable to open display 'unix:1000'
xset:  unable to open display "unix:1000"
xsetroot:  unable to open display 'unix:1000'
startkde: Starting up...
ksplash: cannot connect to X server unix:1000
krandrinithack: cannot connect to X server unix:1000
kded: cannot connect to X server unix:1000
DCOP aborting call from 'anonymous-11893' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
kcminit: cannot connect to X server unix:1000
ivman 0.6.3, http://ivman.sourceforge.net
Compiled against HAL 0.5.x or later
Running in system mode
manager.c:104 (discover_pmount_version) pmount does not accept --async
manager.c:130 (discover_pmount_version) pmount accepts -t <fs>
manager.c:161 (discover_pmount_version) pmount accepts -u <umask>
manager.c:963 (main) Running through rules for every current property.
IvmConfigCommon.c:131 (ivm_device_is_mountable) /org/freedesktop/Hal/devices/storage_model_FX322M is /dev/hdc
IvmConfigCommon.c:148 (ivm_device_is_mountable) /dev/hdc can't be mounted because it is not a volume
manager.c:993 (main) Entering main loop.

ksmserver: cannot connect to X server unix:1000
startkde: Shutting down...
klauncher: Exiting on signal 1
startkde: Running shutdown scripts...
startkde: Done.

```

Client side:
```
NX> 203 NXSSH running with pid: 3500
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 192.168.1.35 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: lex
NX> 102 Password: 
NX> 103 Welcome to: Servertje user: lex
NX> 105 listsession --user="lex" --status="suspended,running" --geometry="1280x1024x32+render" --type="unix-kde"
NX> 127 Sessions list of user 'lex' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: lex
NX> 105 startsession --session="servertje" --type="unix-kde" --cache="8M" --images="32M" --cookie="******" --link="lan" --kbtype="pc102/nl" --nodelay="1" --encryption="1" --backingstore="never" --geometry="fullscreen" --media="0" --agent_server="" --agent_user="" agent_password="******""  --screeninfo="1280x994x32+render" 

NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: Servertje-1001-A1AA4163CE819113A1C94A6C13A060CE
NX> 705 Session display: 1001
NX> 703 Session type: unix-kde
NX> 701 Proxy cookie: a1034139e15316453e2aed1e1043f7a8
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: a1034139e15316453e2aed1e1043f7a8
NX> 704 Session cache: unix-kde
NX> 707 SSL tunneling: 1
NX> 1004 Error: Session did not start.
NX> 504 Session startup failed.
NX> 999 Bye
Killed by signal 15.

NX> 203 NXSSH running with pid: 2532
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 192.168.1.35 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: lex
NX> 102 Password: 
NX> 103 Welcome to: Servertje user: lex
NX> 105 listsession --user="lex" --status="suspended,running" --geometry="1280x1024x32+render" --type="unix-kde"
NX> 127 Sessions list of user 'lex' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: lex
NX> 105 startsession --session="servertje" --type="unix-kde" --cache="8M" --images="32M" --cookie="******" --link="lan" --kbtype="pc102/nl" --nodelay="1" --encryption="1" --backingstore="never" --geometry="fullscreen" --media="0" --agent_server="" --agent_user="" agent_password="******""  --screeninfo="1280x994x32+render" 

NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: Servertje-1000-D4421473CB8077C603290D780C3C8E84
NX> 705 Session display: 1000
NX> 703 Session type: unix-kde
NX> 701 Proxy cookie: 837b196472e4de7aaf995606511fe4a0
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 837b196472e4de7aaf995606511fe4a0
NX> 704 Session cache: unix-kde
NX> 707 SSL tunneling: 1
NX> 1004 Error: Session did not start.
NX> 504 Session startup failed.
NX> 999 Bye
Killed by signal 15.

```

---

### Post by phillywize on 2006-06-08
Wow another thank you.  This worked with a minimum of sweat...

I am running Dapper, but inadvertently installed from the Breezy repo.  No troubles really, but for formality's sake, I updated to the dapper.

It's amazing what you can do when you push the limits of ubuntu...

---

### Post by j0bro on 2006-06-09
Having trouble connecting to an X.org 7 server w/ KDE with a NX client from a remote computer? I did, and finally found out that I needed to install the 'dbus-1-utils' package to meet the requirement of having 'dbus-launch' installed. 

In short, do: "apt-get install dbus-1-utils" and you should be able to make a connection. Hope it helps,

regards, Jeroen (NL)

---

### Post by unwoken on 2006-06-13
unfortunately i am having trouble even installing the client.

after adding the repo, i cannot install either the nx client or the nx desktop because of dependency issues.

the message synaptic gives is below:

nxclient:
 Depends: libstdc++2.10-glibc2.2  but it is not installable


i originally tried downloading the deb and the tar, but have had no luck at all.

i would appreciate any help :confused: 

u.

---

### Post by chz on 2006-06-14
i Have been able to log in to my server at home remotely from another computer at work, but it tends to log in and then freeze at random points...sumtimes as the panels are loading, sometimes as something is clicked on the screen, etc.

i did some tests at home, and see that connecting to my dyndns account which points back to my server does the same thing, but when i connect directly to the IP it works just fine.

---

### Post by palermi on 2006-06-16
I have this problem: "Authentication failed for user xxxxxxx"

---

### Post by palermi on 2006-06-16
YEAH!! WORKs !

but (always i have a but) when i login from localhost , i have no icons in my desktop, but if i login from windows xp it fine !

maybe because i have XGL ?

[img]http://static.flickr.com/66/168161690_2bf64e43bd_d.jpg[/img]

---

### Post by j.stagner on 2006-06-18
This rocks!!!  I followed Fisslefink's instructions, and while the process wasn't painless (I *still* can't get nxclient to run on my Kubuntu box) it is working quite well.  I am using the nxclient for Windows to type this response, and I couldn't be happier!!!

I had tried using other "remote desktop" solutions to try and admin my Kubuntu machine from my Windows machine, but performance was generally abominable.  I had my doubts before trying it, but Freenx is quite speedy on my WAN.

Thanks to everyone involved in developing NoMachine/Freenx and to those who post useful information on how to set it up and use it!!!!

[EDIT] I take it back, I can in fact use the nxclient for Linux, I just had to look in the Lost & Found ;)

---

### Post by jmoore5 on 2006-06-21
When following fisslefinks steps, I get stuck on step #4.  There is no sign of nxkeygen, nxloadconfig, nxnode, nxnode-login, nxserver, and nxsetup.  There are no packages for these files either. 

When following one of his earlier steps I entered...

deb [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) breezy-seveas freenx

...into the sources.list file and I was missing a bunch of files.  When I changed the word breezy to dapper and ran the process all over again, I'm still missing those files.

Any suggestions would be greatly appreciated.

---

### Post by hugmenot on 2006-06-21
[QUOTE=palermi]but (always i have a but) when i login from localhost , i have no icons in my desktop, but if i login from windows xp it fine !

maybe because i have XGL ?[/QUOTE]

No icons here either, and I use XGL here too.
Did you solve it since you posted?

EDIT: Ah, it&#8217;s getting weirder. Deeming myself smart I started nxclient in a new (non-XGL) Xnest window. The appearance speaks for itself.[img]http://www.ubuntuforums.org/attachment.php?attachmentid=11590&d=1150908444[/img]

---

### Post by Camino on 2006-06-28
[QUOTE=palermi]I have this problem: "Authentication failed for user xxxxxxx"[/QUOTE]
Hey palermi,
could you describe what you did to solve the problem. I´m stuck at the same problem here and can´t find a solution atm (nxserver 2.0)

Thanks

---

### Post by allnameswereout on 2006-06-28
Good tutorial.

Some suggestions:

1) Add notice about GnuPG keys or related warning.
2) Add notice it is i386 specific.

---

### Post by twinprism on 2006-06-30
If anyone else has had the misfortune of trying to get FreeNX working with the new Nomachine 2.0 client, you have to hack the nxnode file to get the fake cookie authentication working.  

I got it to work with this ugly hack..  by making it look like this around line 683

```

     if [ "$ENABLE_1_5_0_BACKEND" = "1" -a "$clientproto" = "1.5.0" ] || [ "$ENABLE_1_5_0_BACKEND" = "1" -a "$clientproto"  = "1.4.0" ]        
      then
                # enable fake cookie authentication
                cookie=$proxy_cookie
        fi

```

Counterintuitively, the 2.0 version of the client uses 1.4.0 as the proto so 
you would need some sort of additional conditional to get it to work 1.4 clients as well..

---

### Post by YvesDL on 2006-07-08
> **jdmpike said:**
> I have been banging my head on this ](*,)  for a while now and just can't seem to get it.

I had a perfect working copy of freenx in breezy, but in Dapper, that is no more...

So far here is what I have done...

I have updated **/etc/apt/sources.list** to include the following:
```
deb http://mirror.ubuntulinux.nl/ dapper-seveas custom extras freenx java seveas-meta all
```

I have installed the following packages (I assume from the seveas repo):
```
sudo apt-get install freenx nxclient libxcomp1 libxcompext1 nxagent nxdesktop nxlibs nxviewer
```

***NOTE:** I couldn't find the nxproxy package... probably not good...

Modified my **/etc/ssh/sshd_config** to look like the following:

```

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile   /var/lib/nxserver/home/.ssh/authorized_keys2

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
PasswordAuthentication yes
AllowUsers nx

# To change Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#AFSTokenPassing no
#KerberosTicketCleanup no

# Kerberos TGT Passing does only work with the AFS kaserver
#KerberosTgtPassing yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
KeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

```

***NOTE:** I removed the "AllowUsers nx" because it didn't work...

Modified my **/etc/nxserver/node.conf** and attached the file

Can anyone help me figure out what I have done???

P.S. I sincerely am so happy that Dapper is here! It is a great improvement

God bless you all!

jdmpike

Hi there,

I just installed successfuly the freenx version, downloaded from seveas.  I had the same problems you have. Tried to modifiy the sshd config file and etc...  Didn't work for me.  So here's what did:

1- I uninstalled completly (including conf files) openssh server with synaptic.
2- I uninstalled completly (including conf files) freenx server with synaptic.
3- I reinstalled freenx using synaptic, it installed openssh as a dependency. Chose the default nx keys when asked by synaptic.
4- Tada!  Works fine. :D 

Hope it helps,

gooday mate

YvesDL

---

### Post by GhettoPuNKkiD on 2006-07-13
I have FREENX daemon started..but when I connect from my XP machine  the NX client dialog box just disappears.. It says it has established a connection, but I can't get a desktop. I'm using Breezy. HELP!:confused:

---

### Post by sjv on 2006-07-13
I previously had FreeNX working perfectly under Breezy, and am now trying to get it up and running under Dapper. Connecting from my windows machine(where nothing has changed), it connects, auths, and puts up the big black screen with the !M logo, stays there for a while like usual, and then just goes away.

My server logs contain the following:
```

-- NX SERVER START: -c /usr/lib/nx/nxserver
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: steve
NX> 102 Password: 
NX> 103 Welcome to: dev1 user: steve
NX> 105 listsession --user="steve" --status="suspended,running" --geometry="1920x1200x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'steve' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: steve
NX> 105 startsession --session="dev1.remote" --type="unix-gnome" --cache="8M" --images="32M" --cookie="******" --link="isdn" --kbtype="pc102/en_US" --nodelay="1" --encryption="1" --backingstore="never" --geometry="fullscreen" --media="0" --agent_server="" --agent_user="" agent_password="******""  --screeninfo="1920x1147x32+render" 

steve@127.0.0.1's password: 
NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: dev1-1000-19191CBC98710EE81CEC1C36B971572F
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: 304697a8d57ce629eb6e54a41239d89f
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 304697a8d57ce629eb6e54a41239d89f
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
NX> 105 bye
Bye
NX> 999 Bye
NX> 1009 Session status: terminating
NX> 1006 Session status: closed
NX> 1001 Bye.

```

My question is, who is saying bye? Is it the win !M client, or my server? Any ideas what might be wrong here?

---

### Post by GhettoPuNKkiD on 2006-07-16
Hello all.. I did get the software from the sveas repositories.
Server daemon is up. I get Authorized completed then it hangs for awhile then gives me a timeout. Any gives? By the by, I'm using Dapper.

```

NX> 203 NXSSH running with pid: 176
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.0.68 on port: 8888
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.4.0
NX> 134 Accepted protocol: 1.4.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: erik
NX> 102 Password: 
NX> 103 Welcome to: casper user: erik
NX> 105 listsession --user="erik" --status="suspended,running" --geometry="1024x768x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'erik' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: erik
NX> 105 startsession  --link="lan" --backingstore="when_requested" --nodelay="1" --encryption="1" --cache="8M" --images="32M" --media="1" --mediahelper="esd" --session="hp" --type="unix-gnome" --cookie="******" --geometry="fullscreen" --kbtype="pc102/en_US" --screeninfo="1024x740x32+render" 

Killed by signal 15.

```

---

### Post by allnameswereout on 2006-07-16
> **twinprism said:**
> If anyone else has had the misfortune of trying to get FreeNX working with the new Nomachine 2.0 client, you have to hack the nxnode file to get the fake cookie authentication working.  

I got it to work with this ugly hack..  by making it look like this around line 683

```

     if [ "$ENABLE_1_5_0_BACKEND" = "1" -a "$clientproto" = "1.5.0" ] || [ "$ENABLE_1_5_0_BACKEND" = "1" -a "$clientproto"  = "1.4.0" ]        
      then
                # enable fake cookie authentication
                cookie=$proxy_cookie
        fi

```

Counterintuitively, the 2.0 version of the client uses 1.4.0 as the proto so 
you would need some sort of additional conditional to get it to work 1.4 clients as well..

FreeNX 1.5 is released which has support for the 2.0 protocol.
Get it here: [http://developer.berlios.de/project/showfiles.php?group_id=2978&release_id=10441](http://developer.berlios.de/project/showfiles.php?group_id=2978&release_id=10441)

---

### Post by lindsay_keir on 2006-07-25
I also get the message "authentication failed for user" - it seems to be after a power failure, and probably something to do with resume getting confused. Anyway, my resolution is to delete the .nx directory and re-install freenx (only freenx, the other program's do not seem to be affected)

From both the client and server computers - use ssh to access the server.
 sudo rm -R .nx
 sudo apt-get remove freenx
 sudo apt-get install freenx

---

### Post by hotelwhiskey on 2006-07-29
> **sjv said:**
> 
My server logs contain the following:
```

-- NX SERVER START: -c /usr/lib/nx/nxserver
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: steve
NX> 102 Password: 
NX> 103 Welcome to: dev1 user: steve
NX> 105 listsession --user="steve" --status="suspended,running" --geometry="1920x1200x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'steve' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: steve
NX> 105 startsession --session="dev1.remote" --type="unix-gnome" --cache="8M" --images="32M" --cookie="******" --link="isdn" --kbtype="pc102/en_US" --nodelay="1" --encryption="1" --backingstore="never" --geometry="fullscreen" --media="0" --agent_server="" --agent_user="" agent_password="******""  --screeninfo="1920x1147x32+render" 

steve@127.0.0.1's password: 
NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: dev1-1000-19191CBC98710EE81CEC1C36B971572F
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: 304697a8d57ce629eb6e54a41239d89f
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 304697a8d57ce629eb6e54a41239d89f
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
NX> 105 bye
Bye
NX> 999 Bye
NX> 1009 Session status: terminating
NX> 1006 Session status: closed
NX> 1001 Bye.

```

My question is, who is saying bye? Is it the win !M client, or my server? Any ideas what might be wrong here?

I am observing the exact same situation.  Can anyone shed some light on this issue??  I have tried removing the nxserver and the openssh packages using synaptic and then reinstalling them.

---

### Post by Predseda3D on 2006-08-02
> **twinprism said:**
> If anyone else has had the misfortune of trying to get FreeNX working with the new Nomachine 2.0 client, you have to hack the nxnode file to get the fake cookie authentication working.  

I got it to work with this ugly hack..  by making it look like this around line 683

```

     if [ "$ENABLE_1_5_0_BACKEND" = "1" -a "$clientproto" = "1.5.0" ] || [ "$ENABLE_1_5_0_BACKEND" = "1" -a "$clientproto"  = "1.4.0" ]        
      then
                # enable fake cookie authentication
                cookie=$proxy_cookie
        fi

```

Counterintuitively, the 2.0 version of the client uses 1.4.0 as the proto so 
you would need some sort of additional conditional to get it to work 1.4 clients as well..

Hi,
there is another problem with newest client v. 2.0.0 . The newest version of NX Client (2.0.0-98 now) uses 1.5.0 proto version, so this hack is not needed for this clients, but use new value for 'backingstore' option, which fails to create new session. You can read more about this with solution for it here:
[http://openfacts.berlios.de/index-en.phtml?title=FreeNX_FAQ/Problem_Solving]("http://openfacts.berlios.de/index-en.phtml?title=FreeNX_FAQ/Problem_Solving")
or here:
[http://gentoo-wiki.com/Talk:HOWTO_FreeNX_Server#Solutions_for_NX_Clients_versions_2.0.0_and_FreeNX_0.4.x_and_0.5.0]("http://gentoo-wiki.com/Talk:HOWTO_FreeNX_Server#Solutions_for_NX_Clients_versions_2.0.0_and_FreeNX_0.4.x_and_0.5.0")

Hope that will help. 

Predseda

---

### Post by iH8forcedRegistration on 2006-08-04
An older Windows version of the client is available [here](http://www.users.muohio.edu/charnedn/nxclient.win.zip) under the license from [here](http://www.users.muohio.edu/charnedn/license-info).

This is a ZIP of a working Program Files directory. The following procedure 
seems to work:
- Download the new nomachine version's installer and run it
- Delete the NX Client directory in Program Files
- Extract this ZIP there
- Happily use your home machine from work :)

Yes, it's not an ideal solution, but it works as a quick, hacky workaround until the apt packages get updated.

---

### Post by SlamBam on 2006-08-05
Hi,

I got some very strange results. I can connect to my machine using one username/pass combo, but not with the other. I use the 1.5.0-138 client on Windows XP, and just used the guide to install on Ubuntu 6.06. 

Log on client side when I can´t connect:
```
NXPROXY - Version 1.5.0

Copyright (C) 2001, 2005 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '3864'.
Info: Connecting to remote host '192.168.1.101:5000'.
Info: Connection to remote proxy '192.168.1.101:5000' established.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Not using NX delta compression.
Info: Using lan link parameters 16384/8/0/0.
Info: Using pack method '16m-png-9' with session 'unix-gnome'.
Info: Not using ZLIB stream compression.
Info: Not using remote ZLIB stream compression.
Info: Not using persistent cache.
Info: Using remote server '192.168.1.101:5000'.
Info: Starting X protocol compression.
Info: Established X server connection.
Info: Using shared memory support in X server.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting.
```

Anyone got a clue why the end of session is requested? By who?

Thanks

---

### Post by Khannie on 2006-08-08
> **hotelwhiskey said:**
> I am observing the exact same situation.  Can anyone shed some light on this issue??  I have tried removing the nxserver and the openssh packages using synaptic and then reinstalling them.

I'm seeing the exact same thing. Anyone overcome this yet?

---

### Post by Khannie on 2006-08-08
Well....I overcame my problems. I hope this helps someone else. Not sure /entirely/ what fixed the problem, but here are the steps I followed:

completely removed freenx (including config files) with synaptic
completely removed openssh server (including config files) with synaptic
reinstalled freenx (this has a dependency on openssh, so reinstalls it)
added localhost to the /etc/hosts.allow file

Followed the instructions [here](http://www.ubuntuforums.org/showthread.php?t=97277) (edit: don't forget to add your default user to the allowed users in the sshd_config file if you want to be able to ssh into your machine from remote computers). After the sudo dpkg-reconfigure freenx, I imported the newly generated key, and presto, everything worked.

---

### Post by galamud on 2006-09-05
> **palermi said:**
> YEAH!! WORKs !

but (always i have a but) when i login from localhost , i have no icons in my desktop, but if i login from windows xp it fine !

maybe because i have XGL ?


From [http://www.nomachine.com/tr/view_notes.php?commid=108&id=TR05D01384]("http://www.nomachine.com/tr/view_notes.php?commid=108&id=TR05D01384"):

> The problem disappears if the Render extension is non used

The problem seems to be related to the Render extension. A workaround is to disable the Render extension using the "custom settings" panel in NX Client GUI.

The problem arises because the X11 agent returns to the X clients more picture formats than the ones available by the Xgl X server. So it may happen that the applications try to use a picture format not available by the X server. This makes the  Render acceleration by the X11 agent failing. 

---

### Post by perchecreek on 2006-09-06
I attempted to install freenx on ubuntu and received message below.

Could someone post detailed instructions for how to do each of these? 

Please check your ssh setup:

        - Make sure "nx" is one of the AllowUsers in sshd_config.
        - Make sure your sshd allows public key authentication.
        - Make sure your sshd is really running on port 22.
        - Make sure your sshd_config AuthorizedKeysFile in sshd_config is set to authorized_keys2.

thank you.

---

### Post by perchecreek on 2006-09-06
I just did an apt-get remove freenx, and tried installing nomachines's server (the free version), and received this error:

dpkg: error processing nxserver (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nxclient
 nxnode

Yes, ssh works and is running on port 22.

So, sadly, it seems that the installers for freenx and for nxserver's free version, when run on Ubuntu Dapper Drake, land one in a troubleshooting situation that is not for the inexperienced, or for those short on time. The help messages can be a bit cryptic, too.  Er, what was that? 'dependency problems'?  Now what?

---

### Post by galamud on 2006-09-07
> **perchecreek said:**
> I just did an apt-get remove freenx, and tried installing nomachines's server (the free version), and received this error:

dpkg: error processing nxserver (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nxclient
 nxnode


There's 2 other packages on the nomachine page that you need to download, called "nxclient" and "nxnode".  You can find them both on the downloads page.

If they set up a proper repository, you wouldn't have this problem, but c'est la vie.

---

### Post by galamud on 2006-09-07
> **perchecreek said:**
> I attempted to install freenx on ubuntu and received message below.

Could someone post detailed instructions for how to do each of these? 

Please check your ssh setup:

        - Make sure "nx" is one of the AllowUsers in sshd_config.
        - Make sure your sshd allows public key authentication.
        - Make sure your sshd is really running on port 22.
        - Make sure your sshd_config AuthorizedKeysFile in sshd_config is set to authorized_keys2.

thank you.

There's a file in /etc/ssh/ called sshd_config.  It's relatively well-commented, so you should be able to find the settings described there yourself.  If not, paste it in a reply and I'll take a look.

Are you able to ssh into the machine using your regular account?

---

### Post by perchecreek on 2006-09-11
galamud, thank you for the replies.  I'll need to put solving this on hold for a bit due to other commitments, and then I'm sure a little poking around will get things working.

---

### Post by k.breiner on 2006-09-13
I've read about the fixes, but still cannot connect from my XP machine to my Linux box using the 2.0.0-98 Windows client.   The 1.5 client works fine.

I tried the "backingstore" fix, and I think it has made some progress (i.e. no error now), but I still cannot connect.  Now I get all the way to the end, and it acts like it connects ("Established X server connection") and then the window just disappears.  No error, nothing!  I suspect the session is actually running; I just cannot see it.

If anyone has any ideas, please let me know.  I can post logs if someone tells me where to find them.  I'm more of a Windows guy and sort of a Linux noob.

Thanx!
Karl

---

### Post by 1Time on 2006-09-14
I tried for over 24 hours to install this using the instructions in this thread, and never could get all the pieces to play nicely together.  After that I found the thread at [http://www.ubuntuforums.org/showthread.php?t=204976]("http://www.ubuntuforums.org/showthread.php?t=204976") and while it has you installing packages not from a repository, at least the end result is a working NX server that can be used with the latest client.  If you are banging your head against the desk because you can't get this working, try the above-mentioned thread (be sure to read the comments first).  I wish I'd found the above page about 36 hours ago. Did I mention that the instructions there are a WHOLE lot easier to follow?  15 minutes vs. 30 hours of my life I can never get back (well, okay, there was time spent sleeping and eating in there somewhere).  :?

---

