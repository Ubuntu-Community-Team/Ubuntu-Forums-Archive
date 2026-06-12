---
title: "Ubuntu Lucid 10.04 xterm freezes/hangs"
date: 2011-07-30
forum: General Help
---

### Post by Pegasus-21- on 2011-07-30
I connect from my Ubuntu Lucid box to a Scientific Linux (rhel binary compatible distro) box,using ssh.The connection is for administration purposes,for which I run a bash script doing various stuff needed.Because I must do the same for a set of machines,I run the administration script through a loop in a wrapper script for all machines,executing it through xterm with the help of ssh.
i.e.:
```

for host in $hosts
do
   ssh root@$host "./admin.sh"
done

```

The problem is that for some unknown reason,xterm freezes. Using gnome-terminal,resulted in the same behavior. This happens only for 3 out of 13 hosts.All hosts are though identical (in hw and sw) and the script performs almost the same administration operations for all of them(install/update packages,(re)configure installed apps). The freezing happens almost always -only for the same 3 hosts,all the others produce no errors- ,but I wasn't able to find any variable condition which affects whether it happens or not. I have built xterm with debugging and tracing support,and the resulting files from xterm and gdb are appended to this post.

Relevant libraries versions (library names obtained from ldd):
```

XTerm(271)
libxft2          2.1.14-ubuntu1
libxaw7          2:1.0.7-1
libncurses5      5.7+20090803-2ubuntu3
libc6            2.11.1-0ubuntu7.8
libfontconfig1   2.8.0-2ubuntu1
libx11-6         2:1.3.2-1ubuntu3
libxt6           1:1.0.7-1
libxmu6          2:1.0.5-1
libice6          2:1.0.6-1
libfreetype6     2.3.11-1ubuntu2.4
libxrender1      1:0.9.5-1
libxext6         2:1.1.1-2
libxpm4          1:3.5.8-1
libz (zlib1g)    1:1.2.3.3.dfsg-15ubuntu1
libexpat1        2.0.1-7ubuntu1
libxcb1          1.5-2
libsm6           2:1.1.1-1
libxau6          1:1.0.5-1
libxdmcp6        1:1.0.3-1
libuuid1         2.17.2-0ubuntu1.10.04.2

```

Once frozen,I send a ctrl-c interrupt signal through keyboard to gdb,and backtrace.The following output is produced:
```

Program received signal SIGINT, Interrupt.
0x0012d422 in __kernel_vsyscall ()
(gdb) bt
#0  0x0012d422 in __kernel_vsyscall ()
#1  0x0029e93d in select () from /lib/tls/i686/cmov/libc.so.6
#2  0x0806451a in in_put (xw=<value optimized out>) at ./charproc.c:3699
#3  doinput (xw=<value optimized out>) at ./charproc.c:3731
#4  VTparse (xw=<value optimized out>) at ./charproc.c:3284
#5  0x08064a18 in VTRun (xw=0x80da050) at ./charproc.c:5443
#6  0x080739f8 in main (argc=0, argv=0xbffff714) at ./main.c:2442

```

The output trace files from xterm,are the following:
1) Trace-parent.out:
```

XTerm(271)
process 24533 real (1000/1000) effective (1000/1000)-- Sat Jul 30 07:17:06 2011
turn on/off: +132 off: -/+132 (turn on/off 80/132 column switching)
turn on/off: +ah off: -/+ah (turn on/off always highlight)
turn off/on: +ai on: -/+ai (turn off/on active icon)
turn on/off: +aw off: -/+aw (turn on/off auto wraparound)
turn on/off: +bc off: -/+bc (turn on/off text cursor blinking)
turn off/on: +bdc on: -/+bdc (turn off/on display of bold as color)
turn on/off: +cb on: -/+cb (turn on/off cut-to-beginning-of-line inhibit)
turn on/off: +cjk_width off: -/+cjk_width (turn on/off legacy CJK width convention)
turn off/on: +cm on: -/+cm (turn off/on ANSI color mode)
turn on/off: +cn on: -/+cn (turn on/off cut newline inhibit)
turn on/off: +cu off: -/+cu (turn on/off curses emulation)
turn off/on: +dc on: -/+dc (turn off/on dynamic color selection)
turn on/off: +fbb on: -/+fbb (turn on/off normal/bold font comparison inhibit)
turn off/on: +fbx on: -/+fbx (turn off/on linedrawing characters)
turn on/off: +fullscreen off: -/+fullscreen (turn on/off fullscreen on startup)
turn on/off: +hm off: -/+hm (turn on/off selection-color override)
turn on/off: +hold off: -/+hold (turn on/off logic that retains window after exit)
turn on/off: +ie off: -/+ie (turn on/off initialization of 'erase' from pty)
turn on/off: +im off: -/+im (turn on/off use insert mode for TERMCAP)
turn on/off: +j off: -/+j (turn on/off jump scroll)
turn on/off: +k8 off: -/+k8 (turn on/off C1-printable classification)
turn on/off: +l off: -/+l (turn on/off logging (not supported))
turn on/off: +lc off: -/+lc (turn on/off locale mode using luit)
turn on/off: +ls off: -/+ls (turn on/off login shell)
turn on/off: +maximized off: -/+maximized (turn on/off maxmize on startup)
turn on/off: +mb off: -/+mb (turn on/off margin bell)
turn off/on: +mesg on: -/+mesg (turn off/on forbid/allow messages)
turn on/off: +mk_width off: -/+mk_width (turn on/off simple width convention)
turn off/on: +nul on: -/+nul (turn off/on display of underlining)
turn on/off: +pc off: -/+pc (turn on/off PC-style bold colors)
turn on/off: +pob off: -/+pob (turn on/off pop on bell)
turn on/off: +rv off: -/+rv (turn on/off reverse video)
turn off/on: +rvc on: -/+rvc (turn off/on display of reverse as color)
turn on/off: +rw off: -/+rw (turn on/off reverse wraparound)
turn on/off: +s off: -/+s (turn on/off multiscroll)
turn on/off: +samename off: -/+samename (turn on/off the no-flicker option for title and icon name)
turn on/off: +sb off: -/+sb (turn on/off scrollbar)
turn on/off: +sf off: -/+sf (turn on/off Sun Function Key escape codes)
turn on/off: +si on: -/+si (turn on/off scroll-on-tty-output inhibit)
turn on/off: +sk off: -/+sk (turn on/off scroll-on-keypress)
turn on/off: +sm off: -/+sm (turn on/off the session-management support)
turn on/off: +sp off: -/+sp (turn on/off Sun/PC Function/Keypad mapping)
turn on/off: +t off: -/+t (turn on/off Tek emulation window)
turn on/off: +u8 0: -/+u8 (turn on/off UTF-8 mode (implies wide-characters))
turn on/off: +uc off: -/+uc (turn on/off underline cursor)
turn off/on: +ulc on: -/+ulc (turn off/on display of underline as color)
turn off/on: +ulit on: -/+ulit (turn off/on display of underline as italics)
turn on/off: +ut off: -/+ut (turn on/off utmp support)
turn on/off: +vb off: -/+vb (turn on/off visual bell)
turn on/off: +wc off: -/+wc (turn on/off wide-character mode)
turn on/off: +wf off: -/+wf (turn on/off wait for map before command exec)
Checking options-tables for inconsistencies:
Options listed in help, not found in resource list:
  -C                          
  -Sccn                       
  -bd color                    (standard)
  -bg color                    (standard)
  -bw number                   (standard)
  -display displayname         (standard)
  -fg color                    (standard)
  -fn fontname                 (standard)
  -iconic                      (standard)
  -name string                 (standard)
  -title string                (standard)
  -xrm resourcestring          (standard)
Resource list items not found in options-help:
  +kt
  +r
  -en
  -hc
  -r
  -w
Resource list items that will be ignored by XtOpenApplication:
  -class                       {param}
  -e                           {remainder of line}
  -help                        {0 params}
  -into                        {param}
  -version                     {0 params}
Before XtOpenApplication:
  0:./xterm
  1:-version
parsing -version

```

2) Trace-child.out
```

XTerm(271)
process 24101 real (1000/1000) effective (1000/1000)-- Sat Jul 30 06:16:35 2011
process 24101 real (1000/1000) effective (1000/1000) (./main.c@2627)
process 24101 real (1000/1000) effective (1000/1000) (./main.c@2937)
set_owner(/dev/pts/20, uid=1000, gid=5, mode=0620
check if we should set erase to 127:NO
	ptyInitialErase:1,
	overide_tty_modes:0,
	XTTYMODE_erase:0
xtermSetenv(TERM=xterm)
xtermSetenv(WINDOWID=73400354)
xtermSetenv(DISPLAY=localhost:10.0)
xtermSetenv(XTERM_VERSION=XTerm(271))
xtermEnvLocale ->en_US.UTF-8
xtermSetenv(XTERM_LOCALE=en_US.UTF-8)
xtermSetenv(XTERM_PARENT=24097)
xtermSetenv(XTERM_CHILD=24101)
xtermSetenv(LOGNAME=dfiore)
my_pty_name(/dev/pts/20) -> 'pts/20'
my_utmp_id (/dev/pts/20) -> 'p20'
my_pty_name(/dev/pts/20) -> 'pts/20'
getutid: pid=11083 type=8 user=dfiore line=pts/20 id=p20
my_pty_name(/dev/pts/20) -> 'pts/20'
my_utmp_id (/dev/pts/20) -> 'p20'
my_pty_name(/dev/pts/20) -> 'pts/20'
DisplayString(localhost:10.0)
pututline: id p20, line pts/20, pid 24101, errno 13 Permission denied
handshake writing UTMP_ADDED errno=0, error=0 device "/dev/pts/20"
process 24101 real (1000/1000) effective (1000/1000) (./main.c@4259)
process 24101 real (1000/1000) effective (1000/1000) (./main.c@4271)
handshake writing PTY_GOOD errno=0, error=0 device "/dev/pts/20"
xtermSetenv(XTERM_SHELL=/bin/bash)
shell path '/bin/bash' leaf 'bash'

```

Hopefully,I provided all the relevant info needed.

P.S.: Since I actually run xterm on the Ubuntu machine,I suppose that this is where I should ask for help.If not,I would be glad to be pointed to the right direction.

---

### Post by itcotbtoemik on 2011-08-02
The gdb walkback seems to offer the only clue: xterm has started, and is trying to read from the pty.  If I were debugging this, I'd be curious whether it's getting any data at all, or whether it chokes after a while.  xterm's two processes - the parent which does most of the work (including the part that gdb's showing).  The child seems to have done its work.

---

