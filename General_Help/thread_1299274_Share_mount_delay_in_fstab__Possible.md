---
title: "Share mount delay in fstab?  Possible?"
date: 2009-10-23
forum: General Help
---

### Post by dwasifar on 2009-10-23
I have two nfs network shares that mount in fstab.  I upgraded to 9.10 RC and now when I boot, I get scrolling error messages before the splash screen comes up (black screen, white Ubuntu logo, white message text) that tell me the system is unable to reach the shares.  The messages repeat two or three times, then they go away and the boot proceeds normally.  When the boot is completed, the shares are mounted.

What this tells me is that the presence of the shares in fstab is delaying the boot, probably until the network interface comes up or nfs loads.

Is it possible to delay mounting the shares so that the boot will not be held up, perhaps by mounting them some other way, or by changing the fstab options?  Or, failing that, at least suppress the warnings?

---

### Post by dwasifar on 2009-10-25
bumpity-bump-bump

---

### Post by snyderxc on 2010-06-19
Hey everyone,
I was also looking for a way to do this in Lucid. This would significantly increase the boot process if I can tell it not to attempt until login, or at least until I have a network connection.

I've pondered /etc/rc.local, but if I could add a "sleep 1" to fstab without delaying the *entire* boot process, I would appreciate it.

---

### Post by ForgivenByJC on 2010-09-21
**[COLOR="Red"]UPDATE:[/COLOR]** Previous post below, and slightly different from this approach.

Now that I have had a couple of minutes to work with the scripts, here is a simplified approach.  In **/etc/fstab** make your nfs mounts have the 'noauto' option.  Like this```
# <file system> <mount point> <type> <options> <dump> <pass>
yournfsserver:/some/directory /media/directory2 nfs noauto,users,rw,hard,intr,noacl,nolock 0 0
```***** "yournfsserver," "some," "directory," "media," "directory2," and options should be changed to fit your application.

Next, create **/etc/network/if-up.d/mountnetfs** and copy this script to it```
#!/bin/sh

## Revised from http://ubuntuforums.org/showthread.php?t=430312
## Script will attempt to mount any fstab entry with type "nfs"

# Not for loopback
[ "$IFACE" != "lo" ] || exit 0

# unmount all shares first
sh "/etc/network/if-down.d/umountnetfs"

while read fs mp type opts dump pass extra
do
    # check validity of line
    if [ -z "$pass" -o -n "$extra" -o "`expr substr ${fs}x 1 1`" = "#" ];
    then
        # line is invalid or a comment, so skip it
        continue
    
    # check if the line is a selected line
    elif echo $type | grep -q "nfs"; then
        { sh -c "mount $mp" && 
        echo "$mp mounted as current user (`id -un`)" || 
        echo "$mp failed to mount as current user (`id -un`)"; 
        } &
    fi
    # if not a nfs line, do nothing
done </etc/fstab

wait

```

One more file, **/etc/network/if-down.d/umountnetfs** and copy this script to it```
#!/bin/bash

# Not for loopback!
[ "$IFACE" != "lo" ] || exit 0

# comment this for testing
exec 1>/dev/null # squelch output for non-interactive

# umount all nfs mounts
mounted=`grep 'nfs' /etc/mtab | awk '{ print $2 }'`
[ -n "$mounted" ] && { for mount in $mounted; do umount -l $mount; done; }

```Finally, change the user and permissions```
sudo chmod 755 /etc/network/if-up.d/mountnetfs /etc/network/if-down.d/umountnetfs
sudo chown root:root /etc/network/if-up.d/mountnetfs /etc/network/if-down.d/umountnetfs
```
Should now be able to reboot and the mounts wait for connectivity.  Hopefully this is helpful.  Let me know if you find a better way.  Again, this is just revised from [http://ubuntuforums.org/showthread.php?t=430312](http://ubuntuforums.org/showthread.php?t=430312), so most credit goes to [http://ubuntuforums.org/member.php?u=233493](http://ubuntuforums.org/member.php?u=233493) .


----Previous post----
Hello, depending on your handiness with script tweaking, you can adapt this to your situation.
[http://ubuntuforums.org/showthread.php?t=430312](http://ubuntuforums.org/showthread.php?t=430312)

Change the ```
comment=sshfs
``` in the **/etc/fstab** entry to ```
comment=netfs
``` (see *)

Create the **/etc/network/if-up.d/mountsshfs** script as **/etc/network/if-up.d/netfs** (see *)

Change ```
SELECTED_STRING="sshfs"
``` in the **if-up.d** script to ```
SELECTED_STRING="netfs"
``` (see *)

Will have to re-work much of the **if-down.d** script to work properly.  I currently don't have time to work through it.

> *****('netfs' could be any non-space word, e.g. "comment=goober" -- be certain "SELECTED_STRING" and "comment" are the same, if-up.d and if-down.d file names do not have to match any other name, just done to look nice).

At any rate, hopefully this can get you on the right track.  The scripts basically only need to execute the lines which are not comments and contains "nfs", if you want to whittle down to bare essentials.  This was a very quick post, so sorry for lacking detail and not having time to test it out myself.

---

