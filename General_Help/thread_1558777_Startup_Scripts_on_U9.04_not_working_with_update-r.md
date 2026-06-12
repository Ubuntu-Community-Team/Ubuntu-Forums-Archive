---
title: "Startup Scripts on U9.04 not working with update-rc.d"
date: 2010-08-22
forum: General Help
---

### Post by DaveLevy on 2010-08-22
I am trying to install a system V init script on Ubuntu 9.04. It doesn't seem to run.

There are a number of threads in the forums on this, but non solved and AFAIK, non with really a good problem definition.

_[SIZE=2]**Problem**[/SIZE]_

I have a manager script which takes the classic start|stop syntax and works from the command line. It invokes Java with the snipsnap class libraries. The initialisations script is called rc.snipsnap and invokes the manager script, using[INDENT][FONT=Courier New] su - ${USER} -c "${BINDIR}/snipsnapmgr.sh $* "[/FONT]
[/INDENT]I have used my script to install the rc?.d versions of the script which invokes.[INDENT][FONT=Courier New]update-rc.d -f rc.snipsnap remove
update-rc.d rc.snipsnap start 98 2 3 4 5 . stop 95 0 1 6 .
[/FONT][/INDENT]I originally get the 'LSB missing tags' warning, which points me at 

[http://wiki.debian.org/LSBInitScripts](http://wiki.debian.org/LSBInitScripts)

, so I have fixed that.

I run `find . -name "*rc.snipsnap*"` and get[INDENT][FONT=Courier New]./rc0.d/K95rc.snipsnap
./rc1.d/K95rc.snipsnap
./rc2.d/S98rc.snipsnap
./rc3.d/S98rc.snipsnap
./rc4.d/S98rc.snipsnap
./rc5.d/S98rc.snipsnap
./rc6.d/K95rc.snipsnap
[/FONT][/INDENT]The script doesn't seem to run. I have no log entries, the deamon start script should start several i.e. two. I have placed an echo >> into the script for diagnostic purposed and this log is not updated. It all works fine on the command line.

I then tried sysv-rc-conf, confirmed the 98/95 priorities and restarted. Still no diagnostics.

Other threads on the forums seem to point to upstart, although some poit to sysv-rc-conf and bum. I think now I have got to grips with update-rc.d, I'd prefer to stay there unless some one has a good reason to move on. 

Obviously if I need to move on to upstart then I will.

My scripts were written for the Cobalt Qube and do not use the startup function files and do not utilise the log managers functionality. The run from the command line after Ubuntu has booted.

_[SIZE=2]**Help**[/SIZE]_

So my questions are,

Have I done anything obvioulsy wrong for a standard sysV startup? Shall I put an echo into rc.local?

Do I need to rewrite the rc.snipsnap file to use the standard functions, if so where are they best documented other than the function file?

Where is Upstart documented? How do I write an upcast compliant script and install 
it? Is this the problem?

---

### Post by DaveLevy on 2010-08-28
Shame, no reply?

I plan to examine a post install trigger to see what they do?

Can anyone point me at pages in the support domain that might help me do this, or solve the original problem? See above. 

--
Dave

---

### Post by DaveLevy on 2010-09-01
This is now working as expected. The problem was in  the environement and the ${BINDIR}/snipsnapmgr.sh was failing.

So hoorah for Ubuntu, it was working and yet again it's user error not engineering failure.

I am a bit suspicious of a couple of things but with startup scripts, sh, bash etc, environments can be tricksy things. I'll write something longer and more communicative when I have more time and sobriety.

Till then, most people, that I have seen, on this forum complaining about startup scripts have made a mistake, and the answers are nothing to do with the startup script implementation. This now includes me! :) So if you are following me through this pain, have another look at your own code. This is what the forum suggested, although not explicitily i.e. because no-one was identifying problems and fixes for startup scripts, it was always some rubbish like below.

Lesson 2, if it had been fully LSBised, see [http://wiki.debian.org/LSBInitScripts](http://wiki.debian.org/LSBInitScripts) I would have found the error quicker; there were no logs to browse, although that too was a clue. 

I sorted this by looking at rc.local. i.e. I decided that I'd run the program by invoking it through rc.local, which does not get the LSB instruction argument i.e. start|stop etc. I inserted an echo which behaved as I expected, but the non use of a run mode made this deeply unattractive. Fortunately, the different boot sequence allowed me to observe the program failure.


Dave

My error was that the program doing the work ./snipsnapmgr.sh did not inherit the correct environment.

rc.snipsnap is bourne shell which has no shell rc file. Using the su - ${user} should in my book make the spawned shell behave as a login. The ${USER}'s login shell is bash which in my book means that .bash_profile and .bashrc should run. This should reset ${HOME} or is that a Berkley variable? Anyway snipsnapmgr.sh is a bourne shell as well. 

Actually /bin/sh is symbollically linked to /bin/dash. Sholdn't change the user startup scripts, but does explain why various syntax such as $() and case works. It is relevant to the shebanh as snipsnapmgr.sh is currently forced as #!/bin/sh.

One reason is that this is a port from a Cobalt Qube which had a brain dead bash afiak, also I was always taught to use bourne shell for admin utilities for speed and because more exotic shells were held in /usr/bin which might not be available while running startup scripts. Anyway, replacing the $HOME variable in the function file call, don't think bourne shell has an FPATH autoload feature , fixed the problem.

I hope someone finds this helpful. :o

---

### Post by meliniak on 2010-10-07
Thank you for sharing the solution, it was helpful in my case.

---

