---
title: "Custom Upstart service  failing with &quot;Rejected send message&quot;"
date: 2011-02-08
forum: General Help
---

### Post by seventoes on 2011-02-08
I'm trying to write an upstart conf file to get Murmur (the Mumble server) to run as a service. It's located in /etc/murmur, and I'm using the following script in /etc/init/murmur.conf:

```
# Start when we have a net connection, filesystem, and
# a runnable runlevel.
start on (net-device-up
          and local-filesystems
          and runlevel [2345])

# Stop single user mode, system halt, or reboot.
stop on runlevel [016]

# Restart if it crashes
respawn

# Set the working directory for the job
chdir /etc/murmur

# Make sure the files we need are there
pre-start script
    set -e
    test -e /etc/murmur/murmur.ini
end script

# Ugly hack to run the service as an unprivileged user
script
   su -s /bin/sh -c 'exec "$0" "$@"' murmur -- /etc/murmur/murmur.x86 -fg >> /etc/var/murmur.log 2&>1
end script
#exec /etc/murmur/murmur.x86 -fg
```

When I try to run this, I get:

[HTML]$ service murmur start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.282" (uid=1000 pid=16314 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init))[/HTML]

I've tried commenting out each of the rules in the conf script individually and starting, but they all give me the same message. Anyone know what the issue might be?

---

### Post by Jimmy_r on 2011-02-20
Are you running ```
service murmur start
``` as root?
I was playing around with the same thing, but ended up stripping the code down a bit.. My goal was just to make it work at all since for some reason the regular init script failed to load it properly at boot

This is how it ended up for me, abit basic but atleast it works

```
start on (local-filesystems and net-device-up IFACE=eth0)

stop on runlevel [!12345]

exec /usr/sbin/murmurd -ini /etc/mumble-server.ini

```

Am using MURMUR_USE_CAPABILITIES=1 in the config so think it should drop root privs anyway.

---

