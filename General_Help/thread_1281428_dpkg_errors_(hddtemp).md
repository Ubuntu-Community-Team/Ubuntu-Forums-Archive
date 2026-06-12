---
title: "dpkg errors (hddtemp)"
date: 2009-10-03
forum: General Help
---

### Post by Feelin_froggy8877 on 2009-10-03
I am having a install/reinstall problem w/ package (hddtemp)
I have never ran into a problem like this befor, and any google results close to this seems to be package specific. So not sure what info might be needed. Please just let me know. thanx.

---

### Post by crolanx on 2009-10-03
There seems to be a problem with the file **/etc/defaults/hddtemp** .
You could take a look at line 40 of that file and try to correct the syntax.

You also could rename the file and then try again to reinstall hddtemp. If something goes wrong afterwards, just restore the old file.

---

### Post by Feelin_froggy8877 on 2009-10-03
Sorry, I'm not very good w/ syntax. Could you maybe give an example of what im looking for? "EOF in backquote substitution"? I took a look at the file, don't even seem to be a line 40.

---

### Post by crolanx on 2009-10-04
In my hddtemp there are only 39 lines, too. 

First of all, I can't say you what "EOF in backquote substitution" means, but I could think of something like that:

```

RUN_SYSLOG="0

OPTIONS=""

```In this example, one quotation mark is missing. 

It is also possible, that there is a special character somewhere in that file, which is not interpreted the way it should be.

If you wanted, you could attach your hddtemp to your next post, so that I could take a look at it.

---

### Post by Feelin_froggy8877 on 2009-10-04
Thanks for your help here. 

# Defaults for hddtemp initscript (/etc/init.d/hddtemp)
# This is a POSIX shell fragment

# [automatically edited by postinst, do not change line format ]

# hddtemp network daemon switch. If set to true, hddtemp will listen
# for incoming connections.
RUN_DAEMON="true"

# List of devices you want to use with hddtemp. If none specified,
# hddtemp will probe standard devices.
#DISKS="/dev/hda"

# List of devices you want to use with hddtemp, but that would not be
# probed for a working sensor.
DISKS_NOPROBE=""

# IP address of the interface on which you want hddtemp to be bound
# on. If none specified, goes to 127.0.0.1. Use 0.0.0.0 to bind hddtemp
# on all interfaces.
INTERFACE="127.0.0.1`"

# Port number on which you want hddtemp to listen on. If none specified,
# the port 7634 is used.
PORT="7634"

# Database file to use. If none specified, /etc/hddtemp.db is used.
#DATABASE="/etc/hddtemp.db"

# Separator to use between fields. The default separator is '|'.
#SEPARATOR="|"

# Logging period (in seconds) for the temperatures. If set to a value
# different than 0, hddtemp will run as a daemon periodically logging
# the temperatures through syslog
RUN_SYSLOG="0"

# Other options to pass to hddtemp
OPTIONS=""

---

### Post by crolanx on 2009-10-04
I can not see any errors in your file, so I'd just suggest that you rename **/etc/defaults/hddtemp** to **/etc/defaults/hddtemp.old**. After that, try to remove and install hddtemp again. Then the file should be created again.

If something goes wrong then, you could easily restore the original file.

---

### Post by Feelin_froggy8877 on 2009-10-04
No luck w/ that, I have also noticed while installing other packages, I see an error "error in package" referring to hddtemp.

---

### Post by crolanx on 2009-10-05
> "error in package" referring to hddtemp. 

Well, you could force aptitude to completely remove hddtemp, but such action can harm other packages, so use it at your own risk:
```
sudo aptitude -f purge hddtemp
```.

An other solution could be a manual install of hddtemp with dpkg:
```

sudo aptitude clean
sudo aptitude download hddtemp
sudo dpkg -i /var/cache/apt/archives/hddtemp*.deb

```

---

