---
title: "Transmission-daemon blocklist???"
date: 2010-05-25
forum: General Help
---

### Post by EvilTchnlgy on 2010-05-25
I installed transmission-daemon on my 10.04 server install and got it all setup like I like it with the web interface. I'm trying to get blocklists activated now.
I changed the variable in settings.json to turn the blocklist on. The outdated directions direct you to make a shell script with the following
```
#!/bin/sh

PID="`pidof transmission-daemon`"
if [ -n "$PID" ]; then
        kill $PID
fi

echo -n "Waiting for the daemon to exit "
sleep 2

COUNT=1
while [ -n "`pidof transmission-daemon`" ]; do
        COUNT=$((COUNT + 1))
        if [ $COUNT -gt 60 ]; then
                echo -n "transmission-daemon doesn't respond, killing it with -9"
                kill -9 `pidof transmission-daemon`
                break
        fi

        sleep 2
        echo -n "."
done

echo " done"

cd $HOME/.config/transmission-daemon/blocklists/
if wget http://www.bluetack.co.uk/config/level1.gz 1>/dev/null 2>&1 ; then
        rm -f level1 && gunzip level1.gz
        echo "blocklist updated"
else
        echo "blocklist not updated"
fi

transmission-daemon
```

I went ahead and modified it a little, but I am at a loss to where I will be saving my blocklist. I installed transmission daemon as root and there is one other user that has a home directory. There isn't a .config folder in either /root or /home/user ... My guess was that it goes in /var/lib/transmission-daemon/blocklists but I'm not sure how I'll know if it is actually loading up the blocklists!
Here is my modified script
```
#!/bin/sh

PID="`pidof transmission-daemon`"
if [ -n "$PID" ]; then
        sudo service transmission-daemon stop
fi

echo -n "Waiting for the daemon to exit "
sleep 2

COUNT=1
while [ -n "`pidof transmission-daemon`" ]; do
        COUNT=$((COUNT + 1))
        if [ $COUNT -gt 60 ]; then
                echo -n "transmission-daemon doesn't respond, killing it with -9"
                kill -9 `pidof transmission-daemon`
                break
        fi

        sleep 2
        echo -n "."
done

echo " done"

cd $HOME/.config/transmission-daemon/blocklists/
if wget http://update.transmissionbt.com/level1.gz 1>/dev/null 2>&1 ; then
        rm -f level1 && gunzip level1.gz
        echo "blocklist updated"
else
        echo "blocklist not updated"
fi

sudo service transmission-daemon reload


```
Which is just a different level1.gz link and "sudo service transmission-daemon" in stead of using the init.d scripts.
I'd love some direction where to save my blocklist. Thanks!

---

### Post by MSumulong on 2010-06-12
I think this might point you in the right direction:

[https://trac.transmissionbt.com/wiki/Blocklists](https://trac.transmissionbt.com/wiki/Blocklists)

Let me know if this helps or not...

---

### Post by thuerrschmidt on 2010-07-03
The blocklists go into /var/lib/transmission-daemon/info/blocklists. You may have to create this directory and set its uid and gui to debian-transmission.

Below is a little Perl script that I'm running weekly on my Ubuntu server via cron to update my blocklist (needs root privileges and requires transmission version > 1.76).

```
#!/usr/bin/env perl
# ------------------------------------------------------------------------------
# Settings
my $blocklist_path = '/var/lib/transmission-daemon/info/blocklists';
my $blocklist_url  = 'http://update.transmissionbt.com/level1.gz';
# ------------------------------------------------------------------------------

chdir($blocklist_path)
	or die("failed to change directory to $blocklist_path: $!");
system('wget', '--quiet', $blocklist_url)
	and die("failed to retrieve blocklist");

# remove existing blocklists (if any)
foreach my $blocklist (qw/level1 level1.bin/) {
	if (-f $blocklist) {
		unlink($blocklist)
			or warn("error removing blocklist $blocklist: $!");
	}
}

system('gunzip', 'level1.gz')
	and die("failed to extract blocklist file");
system('chown', 'debian-transmission:debian-transmission', 'level1')
	and die("failed to change owner of blocklist file");
system('pkill', '-HUP', 'transmission-da')
	and die("failed to send SIGHUP to transmission daemon");

```

---

### Post by thomas_d_j on 2010-08-10
> **thuerrschmidt said:**
>  Below is a little Perl script...


Awesome man!  That was the only think missing from t-daemon as far as I was concerned.

---

### Post by prodigy_ on 2011-10-02
Re-implemented as a cron script using python without any external commands:
```

#!/usr/bin/env python

# Author: prodigydancer
# Version: 0.04

# [Description]

# Automatically downloads Bluetack Level 1 P2P blocklist updates
# and feeds them to transmission-daemon. Written in Python 2.6.
# Tested with Ubuntu 10.04.


import errno
import getpass
import gzip
import os
import pwd
import signal
from StringIO import StringIO
import sys
import urllib2

# Checking username.
if getpass.getuser() != 'debian-transmission':
    print("FATAL: {0} should be run under \'debian-transmission\' " +
          "account.".format(__file__))
    sys.exit(1)

# Defining "user" vars.
blocklist_path = '/var/lib/transmission-daemon/info/blocklists'
blocklist_url = 'http://www.bluetack.co.uk/config/level1.gz'
blocklist_fname = 'level1'
# Bluetack blocks non-browser UAs. /sigh
# People who claim to be Internet security experts could have come up
# with something better.
user_agent = ('Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 5.1; ' +
              'Trident/4.0; .NET CLR 1.1.4322; .NET CLR 2.0.50727)')

# Moving to the working dir.
try:
    os.makedirs(blocklist_path)
except OSError, os_error:
    if os_error.errno != errno.EEXIST:
        raise

os.chdir(blocklist_path)

# Clearing the working dir.
blocklist_files = os.listdir(blocklist_path)
for blocklist_file in blocklist_files:
    os.unlink(blocklist_file)

# Retrieving the archive via HTTP.
request = urllib2.Request(blocklist_url)
request.add_header('User-Agent', user_agent)
opener = urllib2.build_opener()
urllib2.install_opener(opener)
try:
    blocklist_data = urllib2.urlopen(request)
except urllib2.HTTPError, http_error:
    if http_error.code == 503:
        print("FATAL: Got \"HTTP Error {0}: {1}\" while trying to retrieve " +
              "the archive.".format(http_error.code, http_error.msg))
        sys.exit(1)
    else:
        raise

# Unpacking GZIP to TXT.
blocklist_gzip = StringIO(blocklist_data.read())
blocklist_txt = gzip.GzipFile(fileobj=blocklist_gzip).read()

# Writing TXT to file.
with open(blocklist_fname, 'w') as outfile:
    outfile.write(blocklist_txt)

# Relodading transmission-daemon.
td_uid = pwd.getpwnam('debian-transmission').pw_uid
pids = [pid for pid in os.listdir('/proc') if pid.isdigit()]

for pid in pids:
    pid_cmdpath = '/proc/' + pid + '/status'
    with open(pid_cmdpath, 'r') as pid_cmdstat:
        pid_cmdline = pid_cmdstat.readline()
        if pid_cmdline.split('\t')[1] == 'transmission-da\n':
            os.kill(int(pid), signal.SIGHUP)
            sys.exit(0)

```

This is programmed to run under debian-transmission account (to minimize any possible damage). If you want to run the script manually: ```
sudo sudo -u debian-transmission /path/to/script_name.py
```

---

