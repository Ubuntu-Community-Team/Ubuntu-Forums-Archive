---
title: "How to hide my fstab mount?"
date: 2010-10-06
forum: General Help
---

### Post by Resilldoux on 2010-10-06
Hi,

I'm having a bit of a problem. How can I hide my fstab mount form nautilus when it isn't mounted yet? You see, I'm actually seeing my fstab entry twice in nautilus. One in a mounted state, and the other in an unmounted state. How can I hide the unmounted one while keeping my mounted one? I want to see my mounted one whenever it's mounted of course, and just want it to disappear when it isn't mounted (you know, as it normally would).

Here's a screenshot:
[IMG]http://img687.imageshack.us/img687/8307/screenshotska.png[/IMG]

Here's my fstab line:

```
sshfs#guido@svr-kroon:/media/DATA-E/Guido        /media/svr-kroon        fuse    defaults,noauto,users,uid=1000,gid=1000,reconnect,follow_symlinks,comment=sshfs    0    0
```I noticed that whenever I deleted the **users** switch in the fstab line it actually would disappear like I want it to, but then my sshfs mount wouldn't mount itself any more when my network is up.

You should note that I'm using scripts in my /etc/network/if-up.d and /etc/network/if-down.d folder to have it automatically mounted when I'm connected to the network and unmounted whenever I lose connectivity to my network. Without the **users** switch in the fstab line the scripts don't work any more.

Here's my /etc/network/if-up.d/mountsshfs
```
#!/bin/sh

## http://ubuntuforums.org/showthread.php?t=430312
## The script will attempt to mount any fstab entry with an option
## "...,comment=$SELECTED_STRING,..."
## Use this to select specific sshfs mounts rather than all of them.
SELECTED_STRING="sshfs"

# Not for loopback
[ "$IFACE" != "lo" ] || exit 0

## define a number of useful functions

## returns true if input contains nothing but the digits 0-9, false otherwise
## so realy, more like isa_positive_integer 
isa_number () {
    ! echo $1 | egrep -q '[^0-9]'
    return $?
}

## returns true if the given uid or username is that of the current user
am_i () {
    [ "$1" = "`id -u`" ] || [ "$1" = "`id -un`" ]
}

## takes a username or uid and finds it in /etc/passwd
## echoes the name and returns true on success
## echoes nothing and returns false on failure 
user_from_uid () {
    if isa_number "$1"
    then
        # look for the corresponding name in /etc/passwd
        local IFS=":"
        while read name x uid the_rest
        do
            if [ "$1" = "$uid" ]
            then 
                echo "$name"
                return 0
            fi
        done </etc/passwd
    else
        # look for the username in /etc/passwd
        if grep -q "^${1}:" /etc/passwd
        then
            echo "$1"
            return 0
        fi
    fi
    # if nothing was found, return false
       return 1
}

## Parses a string of comma-separated fstab options and finds out the 
## username/uid assigned within them. 
## echoes the found username/uid and returns true if found
## echoes "root" and returns false if none found
uid_from_fs_opts () {
    local uid=`echo $1 | egrep -o 'uid=[^,]+'`
    if [ -z "$uid" ]; then
        # no uid was specified, so default is root
        echo "root"
        return 1
    else
        # delete the "uid=" at the beginning
        uid_length=`expr length $uid - 3`
        uid=`expr substr $uid 5 $uid_length`
        echo $uid
        return 0
    fi
}

# unmount all shares first
sh "/etc/network/if-down.d/umountsshfs"

while read fs mp type opts dump pass extra
do
    # check validity of line
    if [ -z "$pass" -o -n "$extra" -o "`expr substr ${fs}x 1 1`" = "#" ]; 
    then
        # line is invalid or a comment, so skip it
        continue
    
    # check if the line is a selected line
    elif echo $opts | grep -q "comment=$SELECTED_STRING"; then
        
        # get the uid of the mount
        mp_uid=`uid_from_fs_opts $opts`
        
        if am_i "$mp_uid"; then
            # current user owns the mount, so mount it normally
            { sh -c "mount $mp" && 
                echo "$mp mounted as current user (`id -un`)" || 
                echo "$mp failed to mount as current user (`id -un`)"; 
            } &
        elif am_i root; then
            # running as root, so sudo mount as user
            if isa_number "$mp_uid"; then
                # sudo wants a "#" sign icon front of a numeric uid
                mp_uid="#$mp_uid"
            fi 
            { sudo -u "$mp_uid" sh -c "mount $mp" && 
                echo "$mp mounted as $mp_uid" || 
                echo "$mp failed to mount as $mp_uid"; 
            } &
        else
            # otherwise, don't try to mount another user's mount point
            echo "Not attempting to mount $mp as other user $mp_uid"
        fi
    fi
    # if not an sshfs line, do nothing
done </etc/fstab

wait
```And here's my /etc/network/if-down.d/umountsshfs
```
#!/bin/bash

# Not for loopback!
[ "$IFACE" != "lo" ] || exit 0

# comment this for testing
exec 1>/dev/null # squelch output for non-interactive

# umount all sshfs mounts
mounted=`grep 'fuse.sshfs\|sshfs#' /etc/mtab | awk '{ print $2 }'`
[ -n "$mounted" ] && { for mount in $mounted; do umount -l $mount; done; }
```Can anyone help me with this?

---

### Post by oldfred on 2010-10-06
I believe anything mounted in /media or /home appears twice. I think there may be a setting somewhere, but my work around is to just mount it elsewhere and link the folders into /home.

I copied this comment's way:
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
 Morgan Hall said:

My personal solution (yes, I use thunderbird) -- I make my data directory a partion mounted on /usr/local so my homebrew apps are in /usr/local/bin. A data directory there contains the working directories for home data -- /usr/local/morganh/Data

oldfred's versions (post #5) of data linking from above blog, based on more from comments 
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by WorMzy on 2010-10-06
I can't help with your problem, but you helped me with one of mine -- I had a similar problem with one of my local partitions, removing "users" from it's fstab line fixed it for me. I'd had that problem for as long as I can remember, and had given up fixing it, so thanks for that. :D

---

### Post by mc4man on 2010-10-06
Your issue (2 entries for 1 mount) is most likely related to this bug.
Unfortunately the simple workaround for local mounts will not work for sshfs though you may wish to check once and a while to see if anything comes up.

(scroll down for posts where /dev/disk/by-uuid/xx or /dev/disk/by-label/xx doesn't work

[https://bugs.launchpad.net/gvfs/+bug/442130](https://bugs.launchpad.net/gvfs/+bug/442130)

---

### Post by Resilldoux on 2010-10-07
@ oldfred - Ok, I'll use that workaround as well then, because it's really annoying having my mounts appear twice.

@ mc4man - Thanks, I'll check that from time to time. This is indeed very similar to the problem I'm experiencing.

@ WorMzy - Glad to help. =)

---

