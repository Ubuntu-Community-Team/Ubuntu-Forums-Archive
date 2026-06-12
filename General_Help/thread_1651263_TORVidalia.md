---
title: "TOR/Vidalia"
date: 2010-12-22
forum: General Help
---

### Post by robbiemacg on 2010-12-22
Hi,
I want to use Vidalia to manage a TOR relay.
My **/etc/default/tor** file references another file **/etc/default/tor.vidalia**. It's supposed to help manage the TOR daemon.
For whatever reason, I don't have a file called **/etc/default/tor.vidalia**.
Do you? 
Could you please less your **/etc/default/tor.vidalia** and copy the code below?

Thanks,
Robbie

---

### Post by robbiemacg on 2010-12-23
Good morning all,
This is a bump. Anyone able to help with this simple request before work today?

Thanks again,
R.

---

### Post by jim_deadlock on 2010-12-23
I use vidalia with tor and I have no /etc/default/tor.vidalia file. I have /etc/default/tor:

```
# Defaults for tor initscript
# sourced by /etc/init.d/tor
# installed at /etc/default/tor by the maintainer scripts

#
# This is a bash shell fragment
#
RUN_DAEMON="yes"

#
# Servers sometimes may need more than the default 1024 file descriptors
# if they are very busy and have many clients connected to them.  The top
# servers as of early 2008 regularly have more than 10000 connected
# clients.
#  (ulimit -n)
#
# (the default varies as it depends on the number of available system-wide file
#  descriptors.  See the init script in /etc/init.d/tor for details.)
#
# MAX_FILEDESCRIPTORS=

#
# If tor is seriously hogging your CPU, taking away too much cycles from
# other system resources, then you can renice tor.  See nice(1) for a
# bit more information.  Another way to limit the CPU usage of an Onion
# Router is to set a lower BandwidthRate, as CPU usage is mostly a function
# of the amount of traffic flowing through your node.  Consult the torrc(5)
# manual page for more information on setting BandwidthRate.
#
# NICE="--nicelevel 5"

# Additional arguments to pass on tor's command line.
#
# ARGS=""

#
# Uncomment the ulimit call below if you want tor to produce coredumps on
# segfaults and assert errors.
#
# Keeping coredumps around is some sort of security issue since they
# may leak session keys, sensitive client data and more, should such
# files fall into the wrong hands.  Therefore coredumps are not enabled
# by default.
#
# ulimit -c unlimited

#
# Config option for the weekly cron file: Whether or not to remove old
# coredumps in /var/lib/tor.  Coredumps can hold sensitive data, as such
# they probably should not be kept lying around if nobody will ever look
# at them.  This option makes /etc/cron.weekly/tor clean out files older
# then three weeks.
#
CLEANUP_OLD_COREFILES=y

# Let the vidalia package override some of our settings.
# People who have vidalia installed might not want to run Tor as a system
# service. The vidalia .deb can ask them that and then set run-daemon to no.
if [ -e /etc/default/tor.vidalia ] && [ -x /usr/bin/vidalia ]; then
    . /etc/default/tor.vidalia
fi
```

... and /etc/tor/torrc which has only 2 uncommented lines:

```
SocksPort 9050 # what port to open for local application connections
SocksListenAddress 127.0.0.1 # accept connections only from localhost
```

---

### Post by robbiemacg on 2010-12-23
You don't have one either, hey? Hmmm. Weird. I'm sure you noted that the last part of your **/etc/default/tor** file also reads:
```
# Let the vidalia package override some of our settings.
# People who have vidalia installed might not want to run Tor as a system
# service. The vidalia .deb can ask them that and then set run-daemon to no.
if [ -e /etc/default/tor.vidalia ] && [ -x /usr/bin/vidalia ]; then
    . /etc/default/tor.vidalia
fi
```Does anybody have a file labeled **/etc/default/tor.vidalia** or am I just chasing after something that doesn't exist? (I could always write one I guess.)

> **jim_deadlock said:**
> I use vidalia with tor and I have no /etc/default/tor.vidalia file. I have /etc/default/tor:

```
# Defaults for tor initscript
# sourced by /etc/init.d/tor
# installed at /etc/default/tor by the maintainer scripts

#
# This is a bash shell fragment
#
RUN_DAEMON="yes"

#
# Servers sometimes may need more than the default 1024 file descriptors
# if they are very busy and have many clients connected to them.  The top
# servers as of early 2008 regularly have more than 10000 connected
# clients.
#  (ulimit -n)
#
# (the default varies as it depends on the number of available system-wide file
#  descriptors.  See the init script in /etc/init.d/tor for details.)
#
# MAX_FILEDESCRIPTORS=

#
# If tor is seriously hogging your CPU, taking away too much cycles from
# other system resources, then you can renice tor.  See nice(1) for a
# bit more information.  Another way to limit the CPU usage of an Onion
# Router is to set a lower BandwidthRate, as CPU usage is mostly a function
# of the amount of traffic flowing through your node.  Consult the torrc(5)
# manual page for more information on setting BandwidthRate.
#
# NICE="--nicelevel 5"

# Additional arguments to pass on tor's command line.
#
# ARGS=""

#
# Uncomment the ulimit call below if you want tor to produce coredumps on
# segfaults and assert errors.
#
# Keeping coredumps around is some sort of security issue since they
# may leak session keys, sensitive client data and more, should such
# files fall into the wrong hands.  Therefore coredumps are not enabled
# by default.
#
# ulimit -c unlimited

#
# Config option for the weekly cron file: Whether or not to remove old
# coredumps in /var/lib/tor.  Coredumps can hold sensitive data, as such
# they probably should not be kept lying around if nobody will ever look
# at them.  This option makes /etc/cron.weekly/tor clean out files older
# then three weeks.
#
CLEANUP_OLD_COREFILES=y

# Let the vidalia package override some of our settings.
# People who have vidalia installed might not want to run Tor as a system
# service. The vidalia .deb can ask them that and then set run-daemon to no.
if [ -e /etc/default/tor.vidalia ] && [ -x /usr/bin/vidalia ]; then
    . /etc/default/tor.vidalia
fi
```... and /etc/tor/torrc which has only 2 uncommented lines:

```
SocksPort 9050 # what port to open for local application connections
SocksListenAddress 127.0.0.1 # accept connections only from localhost
```

---

### Post by jim_deadlock on 2010-12-24
I think that file is for custom settings that you want to add, but by default there are none.

---

### Post by robbiemacg on 2010-12-24
I had considered this possibility, however, this still wouldn't explain why, having selected the option of allowing Vidalia to disable TOR at boot (attached screenshot), it fails to do so.

As I understand it selecting this option should have resulted in the creation of a file  "/etc/default/tor.vidalia," set into motion processes to manage the TOR daemon, switch RUN_DAEMON="no," whatever.
Having looked at some of the project documentation, I guess selecting that option should technically have executed the following processes?

```
invoke-rc.d --force tor stop
ucf --debconf-ok --three-way /usr/share/vidalia/default.tor-off
/etc/default/tor.vidalia

```> **jim_deadlock said:**
> I think that file is for custom settings that you want to add, but by default there are none.

---

### Post by jim_deadlock on 2010-12-24
I don't use Vidalia much so I forgot about this problem. What happens is that by default Tor starts itself under user "debian-t" and because of this Vidalia finds it already running and won't restart. The quick and dirty fix is:

```
sudo service tor stop
```

After that Vidalia will happily restart Tor under its own username "proxy"

For a permanent fix I suggest you install "bum" (BootUp-Manager) from the repository, then find tor on your bootup services list and disable it (hit the Apply button at the bottom). After that Vidalia will fire up Tor nicely on startup and then you can easily configure your relay settings from Vidalia.

I still don't have a file called /etc/default/tor.vidalia even when running as a relay. I think you may be running an older version of Vidalia because the latest version 0.2.10 (which I installed from the repository) shows a graphical option dialog rather than the pseudo-graphical one shown in your screenshot.

Also, I commend you for running a relay but if you're running an exit node I suggest you read through this first:

[http://www.torproject.org/docs/faq-abuse.html.en#TypicalAbuses](http://www.torproject.org/docs/faq-abuse.html.en#TypicalAbuses)

---

### Post by robbiemacg on 2010-12-24
Many thanks, [jim_deadlock]("http://ubuntuforums.org/member.php?u=1108068"). I appreciate your attention/advice.
I think I'm just going to alter my **/etc/default/tor **to prevent the daemon from running, add Vidalia to my start up apps. I think that'd have a similar effect to the method you're suggesting.
Thanks also for linking the TOR FAQ. I'll check it out.

R.

*p.s. Screenshot is not from my machine, it's a found image showing the available options. I'm running 0.2.10

---

### Post by robbiemacg on 2010-12-25
After exchanging a couple of messages with other forum members, I decided to create an /etc/default.tor.vidalia file that looked like this:
```
if [ -x /usr/bin/vidalia ]; then
        RUN_DAEMON=no
fi
```I then set Vidalia to run at start up. Things appear to be running smoothly, I'm satisfied with this solution.  
Thanks to all for your help, and a big high five to [Agent24]("http://ubuntuforums.org/member.php?u=214665") for being community-minded and cool!

---

