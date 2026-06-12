---
title: "mount samba shared permission denied"
date: 2010-12-07
forum: General Help
---

### Post by Clive McCarthy on 2010-12-07
I have a shared directory on another machine but I can't get it to mount. 

The permission denied doesn't say where/which permission is denied. Is it on the remote on on the local machine? The remote has sharing enabled for the shareddocs directory and after I have mkdir'ed the local mount point I open it's permissions too.

The verbose response from mount.cfis looks like this:

mount.cifs kernel mount options: unc=//192.168.1.102\shareddocs,domain=WORKGROUP,ver=1,rw,username=clive,,,,,,,,,,,ip=192.168.1.102,pass=********
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

The man page does not have a list of error codes.

---

### Post by pricetech on 2010-12-07
Can you connect using SSH ??

---

### Post by Clive McCarthy on 2010-12-07
Don't know. But Nautilus can get to the shared folder without difficulty. It is undoubtedly present. There have been tons of posts on the web referring to "mount error(13): Permission denied" and many suggested solutions and I have tried, as best as I can determine, all of them.

---

### Post by Clive McCarthy on 2010-12-10
Arrow Re: mounting samba shared = permission denied
It seems you were on the right track. My command does have a "/" and cifs converts it to a "\" for who knows what reason???

However, if I turn on mapchars then the SAMBA mount.cifs succeeds. This is of course a dreadful hack. The man page for mount.cifs excludes the backslash from being mapped. Not that I had a backslash to start with!

    mapchars
    Translate six of the seven reserved characters (not backslash, but
    including the colon, question mark, pipe, asterik, greater than and
    less than characters) to the remap range (above 0xF000), which also
    allows the CIFS client to recognize files created with such
    characters by Windows´s POSIX emulation. This can also be useful
    when mounting to most versions of Samba (which also forbids
    creating and opening files whose names contain any of these seven
    characters). This has no effect if the server does not support
    Unicode on the wire.

I have seen at least one BIG rant on the web about cfis and it seems appropriate. Judging from some developer commentary it looks as if they are just hacking around. The developers seem to be in a bind about resolving translations between Windows conventions and Unix conventions.
The verbose mode for mount.cfis produces a truncated output and the error messages are worthless. My guess is that a bunch of script kiddies are writing cfis with very tangled command-line Goto logic!

The man pages also suggest that providing the UNC name will work most of the time. It doesn't.

    ip=arg
    sets the destination IP address. This option is set automatically
    if the server name portion of the requested UNC name can be
    resolved so rarely needs to be specified by the user.

I have found it essential to use resolveip to obtain the IP address for the server and then spoon feed mount.cfis with it.

---

