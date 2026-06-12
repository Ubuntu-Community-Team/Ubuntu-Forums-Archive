---
title: "FreeNX can't download/install client (dependency)"
date: 2006-06-14
forum: General Help
---

### Post by unwoken on 2006-06-14
i posted this here: [http://www.ubuntuforums.org/showthread.php?t=156019&page=2](http://www.ubuntuforums.org/showthread.php?t=156019&page=2)  but i am not sure how many people will see it there.  basically what i wrote is this:

i can't download the freenx client (or the nx desktop) through synaptic because of dependency issues.

the message synaptic gives is below:

nxclient:
Depends: libstdc++2.10-glibc2.2 but it is not installable


i originally tried downloading the deb and the tar (no machine website), but had basically the same problem.

some details:
using dapper drake - fresh install
hp pavillion laptop

is there any way around this?  or another nx client i can download?

thanks for any help.

u.

---

### Post by treris on 2006-06-14
are you sure you have all of the required repositories?

anyway you could also just download the client from [http://www.nomachine.com/download_product.php?Prod_Id=10](http://www.nomachine.com/download_product.php?Prod_Id=10)

and then install it using the commandline 
by typing
sudo dpkg -i filename.deb

you shouldn't have any problems doing that, if it tells you you have missing dependencies of broken packages or anything like that just open synaptic and fix the situation using the fix broken packages utility

hope that helps

---

### Post by unwoken on 2006-06-14
thanks for the reply treris.

i clicked the link you posted, downloaded the deb and ran the command you
suggested.  what happened is below.


fireball@valhalla:~$ sudo dpkg -i /home/fireball/Desktop/nxclient_1.5.0-141_i386.deb
Password:
Selecting previously deselected package nxclient.
(Reading database ... 77274 files and directories currently installed.)
Unpacking nxclient (from .../nxclient_1.5.0-141_i386.deb) ...
dpkg: dependency problems prevent configuration of nxclient:
 nxclient depends on libstdc++2.10-glibc2.2; however:
  Package libstdc++2.10-glibc2.2 is not installed.
dpkg: error processing nxclient (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nxclient
fireball@valhalla:~$


i haven't used the fix broken packages utility yet.  i am not sure how to use it, but will give it a go now...

u.


EDIT: tried to find "libstdc++2.10-glibc2.2" but it doesn't seem to exist in synaptic?
EDIT: fixing broken packages seems to do nothing

---

### Post by jethro10 on 2006-06-14
I know this doesn't help, but I get the same problem.
Is anyone able to D/L and install the server/client of these and help us poor people out ? :sad: 

Jeff

---

### Post by treris on 2006-06-14
I actually have both the FreeNX server and the nomachine NX client installed and working, although I have to say I'm still working in breezy because I haven't had time to install dapper yet, but as far as I remember the client worked straight out of the box.

But if it's saying anything about missing dependencies I'd say install it using the commandline and then go into synaptic and go to
Edit ->Fix Broken Packages ->Apply 
and you should be all set
you could also try to find the libstdc++2.10-glibc2.2 package using synaptic (or adept or the commandline) and installing that prior to installing the nx client deb file

hope that works, if it does, please post it, if it doesn't obviously also please post

---

### Post by jethro10 on 2006-06-14
[QUOTE=treris]I actually have both the FreeNX server and the nomachine NX client installed and working, although I have to say I'm still working in breezy because I haven't had time to install dapper yet, but as far as I remember the client worked straight out of the box.

But if it's saying anything about missing dependencies I'd say install it using the commandline and then go into synaptic and go to
Edit ->Fix Broken Packages ->Apply 
and you should be all set
you could also try to find the libstdc++2.10-glibc2.2 package using synaptic (or adept or the commandline) and installing that prior to installing the nx client deb file

hope that works, if it does, please post it, if it doesn't obviously also please post[/QUOTE]
My problem ewas synaptic said it was already installed, so I deleted it and re-installed and still no luck.
J

---

### Post by unwoken on 2006-06-14
[QUOTE=treris]I actually have both the FreeNX server and the nomachine NX client installed and working, although I have to say I'm still working in breezy because I haven't had time to install dapper yet, but as far as I remember the client worked straight out of the box.

But if it's saying anything about missing dependencies I'd say install it using the commandline and then go into synaptic and go to
Edit ->Fix Broken Packages ->Apply 
and you should be all set
you could also try to find the libstdc++2.10-glibc2.2 package using synaptic (or adept or the commandline) and installing that prior to installing the nx client deb file

hope that works, if it does, please post it, if it doesn't obviously also please post[/QUOTE]


unfortunately libstdc++2.10-glibc2.2 is not in synaptic at all.  packages with similar names exist, but the package itself is not there.  the c++ libraries installed look like they are newer versions.....

i'm not sure what to enter into the commandline, but if you can give me some suggestions i will be happy to give it a go.

---

### Post by treris on 2006-06-14
okay now I'm really curious what's going on, but I don't really know what else I could tell you that might help

I'm getting the idea that the nx client from the nomachine site might not work under dapper yet, but as I said I'm still on breezy so I can't verify any of that, 

maybe somebody else has gotten the nomachine nx client to work with dapper yet??

---

### Post by unwoken on 2006-06-14
[QUOTE=treris]okay now I'm really curious what's going on, but I don't really know what else I could tell you that might help

I'm getting the idea that the nx client from the nomachine site might not work under dapper yet, but as I said I'm still on breezy so I can't verify any of that, 

maybe somebody else has gotten the nomachine nx client to work with dapper yet??[/QUOTE]

ok thanks treris.  i hope it can be sorted out.  hopefully somebody has already  got around this on dapper and can point the way...

---

### Post by treris on 2006-06-14
have you seen this thread yet??
[http://ubuntuforums.org/showthread.php?t=156019](http://ubuntuforums.org/showthread.php?t=156019)

---

### Post by unwoken on 2006-06-14
[QUOTE=treris]have you seen this thread yet??
[http://ubuntuforums.org/showthread.php?t=156019](http://ubuntuforums.org/showthread.php?t=156019)[/QUOTE]


i have.  the bit where it seems to go wrong is:

3) If running 'nxclient' from the console does not work, download it from [www.nomachine.com](www.nomachine.com).

i can't get nxclient to run, download (synaptic), or install (download from nomachine).  i do seem to have a script in /usr/lib/nx which is grey? and called nxclient, but synaptic says it is not installed, and i can't run it from the command line.  double clicking the file opens a tiny window called 'xmessage' which has nothing in it.

i am going to leave it for now.  it is way too late here.  i might see what i can do when i get up...

thks ;)

---

### Post by unwoken on 2006-06-16
ok.  i would really love some help on what is happening at the moment.

earlier i was on my desktop pc (which will be the server) and clicked on the nxclient package in synaptic.  To my surprise, it told me that it would install the offending file (listed earlier in this thread).

I wasn't exactly complaining, even though i had no idea why it was now available when it was not before.

The only problem which happened was that i had just installed the client on the server computer, so i loaded up the notebook expecting the same thing to happen... and find that it still will not install the nx client because it says there is a dependency problem and it needs a file which is not available (which i just installed on my desktop).

2 things:

1) both computers received a large number of upgrades today (~100 meg) before any of this happened.

2) apt sources list for both computers are identical

........

is there any explanation for the above?

can i somehow find the file which i just added to the desktop (via synaptic) and transfer it onto my notebook?  I attempted to do a search (through places menu) for it and failed...

anyone who can help me is an absolute legend! :)

cheers.

u.

---

