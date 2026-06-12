---
title: "Unable to autolaunch a dbus-daemon without a $DISPLAY for X11"
date: 2012-07-12
forum: General Help
---

### Post by defaria on 2012-07-12
I recently updated my headless server to 12.04 and started getting the following warning from cron:

```
Cron <root@server> /usr/sbin/uptrack-upgrade -q -y

(process:13965): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
```

I've determined that if I unset DISPLAY (DISPLAY is set because I ssh -X into the server) and attempt to run /usr/sbin/uptrack-upgrade -q -y by hand I get the same warning message. But I have no X running on this headless server nor do I want to run X really and I didn't used to get this warning. Any ideas of how to fix this?

---

### Post by defaria on 2012-07-18
Bump!

---

### Post by Cheesehead on 2012-07-18
Take a look at the uptrack config file: /etc/uptrack/uptrack.conf 
```
# **GUI users will get all notices via the GUI and likely want to set**
# **the following cron options to "no".**
# Cron job will install updates automatically
autoinstall = no
# Cron job will print a message when new updates are installed.
# This option is only relevant if autoinstall = yes
cron_output_install = no
# Cron job will print a message when new updates are available
cron_output_available = no
# Cron job will print a message when it encounters errors
cron_output_error = no
```

Perhaps Uptrack seems to assume an X server now?

---

### Post by defaria on 2012-07-18
That's be my guess as well except I've never had X running (at least I don't think I did) on this headless box and I never had this problem...

---

### Post by defaria on 2012-07-19
Changed it to:

```
[Settings]
# Install updates automatically as soon as we learn about them
# (If you're using the GUI, you likely want to say 'no' here)
autoinstall = yes

# Send detailed Ksplice debug output to the Uptrack server?
# This allows Uptrack to diagnose and fix problems found in the field.
# (In any case, less detailed information is sent to the server
# in order for the service to operate.)
debug_to_server = yes

# If you're using the GUI, you likely want to say 'no' to all of the
# options below, since the GUI will notify you when these things
# happen.
# Should the cron job generate output when errors occur?
cron_output_error = yes
# When new updates are available (and not yet installed)?
cron_output_available = yes
# When updates are successfully installed by the cron job?
cron_output_install = yes

```

Same error.

---

### Post by defaria on 2012-07-28
Bump

---

