---
title: "How do you create a .Xauthority file for remote access"
date: 2011-10-18
forum: General Help
---

### Post by mancora on 2011-10-18
I am trying to enable remote X access to my server but it seems that I need a .Xauthority file to be able to connect to the server. I can ssh without any problem and I already enable all the X11 options under the sshd_config file:

X11Forwarding yes X11DisplayOffset 10 X11UseLocalhost yes

Do I have to use the xauth or xhost command to generate the Xauthority file 
and how do you assign the display?

Thanks,
Mancora

---

### Post by hwttdz on 2011-10-18
I think you're overthinking this, passing  -X as an argument to ssh when you're connecting should be sufficient.  i.e. 

ssh -X myname@somehost

you'll get a 
"/usr/bin/xauth:  file /home/myname/.Xauthority does not exist" 
but it will make one for you on the spot, then you can open up a graphic application from the remote machine, try "gedit" and all should go along smoothly.

---

### Post by mancora on 2011-10-20
[hwttdz]("http://ubuntuforums.org/member.php?u=175488") thanks for your reply, I had done what you said and I have now the .Xauthority file in my home directory.

/home/user

-rw-------   1 user user      0 2011-10-13 13:36 .Xauthority
-rw-------   1 user user   9056 2011-10-13 22:21 .xsession-errors

but once I run:

@server01:~$ gedit

(gedit:4215): Gtk-WARNING **: cannot open display: 


@server01:~$ startx
X: user not authorized to run the X server, aborting.

^CInvalid MIT-MAGIC-COOKIE-1 keyxinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: unexpected signal 2

@server01:~$ firefox
Error: no display specified

any idea? txs

---

### Post by gruadp on 2011-10-20
check if your DISPLAY-variable is set after login in via ssh.  

# echo $DISPLAY
localhost:10.0

localhost:10.0 is very common after login in via ssh -X

you use the debuggig-switch of ssh  (-v or -vv or -vvv) to check for problems.


Not sure about running startx ?? what are you trying to achieve? imho X-server is started by root and always running on the local machine.  Only programs can then connect to this x-server from local or remote.

p

---

### Post by mancora on 2011-10-20
I omitted some output from the ssh authentication process, after it is done I pasted the outcome from the X11 negotiation but I am not sure what to look for, I really dont understand so good how does X works. But here is the outcome. After it none $DISPLAY is set.

I didnt know that startx only ran from the terminal, as you can see I am quite new in linux. I need to manage a GUI application remotely.

ssh -X -vvv user@host


debug1: Authentication succeeded (publickey).
Authenticated to host ([host]:22).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting [EMAIL="no-more-sessions@openssh.com"]no-more-sessions@openssh.com[/EMAIL]
debug1: Entering interactive session.
debug2: callback start
debug2: x11_get_proto: /usr/bin/xauth  list :0 2>/dev/null
debug1: Requesting X11 forwarding with authentication spoofing.
debug2: channel 0: request x11-req confirm 0
debug2: client_session2_setup: id 0
debug2: fd 3 setting TCP_NODELAY
debug3: packet_set_tos: set IP_TOS 0x10
debug2: channel 0: request pty-req confirm 1
debug1: Sending environment.
debug3: Ignored env ORBIT_SOCKETDIR
debug3: Ignored env SSH_AGENT_PID
debug3: Ignored env TERM
debug3: Ignored env SHELL
debug3: Ignored env XDG_SESSION_COOKIE
debug3: Ignored env WINDOWID
debug3: Ignored env GNOME_KEYRING_CONTROL
debug3: Ignored env GTK_MODULES
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env USERNAME
debug3: Ignored env DEFAULTS_PATH
debug3: Ignored env XDG_CONFIG_DIRS
debug3: Ignored env PATH
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env PWD
debug3: Ignored env GDM_KEYBOARD_LAYOUT
debug3: Ignored env GNOME_KEYRING_PID
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env GDM_LANG
debug3: Ignored env MANDATORY_PATH
debug3: Ignored env UBUNTU_MENUPROXY
debug3: Ignored env COMPIZ_CONFIG_PROFILE
debug3: Ignored env GDMSESSION
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env LANGUAGE
debug3: Ignored env GNOME_DESKTOP_SESSION_ID
debug3: Ignored env LOGNAME
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env LESSOPEN
debug3: Ignored env WINDOWPATH
debug3: Ignored env DISPLAY
debug3: Ignored env LESSCLOSE
debug3: Ignored env COLORTERM
debug3: Ignored env XAUTHORITY
debug3: Ignored env _
debug2: channel 0: request shell confirm 1
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-11-server x86_64)


@server01:~$ echo $DISPLAY
NOTHING
@server01:~$ echo $XAUTHORITY
NOTHING
@server01:~$

---

### Post by gruadp on 2011-10-20
do you have a DISPLAY where you start the ssh-connection???

usually its like this:

on my local machine I've a X-Server running and a terminal that has DISPLAY set.

$echo $DISPLAY
:0.0
$ssh -X [email]user@mymachine.com[/email]
...
ssh-output
...
$echo $DISPLAY
localhost:11.0
$xterm &

and then the xterminal is tunneled through ssh to my local X-server and displayed there.

Of course ssh can only tunnel ssh when it has a DISPLAY locally. Remotely the DISPLAY is set by ssh, but locally it has to be set before ssh is started. usually when you start a terminal in ubuntu it is started.

can you check?

---

### Post by mancora on 2011-10-20
Thanks for your fast reply.

I am running ubuntu 11.04 in my client as well on my server.

In the client I have :

$ echo $DISPLAY
:0

$ ssh -X -v user@host

Last login: Thu Oct 20 21:04:28 2011 from xxxxxx.com
@server01:~$ xterm &
[1] 5947
@server01:~$ xterm Xt error: Can't open display: 
xterm:  DISPLAY is not set

[1]+  Exit 1                  xterm

---

### Post by gruadp on 2011-10-20
dude thats odd :)

you can start a xterm from your local terminal?  I guess so cause DISPLAY is set.

I deal a lot with ssh here for many many years and I vaguely remember having a similar problem once but I can remember the details or the solution. Sorry.


Before I give up, lets check the basics again:

in /etc/ssh/sshd_config  on the remote machine you have the following two lines:

X11Forwarding yes
X11DisplayOffset 10

and you restarted the ssh-server after changing anything to the config:

#/etc/init.d/ssh restart
or for modern people:
#restart ssh


best,
p

---

### Post by mancora on 2011-10-21
Hi thanks for you patience.

$ xterm works on the client computer

in the config file /etc/ssh/sshd_config are as you mentioned:

X11Forwarding yes
X11DisplayOffset 10

no change on the outcome:

@server01:/etc/ssh$ xterm &
[1] 4237
@server01:/etc/ssh$ xterm Xt error: Can't open display: 
xterm:  DISPLAY is not set
^C
[1]+  Exit 1                  xterm


I think it has to do something with the permits to start the X session, but I don't know how to troubleshoot it.

---

### Post by mancora on 2011-10-25
Does anybody has further inside on the Authorization process from X11 in order to keep troubleshooting?

Txs.

---

### Post by bkline on 2012-08-08
Did you ever get any reply to your last appeal for assistance?  Or solve your problem somehow?

---

### Post by mancora on 2012-08-08
Unfortunately I never got a reply, the problem is that the machine that I am using is running as my house server and I dont have the time to do a complete re-installation. DO you have any inside on the possible problem?

Txs
Mancora

---

### Post by bkline on 2012-08-08
> **mancora said:**
> Unfortunately I never got a reply, the problem is that the machine that I am using is running as my house server and I dont have the time to do a complete re-installation. DO you have any inside on the possible problem?

Txs
Mancora

[I think you mean "insight."]  Unfortunately, no, sorry.  I'm wrestling with the same problem myself.  I am dealing with a server that exhibiting the same symptoms you describe, and I'm trying to find out what's different between it and all of the other servers I connect to, which don't give me any X display problems at all.  I'll post back if I stumble across any magic information.

---

### Post by mancora on 2012-08-08
Indeed the problem that I ran was that the documentation about it is really poor becuase is to high level and I dont get the full picture of how does X exactly work and been myself not an expert it is time consuming research. Good luck and I hope you get to solve your problem.
Cheers,
Mancora

---

### Post by bkline on 2012-08-08
Found it.  Had to change X11Forwarding from no to yes in /etc/ssh/sshd_config (thanks to the earlier post in this thread pointing this out).

---

### Post by RoeJice on 2012-09-13
> **mancora said:**
> 
debug2: x11_get_proto: /usr/bin/xauth  list :0 2>/dev/null



I was facing the same problem and found that my server was missing /usr/bin/xauth.  After installing the appropriate package, ssh invoked xauth to create a /root/.Xauthority.  and X forwarding started working.

=J

---

