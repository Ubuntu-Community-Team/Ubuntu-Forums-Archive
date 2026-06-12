---
title: "Remote User Login for GDM over SSH"
date: 2010-08-03
forum: General Help
---

### Post by bigben1313 on 2010-08-03
I have a remote computer (A) running Ubuntu 10.04 that I can ssh to from my windows computer (B).  I use TightVNC over ssh to access my remote desktop (A).  Occasionally I will need/want to restart computer A using computer B.  I can reboot using ssh (sudo reboot now), but after reboot I can no longer use VNC because computer A is stuck on the GDM login screen.  I need to be able to login to GDM as a user on computer A from computer B.

Limitations:
1. I do not want to use auto-login.
2. Computer B is on Windows, so forwarding X will be a bit more complicated and I haven't been able to figure this out to get to the login screen.

Ideas (that I haven't been able to get working)
1. Is there a way to login to GDM using the ssh terminal?  I.e., a command line option to bypass the graphical login screen for GDM.  Once GDM loads I could then use VNC.
2. Let a VNC see the login screen and enter my GDM username and password though VNC.  I have seen general references to doing this by forwarding X, but I haven't seen any specific directions for doing this with Windows.

Any help would be much appreciated.

---

### Post by mexicanseaf00d on 2010-08-03
my GDM also gets stuck when doing 'remote reboot'. Because I'm a noob, I dont now where to look for error messages etc

---

### Post by anglican on 2010-08-03
> **bigben1313 said:**
> I have a remote computer (A) running Ubuntu 10.04 that I can ssh to from my windows computer (B).  I use TightVNC over ssh to access my remote desktop (A).  Occasionally I will need/want to restart computer A using computer B.  I can reboot using ssh (sudo reboot now), but after reboot I can no longer use VNC because computer A is stuck on the GDM login screen.  I need to be able to login to GDM as a user on computer A from computer B.

Limitations:
1. I do not want to use auto-login.
2. Computer B is on Windows, so forwarding X will be a bit more complicated and I haven't been able to figure this out to get to the login screen.

Ideas (that I haven't been able to get working)
1. Is there a way to login to GDM using the ssh terminal?  I.e., a command line option to bypass the graphical login screen for GDM.  Once GDM loads I could then use VNC.
2. Let a VNC see the login screen and enter my GDM username and password though VNC.  I have seen general references to doing this by forwarding X, but I haven't seen any specific directions for doing this with Windows.

Any help would be much appreciated.This works for me:

1) Login via ssh:
```
ssh -L5900:localhost:5900 username@remotehost
```2) On the remotehost use sudo to run x11vnc:
```
sudo x11vnc -ncache 10 -display :0 -usepw -q
```You should see something like (in the ssh terminal):
> The VNC desktop is:      remotehost:0
PORT=59003) Run the vncviewer on your localhost and connect to "localhost:0" which should then show you the gdm login screen. You can login and use remotehost as normal.

Sorry: just noticed that your local computer is windows. You need to install "putty" (from [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)) on the windows computer then set up a tunnel in putty. In the SSH->Tunnels menu enter 5900 as "Source port" and "localhost:5900" as destination port then click on "Add". You may need to check the "Local ports accept connections from other hosts" box - I don't use Windows so I'm not sure on that - try it either way.
H

---

### Post by bigben1313 on 2010-08-04
Success!  Thanks for the help.  The problem (I think) was that I was using the remote desktop option that comes with Ubuntu and not x11vnc.  I already had the ssh working, but I couldn't connect to the pre-installed remote desktop until login.  x11vnc works great!

Thanks again!

---

### Post by anglican on 2010-08-06
> **bigben1313 said:**
> Success!  Thanks for the help.  The problem (I think) was that I was using the remote desktop option that comes with Ubuntu and not x11vnc.  I already had the ssh working, but I couldn't connect to the pre-installed remote desktop until login.  x11vnc works great!

Thanks again!That's great, glad it works now. I should have added that it is only necessary to "sudo" the x11vnc command if you're not already logged in on the remote computer i.e. to get a login screen rather than a desktop.

H

---

### Post by alexwagner on 2010-10-06
I've googled for hours and this thread is the closest I've seen to addressing my problem.  I'm in roughly the same situation as the OP, but I have some additional constraints that make the given solution unusable. :-(

1- I have to use a specific custom VNC-derivative (Axeda Desktop Server, but I don't think the details of this particular one is so important, other than that I can't use x11vnc).

2- I can't install anything new on this machine.  Well, I can, but I can't put anything in /etc, /usr, /bin, and so on.  I have a directory I'm allowed to put stuff in, but I can't modify anything outside of my given location.  (I mean, I *can*; I do have root access, but I'm not "allowed" for reasons I can't explain very easily.)

3- This is actually a Debian machine, but I'm hoping it's similar enough to Ubuntu that I can find help here.

I basically need to be able to ssh into the machine while it's sitting there at the login screen and force it to log in to a desktop so I can start up this custom VNC server.  If I happened to already be logged into the machine in GDM, it's not a problem; I just preface the startup command for the VNC server with "DISPLAY=:0" in my ssh terminal and it works just fine.  But until you're logged in, you can't do anything with :0.

---

### Post by anglican on 2010-10-06
> **alexwagner said:**
> I've googled for hours and this thread is the closest I've seen to addressing my problem.  I'm in roughly the same situation as the OP, but I have some additional constraints that make the given solution unusable. :-(

1- I have to use a specific custom VNC-derivative (Axeda Desktop Server, but I don't think the details of this particular one is so important, other than that I can't use x11vnc).I'm not familiar with Axeda Desktop Server so I can't help much with that. x11vnc can additionally set an X authority file using the command line option -auth so you can run it something like:
```
x11vnc -ncache 10 -display :0 -usepw -q -auth /var/gdm/:0.Xauth
```Axeda may have some similar option - you'll have to look in the documentation.

> **alexwagner said:**
> 2- I can't install anything new on this machine.  Well, I can, but I can't put anything in /etc, /usr, /bin, and so on.  I have a directory I'm allowed to put stuff in, but I can't modify anything outside of my given location.  (I mean, I *can*; I do have root access, but I'm not "allowed" for reasons I can't explain very easily.)Well x11vnc doesn't have to be installed in any of those directories, you can easily put it in your allowed location. Debian packages are just ar archives so you can extract them with:
```
ar vx mypackage.deb
```to get the three components debian-binary, control.tar.gz, data.tar.gz. Then extract files with:
```
tar -xzvf data.tar.gz
```> **alexwagner said:**
> 3- This is actually a Debian machine, but I'm hoping it's similar enough to Ubuntu that I can find help here.

I basically need to be able to ssh into the machine while it's sitting there at the login screen and force it to log in to a desktop so I can start up this custom VNC server.  If I happened to already be logged into the machine in GDM, it's not a problem; I just preface the startup command for the VNC server with "DISPLAY=:0" in my ssh terminal and it works just fine.  But until you're logged in, you can't do anything with :0.Debian is indeed so close to ubuntu that answers should generally work for both.

H

---

### Post by HermanAB on 2010-10-06
The other way is to install Cygwin on Windows and be sure to include X and Openssh-server and client. Then do:
$ ssh -X -C -c blowfish user@linuxserver gnome-panel

The result is a remote gnome panel on your Windows desktop and you can then go click happy.  All remote Linux applications will then run transparently on the local Windows desktop.

---

### Post by meoconvn38 on 2010-10-06
Why not using FREENX and setting for the ssh initd not require login:KS

---

### Post by alexwagner on 2010-10-06
anglican--

Thanks for your response.  I apologize for not being clearer about my constraints; I'm stuck with Axeda Desktop Server.  What I'd said about not being able to install anything was more directed at any *other* proposed solutions, if there was some utility out there that could help.  I can't install x11vnc, or if I did install it, I can't use it.

This is actually pretty frustrating... it seems like this ought to be a pretty easy thing to do.

I have a follow-up question that's tangentially related to this one.  I can start new xsessions and switch around with alt-F7, alt-F8, and so on.  If I open a terminal in any of these and try to find out what $DISPLAY is, it'll tell me a different thing depending on which one I'm in, e.g., ":0.0", ":2.0"... this makes perfect sense.  But obviously, only one display is active at any given time, right?  So how do I ask my system what it's currently displaying on my actual physical screen if I'm SSHing in from the outside?  And is there a way to force it to switch to a particular display?

And the follow-up to the follow-up is, if you know the answer to that, where did you learn it?

HermanAB--

That actually sounds pretty cool, and I'm definitely going to try it just for fun!  But unfortunately, I'm kind of stuck with my current constraints.  I'm expected to use Axeda Desktop Server.  The actual details of ADS aren't really important... if someone can get me to the point where I am able to log into GDM on the machine itself by SSHing in from the outside, I can take care of the rest myself.

meoconvn38--

I'm thinking this would violate my constraints in multiple ways.  I can't change how this machine starts up, other than that I'm given a "hook" of sorts... somewhere late in the boot-up sequence, there will be something that calls any one script of my choosing, but the expectation is that my script won't do anything terribly intrusive; it *especially* can't change /etc in any way.  After it has booted, all I have to work with is what I can do over an SSH session over PuTTY, and preferably without any X11 forwarding.

---

### Post by alexwagner on 2010-10-06
Here's what I have now:

I copied /usr/share/gdm/defaults.conf to another location that I have control over and modified it to use automatic login:

```
...
[daemon]
AutomaticLoginEnable=true
AutomaticLogin=YOUR_LOGIN_HERE
...
```

Then, I copied /etc/init.d/gdm to another location I can control, and hacked it up to get only the stop and start pieces.  It doesn't need to handle "start" or "stop" arguments any more because to won't be part of the rcX.d setup; I'll only call it from my remote SSH session.

```
#!/bin/bash
set -o errexit

PATH=/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/gdm
CONFIG=/YOUR/CUSTOM/GDM/CONFIG/FILE.conf

test -x $DAEMON || exit 0

if [ -r /etc/default/locale ]; then
    source /etc/default/locale
    export LANG LANGUAGE
fi

source /lib/lsb/init-functions


# Stop GDM, as would be done in /etc/init.d/gdm
# ---------------------------------------------
log_daemon_msg "Stopping GNOME Display Manager" "gdm"
set +o errexit
start-stop-daemon --stop --quiet --pidfile /var/run/gdm.pid \
        --name gdm --retry 5
set -o errexit
log_end_msg $?

# Start GDM, but have it use a custom config file, so that
# autologin is turned on for root
# --------------------------------------------------------
log_daemon_msg "Starting GNOME Display Manager" "gdm"
start_daemon $DAEMON --config $CONFIG
log_end_msg $?

exit 0
```

So, now, I can just run this script, and it'll start gdm with a custom configuration that causes it to log in automatically.  From there, I can start Axeda Desktop Server remotely (making sure DISPLAY is set to :0.0 before starting it), and it works fine.  Problem solved....

Well... no, it's not quite solved.  :-(  There's still one huge problem.

I didn't explain one of my constraints very well.  This computer is intended to be embedded into a medical device, and it has a highly-customized version of Debian 5.0 on it.  One of the customizations is that most of the filesystem is mounted read-only, to prevent tampering (apparently, or something like that), including the /etc directory.  It's actually worse than just being read-only, it's a union mount from a number of different places.  The only user that can be logged in right now is root, and no more can be added, because /etc/passwd is part of the read-only filesystem.  I can actually hack this by remounting it read-write, but I can't do this for the final product.  

The kicker is that **gdm does not allow you to use root as the account to be automatically logged in.**

Any ideas?  Please?  *makes an extremely sad face*

But at least if someone else runs into the same problem up to but not including having to use root, then this should work.

(I don't feel like debating how dangerous and/or stupid it is to only have root available to log in with.  I tend to agree, but it's out of my hands.)

---

