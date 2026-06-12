---
title: "Update manually ClamAV database"
date: 2012-03-19
forum: General Help
---

### Post by maceguo on 2012-03-19
Hi everyone, i'm trying to update manually the virus database of ClamAV application from a local directory but  i have problems to do it. I'm using Ubuntu 10.04.

i saved the virus database files *.cvd on **/var/lib/clamav** and i modified the source path to find the updated databases:

root@root: /etc/clamav# gedit freshclam.conf

```

# Automatically created by the clamav-freshclam postinst
# Comments will get lost when you reconfigure the clamav-freshclam package

DatabaseOwner clamav
UpdateLogFile /var/log/clamav/freshclam.log
LogVerbose false
LogSyslog false
LogFacility LOG_LOCAL6
LogFileMaxSize 0
LogTime true
Foreground false
Debug false
MaxAttempts 5
**DatabaseDirectory /var/lib/clamav**
DNSDatabaseInfo current.cvd.clamav.net
AllowSupplementaryGroups false
PidFile /var/run/clamav/freshclam.pid
ConnectTimeout 30
ReceiveTimeout 30
TestDatabases yes
ScriptedUpdates yes
CompressLocalDatabase no
Bytecode true
# Check for new database 24 times a day
Checks 24
**DatabaseMirror /var/lib/clamav**

```but when i run the command 'freshclam', i received this message:
[I]
ClamAV update process started at Mon Mar 19 13:16:37 2012
main.cvd is up to date (version: 54, sigs: 1044387, f-level: 60, builder: sven)
WARNING: Current functionality level = 58, recommended = 60
Please check if ClamAV tools are linked against the proper version of libclamav
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
WARNING: Can't get information about /var/lib/clamav: Name or service not known
WARNING: getpatch: Can't download daily-14665.cdiff from /var/lib/clamav
WARNING: Can't get information about /var/lib/clamav: Name or service not known
WARNING: getpatch: Can't download daily-14665.cdiff from /var/lib/clamav
WARNING: Can't get information about /var/lib/clamav: Name or service not known
WARNING: getpatch: Can't download daily-14665.cdiff from /var/lib/clamav
WARNING: Can't get information about /var/lib/clamav: Name or service not known
WARNING: getpatch: Can't download daily-14665.cdiff from /var/lib/clamav
ERROR: Can't get information about /var/lib/clamav: Name or service not known
ERROR: getpatch: Can't download daily-14665.cdiff from /var/lib/clamav
WARNING: Incremental update failed, trying to download daily.cvd
ERROR: Can't get information about /var/lib/clamav: Name or service not known
ERROR: Can't download daily.cvd from /var/lib/clamav
Giving up on /var/lib/clamav...
Update failed. Your network may be down or none of the mirrors listed in /etc/clamav/freshclam.conf is working. Check [http://www.clamav.net/support/mirror-problem](http://www.clamav.net/support/mirror-problem) for possible reasons.[/I]


why is tryning to download [I]daily-14665.cdiff? and how clamav can recognise the directory /var/lib/clamav to find the *.cvd files??
[/I][B][I]ERROR: Can't get information about /var/lib/clamav: Name or service not known
ERROR: Can't download daily.cvd from /var/lib/clamav[/I][/B]

any idea to fix this issue and update the database manually? Thanks

---

### Post by ajgreeny on 2012-03-19
I am pretty sure that when you install clamav it also installs freshclam and that is run at boot each time, or at least daily, so there should not be any reason to update manually.

Have I misunderstood what you are trying to do?

---

### Post by maceguo on 2012-03-19
ajgreeny thanks for your reply  and may be i expressed the wrong idea.
my idea is to download the update virus files as *.cvd from the clamav webpage and save it on a local directory.
Next, configure the freshclam.conf that take the new *.cvd files, that i saved on the local directory.
When the i run the command 'freshclam' to update the clamav application, it is not taking the database updates.
Because the pc doesn't have access to the internet so i would like to do it manually.

---

### Post by ajgreeny on 2012-03-19
OK.  I see what you want, but can't help, I'm afraid.

---

### Post by maceguo on 2012-03-20
any idea folks?

---

### Post by kidoruigenso on 2012-03-24
Maybe my experience can help you or give you an idea to solve your problem.

I have Ubuntu 10.04 LTS.
My version of ClamAV is 0.96.5+dfsg-1ubuntu1.10.04.3.
With this version of Ubuntu and ClamAV, the ClamAV virus databases are stored in:
/var/lib/clamav/

My problem in that the virus definition updates are not successfully downloaded from any of the mirror sites.  The response is (for example):
Ignoring mirror 194.47.250.218 (has connected too many times with an outdated version)

I think this is because the Ubuntu repository does not have the most current version of ClamAV.

As a work around, I collect the database files from the site:
[http://www.clamav.net/lang/en/](http://www.clamav.net/lang/en/)
At least I get daily.cvd and bytecode.cvd, as main.cvd seems to come once when you install ClamAV and remains valid for that version.

I copy these files into /var/lib/clamav/ using the command cp with sudo.

In my case, I then still connect to the internet and run the command
sudo freshclam -v

The program queries the ClamAV site current.cvd.clamav.net to get the current version number of the various virus databases.  For example at this moment, for daily.cvd the reply is:
daily.cvd version from DNS: 14698

But now the freshclam program sees that the version in /var/lib/clamav/ is current.  There is no need to download any incremental updates or a fresh copy of daily.cvd.

For you, the remaining problem may be that you can, or do not want to connect to the internet, and running freshclam with an internet connection may be absolutely required to actually update the virus definitions (i.e. freshclam may do more then simply download the newest .cvd files...it may also then process these .cvd files so that the information they contain is now usable by ClamAV when you request a scan).  I am not sure about this point, perhaps some other person can comment.

---

### Post by kidoruigenso on 2012-04-03
Again maceguo, maybe this experience will help you (or perhaps others): 

As stated in my last post to this thread, my problem in that the virus definition updates are not successfully  downloaded from any of the mirror sites.  The response when running the command 
sudo freshclam -v
from a terminal is (for example):
Ignoring mirror 194.47.250.218 (has connected too many times with an  outdated version).

Again, I have Ubuntu 10.04 LTS.  By enabling unsupported updates this problem is solved (at the expense of using now an unsupported version of ClamAV).  As a result I now have version 0.97.3+dfsg-1ubuntu0.11.04.1-lucid1.
With this version of Ubuntu and ClamAV, the ClamAV virus databases are still stored in:
/var/lib/clamav/.

To do this, one way is to open Synaptic Package Manager, select "Settings" -> "Repositories" -> the "Updates" tab -> and then enable "Unsupported updates (lucid-backports).  Close the Software Sources window and be sure to select "Reload" to reload the now changed latest package information.  On the next update you run you get now the newer and unsupported version of ClamAV and, for me, virus definition updates occur without any problems.  (Alternatively, you can now install the latest version using Synaptic Package Manager directly.)

---

