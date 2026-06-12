---
title: "cannot mount external harddrive"
date: 2010-05-23
forum: General Help
---

### Post by nicewroldorder on 2010-05-23
I have an external hardrive that is connected to my wireless router. I managerd to mount it with a laptop using the following command:

sudo -s
mount -t smbfs //hpmediavault/MediaShare /mnt/MediaShare

I tried this with another computer that is connected to the router via a cable rather than wireless and this is the result:

mount: wrong fs type, bad option, bad superblock on //hpmediavault/MediaShare,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Both computers are running Ubuntu 9.10 so why does it work with one and not the other.

thanks a heap.

Another strange thing is that I had to make a new account to post to this forum because the one I use on my wireless laptop does not work on this message.  This is the message I get:

**nicewroldorder**, you do not have permission to access this page. This could be due to one of several reasons:
  
[LIST=1]
[*]Your user account may not have sufficient privileges to access this page. Are you trying to edit someone else's post, access administrative features or some other privileged system?
[*]If you are trying to post, the administrator may have disabled your account, or it may be awaiting activation
[/LIST]
thanks for the help - chris

---

