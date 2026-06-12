---
title: "gedit-No protocol specified..Problem while installing oracle 11g"
date: 2012-03-11
forum: General Help
---

### Post by ale_ramesh on 2012-03-11
Hi Everyone,

I am following this [link]("http://oracle.su/docs/11g/install.112/e10857/toc.htm#CEGEGDBA") to install Oracle 11gR2 on ubuntu 11.10

Instructions given :

> To set the oracle user's environment:

1. Start a new terminal session, for example, an X terminal (xterm).

2. Enter the following command to ensure that X Window applications can display on this system:

$ xhost fully_qualified_remote_host_name
For example:

$ xhost somehost.us.example.com
3. Complete one of the following steps:

If the terminal session is not connected to the system where you want to install the software, then log in to that system as the oracle user.

If the terminal session is connected to the system where you want to install the software, then switch user to oracle:

$ su - oracle
4. To determine the default shell for the oracle user, enter the following command:

$ echo $SHELL
5. Open the oracle user's shell startup file in any text editor:

Bash shell (bash) on SUSE:

$ vi .profile
Bourne shell (sh), Bash shell on Red Hat (bash), or Korn shell (ksh):

$ vi .bash_profile
C shell (csh or tcsh):

% vi .login


1) As i am trying to install linux on my own laptop i ignored the points 1,2 and typed the command ```
su - oracle
``` in the terminal -- Please confirm if that is wrong?

2)  If my previous step is correct, As mentioned in the 5th point,i tried to edit the .bash_profile using gedit(as i am not comfortable with vi editor)..But i am getting the error :

[IMG]http://i44.tinypic.com/2co6ejk.png[/IMG]

> No protocol specified
Cannot open display:

Please help me in resolving this issue..

I am finding very hard time in installing oracle on Ubuntu

---

### Post by 2F4U on 2012-03-11
If you are not comfortable with vi you can use nano. It behaves much more like other editors and I think it is installed by default.

---

### Post by ale_ramesh on 2012-03-11
> **2F4U said:**
> If you are not comfortable with vi you can use nano. It behaves much more like other editors and I think it is installed by default.

As you said i tried nano editor, now i am getting the error as permission denied..

[IMG]http://i39.tinypic.com/kcgqw0.png[/IMG]

[IMG]http://i42.tinypic.com/mlh27p.png[/IMG]

Tried with sudo command but it says "oracle is not in the sudoers file.  This incident will be reported."

[IMG]http://i39.tinypic.com/1035pnl.png[/IMG]

---

### Post by ale_ramesh on 2012-03-13
Any suggestions guys??

---

### Post by linas on 2012-05-07
This has nothing to do with oracle, or editing, for me; its a generic problem:  I get this for anything started from a tty:

export DISPLAY=:0
xdpyinfo
No protocol specified
unable to open display ":0"

trying this with :1 or :2, etc. is as above, but *without* the "No protocol specified" error.

---

### Post by linas on 2012-05-07
:confused:

Above report is with Oneiric

I am now able to hack around it, like so:

rm /home/me/.Xauthority
ln -s /var/run/gdm/auth-for-me-whatever/database /home/me/.Xauthority

which is such an ugly hack ... I don't understand why I need to do this ... 

I've had to do this every time I've logged into oneiric (which is twice, now, since installing it.  I just forgot that this was the workin-around from the first time).

---

