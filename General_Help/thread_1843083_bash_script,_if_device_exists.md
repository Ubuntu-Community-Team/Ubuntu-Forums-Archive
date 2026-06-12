---
title: "bash script, if device exists"
date: 2011-09-12
forum: General Help
---

### Post by OldManRiver on 2011-09-12
Original thread: [thread=545092]here[/thread]

> if grep '/media/disk' /etc/mtab > /dev/null 2>&1; then
    echo "mounted"
else
    echo "not mounted"
fi


robert_pectol,

I have a flash drive that always shows as 'E441-2317' and it shows in the "etc/mtab" file when inserted.  I want it to mount as "/flash" and so I have the code:
```

if grep 'E441-2317' /etc/mtab > /dev/null 2>&1; then
    mkdir /flash
    # parsing line
    mount $what /flash
fi

```
What parsing is needed, in the "# parsing line" to get the first string set/portion of "/dev/?" for my flash drive from the grep string you are producing here, assigning it to my $what var?

Thanks!

OMR

---

### Post by sisco311 on 2011-09-13
E441-2317 looks like the UUID of the partition. If so, you can use the symlink from dev:
```
mount /dev/disk/by-uuid/E441-2317 /mount/point
```

But why don't you create an fstab entry for it?
[thread=283131]How to fstab[/thread]

---

### Post by OldManRiver on 2011-09-13
> **sisco311 said:**
> E441-2317 looks like the UUID of the partition. If so, you can use the symlink from dev:
```
mount /dev/disk/by-uuid/E441-2317 /mount/point
```

But why don't you create an fstab entry for it?
[thread=283131]How to fstab[/thread]

sisco311,

Appreciate your feedback but the commands I entered work fine, don't need the UUID.  All I have to do is manually look up the entry, with the grep statement, and the first part of the string returned contains the "/dev?point" information which is what I want to parse into the $what var.

I'm not good at assigning vars and parsing strings in bash, yet so trying to learn that.  Keep looking at the manuals, but always get a mental disconnect, so just not getting the "ding" light is on, in my mind.

Thought maybe you or others have some bash insight here!

Oh Hey about the "Old Post" comment, did not even notice the date.  Most old threads are closed, so can not reply, so never think about looking at dates.

Thanks!

OMR

---

### Post by sisco311 on 2011-09-14
You can do it with awk:
```
var="$(awk '/E441-2317/{print $1; exit}' /etc/mtab)"
if [[ "$var" ]]; then
    mount "$var" /flash
fi

```

---

### Post by OldManRiver on 2011-09-15
sisco311,

Thanks for your help!

Added this to my script at:

[http://ubuntuforums.org/showthread.php?p=11253671](http://ubuntuforums.org/showthread.php?p=11253671)

Thanks again!

OMR

---

### Post by OldManRiver on 2011-09-15
sisco311,

Also working on a mount problem at:

[http://ubuntuforums.org/showthread.php?t=1787970](http://ubuntuforums.org/showthread.php?t=1787970)

but this is an external drive mounted on a Windows Server and shared on the system for backups.

Any ideas on that?

Thanks!

OMR

---

### Post by OldManRiver on 2011-09-28
All,

Thanks for the inputs!  Used these in the script at:

[http://ubuntuforums.org/showthread.php?t=1818588](http://ubuntuforums.org/showthread.php?t=1818588)

Was able to successfully find and mount my two externals with this code, as you see.

Still working on adding this to a script, trying to find a SAMBA mount, but not done there yet.

Marking this "SOLVED".

Thanks!

OMR

---

