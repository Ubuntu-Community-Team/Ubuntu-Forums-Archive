---
title: "totally lost on remote login"
date: 2010-06-02
forum: General Help
---

### Post by erupter on 2010-06-02
So i want to setup my home server.
Right now i'm doing tests on a VM.
I installed x11vnc and ssh server.
But i'm lost at how those two should interact between them and my tightVnc windows client.
TightVnc doesn't seem to have a space for any key i should generate with ssh (or so i understand).

I tried using Gnome remote desktop, but you need to already be logged in.
And besides i changed my user password, and now I get a warning
```
the password you use to log in to your computer no longer matches that of your login keyring
```and it asks for my old password.

I then tried making a script and adding to the startup queue:
```
### BEGIN INIT INFO
# Provides:          myscript
# Required-Start:    $all
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start daemon at boot time
# Description:       Enable service provided by daemon.
### END INIT INFO

x11vnc -display :0
```the script is called myscript.sh, placed in /etc/init.d/
and i did

```
sudo update-rc.d myscript.sh defaults
```

But upon restart x11vnc is not running, or at least TightVnc can't connect.
While if i manually start if from a terminal, it works.

So can anyone please help me understand what should i do?
I essentially need remote desktop, but i should be able to login, or at least set it up that it automatically logs in my user and then locks the screen.

---

### Post by krunge on 2010-06-02
Are you sure the X server :0 is running when your rc-script starts x11vnc?

I'm not sure, but there may still be permissions/xauthority issues with what you've set up even if the X server is running at that point.  I suggest the /etc/X11/gdm/Init/Default method described under the section 'Continously' here:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]

Regarding SSH tunnels nearly all VNC clients require you set up the tunnel on your own.  A few will set it up for you: x11vnc has a somewhat cheesy vncviewer wrapper called SSVNC that runs on windows, unix, mac and will set up the SSH tunnel for you.  There may be others.

---

### Post by erupter on 2010-06-02
I can't be sure the X server is running, but the
```

# Required-Start:    $all
```
part should ensure that my script is the last thing that runs.

I'll give a shot at your link.

As for cheesy wrappers, i'd prefer to understand how it works.
I read a number of tutorials, but they are all somewhat convoluted and non linear (imho).

---

### Post by krunge on 2010-06-02
> **erupter said:**
> 
As for cheesy wrappers, i'd prefer to understand how it works.
I read a number of tutorials, but they are all somewhat convoluted and non linear (imho).
Maybe these will help:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-ssh-unix](http://www.karlrunge.com/x11vnc/faq.html#faq-ssh-unix)
[http://www.karlrunge.com/x11vnc/faq.html#faq-ssh-putty](http://www.karlrunge.com/x11vnc/faq.html#faq-ssh-putty)[/INDENT]

Here is the main point from the first one:
> 
For x11vnc one can tunnel the VNC protocol through an encrypted ssh channel. It would look something like running the following commands:

  sitting-here> ssh -t -L 5900:localhost:5900 far-away.east 'x11vnc -localhost -display :0'

(you will likely have to provide passwords/passphrases to login from sitting-here into your far-away.east Unix account; we assume you have a login account on far-away.east and it is running the SSH server)

And then in another terminal window on sitting-here run the command:

  sitting-here> vncviewer -encodings "copyrect tight zrle hextile" localhost:0

If you are using putty on windows you'd need to do the equivalent of the first command inside the putty gui (that is the 2nd link I give.)

Note the above starts x11vnc, if it is already running (your plan) you of course don't have to start it.

---

### Post by erupter on 2010-06-02
Thanks Krunge.
I already knew your tutorials, been reading them.

I have been able to setup an SSH connection by using the standard user/pass auth.
What i can't do is use keys.

I used Putty to create a public and a private key.
I then copied the public to my ssh server, added to known keys and restarded the service. And used putty to connect.
But it does not work, it refuses the connection.

I have also tried TightVnc, but it gives error "you must supply a username: user@host..."
But i can't find where i should put the user info.

Right now i learned that my server is an "anonymous Diffie Hellman"... gonna search for this.

---

### Post by jerome1232 on 2010-06-02
Did you convert the putty public key to an openssh public key?

I actually generate the keys on the server and copy the private key off of the server to the client, leaving the public key on the server. Putty can convert openssh keys into putties format.

so if you wanted to gen the keys on the server you would log into and run ---

```
ssh-keygen
```

You could use [winscp]("http://winscp.net/eng/index.php") to easily copy the file to your client. If you stuck with default values it will be ~/.ssh/id_rsa. Then use putty keygen to convert the openssh key to a putty key file.

---

### Post by erupter on 2010-06-02
Finally i did it!
With Putty. I succeeded in making an SSH connection.
Now... how do i tell TightVNC where to look for my private-key?
It still says "pageant has 0 SSH-2 keys".



> Ok i'm getting confused.

How many keys should i have?

And what are certificates?


I created 2 keys (private and public) on my windows pc with putty.

Jerome is suggesting i create the keys on the unix server, copy the private key over to the windows client, and convert by means of putty.
Shouldn't the server also have some kind of key?



I now did what jerome suggested: created the keys with ssh-keygen, copied the private over to my windows pc, imported in putty.
I think i will include my sshd_config
right now i can't login, putty says "disconnected. no supported authentication methods available"

and here is my sshd_config
```

# Package generated configuration file
# See the sshd_config(5) manpage for details

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
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile    %h/.ssh/authorized_keys

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
PasswordAuthentication no

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

PermitRootLogin no
AllowUsers erupter
```How do i tell both Putty and TightVNC which key file to use?
Right now i tried TightVNC and i saw a terminal window in which there was "pageant has 0 SSH-2 keys"
I guess they don't find my private key file, but alas i can't find how to tell them where to look for it.


Update: ok i found how to tell putty where to look for my private key: now in the terminal window it says "Server refused our key". but it's the same generated on the server!!!

---

### Post by erupter on 2010-06-07
Hey Krunge, hope you're still reading this.
I managed to set up my ssh server, and am able to open a console via ssh from windows to linux.
I can also launch x11vnc and use my tunnel to pass data via ssh. So it basically works.
But if i use the -localhost directive while launching x11vnc, connections are no more accepted. And i'm a bit lost on this. Seems like the tunneled data does not seem to come from the same computer to the server...
But i'm sure i'm using the tunnel as these are two different machines, and i'm putting "localhost" in the vncviewer...


Ok did some other trys and it works if I use "-listen serverIP" rather then "-localhost".
It shows it receives a connection from the same server ip address rather then from 127.0.0.1.
How's that?

Now onto autostarting :P

---

### Post by krunge on 2010-06-07
> **erupter said:**
> 
Ok did some other trys and it works if I use "-listen serverIP" rather then "-localhost".
It shows it receives a connection from the same server ip address rather then from 127.0.0.1.
How's that?

Sounds wrong (i.e. no SSH encryption.)

Please paste in the full x11vnc cmdline you are using.

And also provide the port redirection settings you configured in Putty.

And, finally, indicate what machine and vnc display you told your VNC viewer to connect to.

---

### Post by erupter on 2010-06-08
> **krunge said:**
> Please paste in the full x11vnc cmdline you are using.
i'm using a config file, here it is
```

listen 192.168.1.102
allow 192.168.1.102 127.0.0.1
nopw
find
forever
reopen
ncache 10
rfbport 5900

```> And also provide the port redirection settings you configured in Putty.Here i discovered another strange pair of things:
-on my network everything is slow as hell via ssh, while if connecting from the ISP external ip, everything is far faster
-forwarding from inside works, forwarding from outside doesn't work

Right now i'm testing these two configs:
local network: forward ports 5900 and 5901 of the remote 192.168.1.102 to the same ports locally and directly connect to 192.168.1.102:22

external network: same forwardings, but connect to external_ip_address:random_port_i_chose which the router then forwards to 192.168.1.102:22
in this case ssh works (and login is a lot faster then on the local network: meaning quasi instantaneous, while on the local network key negotiations take some noticeable seconds), but vnc connections are refused locally (meaning they don't even get to the server)


> And, finally, indicate what machine and vnc display you told your VNC viewer to connect to.Haveing used the -find command, it does all the work by itself, but as of now it has always found the correct xserver.
x11vnc is running on the same maching it is providing service for. and i manually start it from ssh connection

**UPDATE**
Ok by thinking about it i think i understood that there must be something wrong with the external forwarding.
But... if i know what internal address the server has, it's ok i can type it in. and this way it works.
I use this kind of forwarding:
L5900 192.168.1.102:5900

What if i don't know it? i tried
L5900 localhost:5900
L5900 127.0.0.1:5900
but they don't work, connections are refused locally... 
What should i put in the remote address field in putty? it shouldn't be the external ip eighter, since the ssh makes a tunnel through it... so what?

---

### Post by krunge on 2010-06-08
> **erupter said:**
> 
What if i don't know it? i tried
L5900 localhost:5900
L5900 127.0.0.1:5900

Yes, that is the correct way to do it. Use this and nothing else.
> 
but they don't work, connections are refused locally... 

Did you get rid of your 'listen 192.168.1.102' in the x11vnc config file and replace it with 'localhost'?

---

### Post by krunge on 2010-06-08
> 
Did you get rid of your 'listen 192.168.1.102' in the x11vnc config file and replace it with 'localhost'?
Also remove your 'allow' line in the file.

---

### Post by erupter on 2010-06-10
Ok Krunge it's working now, many thanks!

If I may, i have a couple questions more though...

1) i can't use gnome remote desktop anymore, it says connections are accepted from localhost only. but i didn't mess with that, so i don't know how such a setting ventured to the xserver too...

2) right now my rig is an athlon XP 2500+ with 1gig ram and an Ati Radeon 9600 (if i remember correctly) with the screen set at 1024x768. VNC refresh is quite slow even if i am on a 100mbit lan. reported data rates vary from 99KB/s to 250KB/s but most of the times, between parentesis, a much higher data rate is reported 

```
10/06/2010 10:10:13 client 1 network rate 253.9 KB/sec (811.8 eff KB/sec)
10/06/2010 10:10:13 client 1 latency:  3.2 ms
10/06/2010 10:10:13 dt1: 3.2591, dt2: 0.6194 dt3: 0.0032 bytes: 984519
10/06/2010 10:10:13 link_rate: LR_UNKNOWN - 3 ms, 253 KB/s

```As a viewer i'm using  TightVNC with High Speed Network settings.

Could it be the raw horsepower of the system that causes this?
But i remember then when i first tried genome own remote desktop it was way faster then this. SSH compression is disabled, and on the receiving part i have a core2duo with plenty of ram and stuff.


update
here is another capture of the server showing higher transfer rates
```

10/06/2010 10:20:01 client 1 network rate 215.4 KB/sec (2553.0 eff KB/sec)
10/06/2010 10:20:01 client 1 latency:  4.4 ms
10/06/2010 10:20:01 dt1: 0.0262, dt2: 0.1765 dt3: 0.0044 bytes: 43195
10/06/2010 10:20:01 link_rate: LR_UNKNOWN - 4 ms, 215 KB/s

```

---

### Post by krunge on 2010-06-10
> 
1) i can't use gnome remote desktop anymore, it says connections are accepted from localhost only. but i didn't mess with that, so i don't know how such a setting ventured to the xserver too...

You mean vino?  Maybe have x11vnc listen on a different port:
```
x11vnc ... -rfbport 5901
```

Then of course change your putty port redir config for x11vnc to be "L5900 localhost:5901"
> 
2) right now my rig is an athlon XP 2500+ with 1gig ram and an Ati Radeon 9600 (if i remember correctly) with the screen set at 1024x768. VNC refresh is quite slow even if i am on a 100mbit lan. reported data rates vary from 99KB/s to 250KB/s but most of the times, between parentesis, a much higher data rate is reported 

These rates are just ballpark estimates and shouldn't be taken too seriously. I doubt they are related to the problem you are seeing.

> 
Could it be the raw horsepower of the system that causes this?

No, I don't think so.

Send these parts of the x11vnc output, they are much more important information:

```

THIS:

10/06/2010 09:11:52 fb read rate: 10 MB/sec
10/06/2010 09:11:52 The X server says there are 5 mouse buttons.
10/06/2010 09:11:53 screen setup finished.

AND:

10/06/2010 09:12:07 Pixel format for client 127.0.0.1:
10/06/2010 09:12:07   16 bpp, depth 16, little endian
10/06/2010 09:12:07   true colour: max r 31 g 63 b 31, shift r 11 g 5 b 0
10/06/2010 09:12:07 no translation needed
10/06/2010 09:12:07 Using compression level 1 for client 127.0.0.1
10/06/2010 09:12:07 Using image quality level 9 for client 127.0.0.1
10/06/2010 09:12:07 Enabling X-style cursor updates for client 127.0.0.1
10/06/2010 09:12:07 Enabling full-color cursor updates for client 127.0.0.1
10/06/2010 09:12:07 Enabling cursor position updates for client 127.0.0.1
10/06/2010 09:12:07 Enabling LastRect protocol extension for client 127.0.0.1
10/06/2010 09:12:07 Enabling NewFBSize protocol extension for client 127.0.0.1
10/06/2010 09:12:07 Using tight encoding for client 127.0.0.1

```

Also there is a bug in the Xorg X server and you may need to supply the -noxdamage option to x11vnc:
```
x11vnc ... -noxdamage
```
You can search these forums for "noxdamage" for more info.

---

### Post by erupter on 2010-06-10
```

10/06/2010 17:38:33 Xinerama is present and active (e.g. multi-head).
10/06/2010 17:38:33 fb read rate: 9 MB/sec
10/06/2010 17:38:33 The X server says there are 13 mouse buttons.
10/06/2010 17:38:33 screen setup finished.


10/06/2010 17:38:34 Pixel format for client 127.0.0.1:
10/06/2010 17:38:34   32 bpp, depth 24, little endian
10/06/2010 17:38:34   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
10/06/2010 17:38:34 no translation needed
10/06/2010 17:38:34 rfbProcessClientNormalMessage: ignoring unsupported encoding type zlibhex
10/06/2010 17:38:34 Enabling X-style cursor updates for client 127.0.0.1
10/06/2010 17:38:34 Enabling full-color cursor updates for client 127.0.0.1
10/06/2010 17:38:34 Enabling cursor position updates for client 127.0.0.1
10/06/2010 17:38:34 Using image quality level 6 for client 127.0.0.1
10/06/2010 17:38:34 Enabling LastRect protocol extension for client 127.0.0.1
10/06/2010 17:38:34 Enabling NewFBSize protocol extension for client 127.0.0.1
10/06/2010 17:38:34 Using hextile encoding for client 127.0.0.1

```I have since moved my x11vnc port to 8000, so 5900 should be free.
But the fact is Vino (is it? i don't know, using lucid lynx here) automatically reports incoming connections are accepted from localhost only. As if there was some kind of block like the SSH tunnel, but i didn't put it up and i never configured any firewall or anything.

I'll try the -noxdamage.

And i don't have xinerama :S

Update: ok i have been able to connect to Vino.
Now i have the two VNCs: Vino is refreshing at about 5Hz, while X11 at abut 0.2Hz
That's my main problem. Same viewer (TightVNC) with same options.

This is the config file i'm using now
```


#listen 192.168.1.102
#allow 192.168.1.102 127.0.0.1
localhost
nopw
find
forever
reopen
#ncache 10
#rfbport 5900
autoport 8000
nowf
#scale 2/3
overlay_nocursor
noxdamage


```

---

### Post by krunge on 2010-06-10
> 
Update: ok i have been able to connect to Vino.
Now i have the two VNCs: Vino is refreshing at about 5Hz, while X11 at abut 0.2Hz
That's my main problem. Same viewer (TightVNC) with same options.

Is the vino connection also using the 'hextile' encoding or is it using the 'tight' encoding?  Can you force your viewer to use the 'tight' encoding?

Are the refresh rates you report above over a LAN or over broadband?

Please kill all existing x11vnc processes (e.g. killall), restart x11vnc and then connect, repeat the 0.2 Hz problem, and attach the entire, full x11vnc log output to this thread (preferrably as an attachment) and I will have a look.  0.2 Hz makes no sense..  Please also explain the sorts of activities you are doing while estimating these refresh rates.

BTW: you can get rid of 'overlay_nocursor', it doesn't apply to your OS.

Also, why did you specify 'nowf'?  That will only slow down the response, right?

---

### Post by erupter on 2010-06-11
> **krunge said:**
> Is the vino connection also using the 'hextile' encoding or is it using the 'tight' encoding?  Can you force your viewer to use the 'tight' encoding?

Are the refresh rates you report above over a LAN or over broadband?

Please kill all existing x11vnc processes (e.g. killall), restart x11vnc and then connect, repeat the 0.2 Hz problem, and attach the entire, full x11vnc log output to this thread (preferrably as an attachment) and I will have a look.  0.2 Hz makes no sense..  Please also explain the sorts of activities you are doing while estimating these refresh rates.

BTW: you can get rid of 'overlay_nocursor', it doesn't apply to your OS.

Also, why did you specify 'nowf'?  That will only slow down the response, right?

I don't know what encoding it ends up using, as there is not debug output for vino.
I two instances of the same viewer: tightvnc. with same option "highspeed network".
One connected via ssh to x11 and one directly to vino.
Both tests are done while bot computers are connected to the local network as to put the two connections on an even ground. I know that if i am outside i have the 1megabit upload of the dsl capping performances.
I'll post the debug info once i can do a new test.
Anyway i was using the player/stage program, that gives a nice moving window with live time feedback and even update rate (meaning you can set it to update the state at the interval you want). That's how i noticed that awkward difference: while on the vino connection i was looking at the time updating every about 200ms, the x11 connection was jerky at best, sometimes updating the major part of the window, but lagging the time information behind. And anyway clearly lagging a lot behind vino, updating every so many seconds. I thought that recording such a behaviour would have been self-explanatory, but i don't have any means of doing it. short of using my camera pointed at the screen... which gives awful results.

---

