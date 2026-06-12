---
title: "bash script: test exit status of unison (send email if it fails)"
date: 2012-07-25
forum: General Help
---

### Post by go4unkwn on 2012-07-25
hello bash experts

i run two apache servers (using ajaxplorer as webfilemanager) on two different pc's.

one of the apache server is reacheable from the internet, the other serve as backup system. in order to backup the data of the webfilemanager i use unison.

til now i run unison by hand. but i have in mind to run unison in batch mode using a bash script.

now i'm looking for some examples, how i can test the exit status of unison in an efficent way. the script should send me an email if the backup process fails and what fails.

unison knows the folloing exit codes:
0: successful sync
1: all file transfers were successful; some files were skipped
2: non-fatal failures during file transfer
3: fatal error occurred; execution was interrupted

hint: script without testing part
[HTML]#!/bin/bash

### test if unison (this script) is already running ###

    # process id of this script
    pid=$$
    
    # extract filename of this script
    # in order to create a lock file
    scriptname_with_extension=$(basename $0)
    scriptname="${scriptname_with_extensio%.*}"
    # hint! the lock file is NOT created; it's ONLY a variable
    lockfile="/var/lock/${scriptname}-$(id -nu).pid"
    
    # test if there is a lock file (script is already running)
    if test -f "${lockfile}" ; then
        echo >&2 "Error: Script already runs ... PID=$pid"
        ps auxw | grep "${scriptname}" | grep -v grep >&2
        exit 1
    fi
    
    # if the script of a previous process has already finished
    # remove the lock file of this finished process
    # and create a lock file for current process 
    trap "rm -f ${lockfile}" EXIT
    echo "${pid}" > "${lockfile}"

### run unison in order to sync two servers ###

    # hint! unison runs as user root
    # hint! unison uses a profile file in /root/.unison
    # hint! unison needs ssh login without password
    unison sync-server1-2-server2.prf

    # test exit status of unison; send email if sync process fail
    [/HTML]

so any example for testing the exit  status of unison is very welcome!

kind regards, go4unkwn

---

### Post by papibe on 2012-07-25
Hi go4unkwn.

The bash variable $? contains the exit code of the last executed command. You may test that variable over known exit codes and take an action if you which so.

This is a simple example using a case statement: 
```
...
unison sync-server1-2-server2.prf

case $? in
    0)
    	echo "successful sync."
        ;; 
    1)
    	echo "all file transfers were successful; some files were skipped."
        ;; 
    2)
    	echo "non-fatal failures during file transfer."
        ;;
    3)
    	echo "fatal error occurred; execution was interrupted."
        ;; 
    *)
    	echo "unknown exit code."
        ;;  
esac

```
I hope that points you in the right direction. Let us know how it goes.
Regards.

---

