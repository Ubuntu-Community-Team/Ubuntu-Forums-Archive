---
title: "Could not download all repository indexes"
date: 2010-07-22
forum: General Help
---

### Post by dystopiangirl on 2010-07-22
I'm completely new to Ubuntu, I've just installed 10.04 and this is only the second week I've had it, and I'm not sure what is going on with this. Whenever I try to check for updates I get this message:

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
> GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by cariboo on 2010-07-23
Feisty is no longer supported, so you should remove that line from /etc/apt/sources.list, you should also comment out the cdrom entry in the same file. To edit /etc/apt/sources.list, press Alt-F2 and type:

```
gksu gedit /etc/apt/source.list
```

to comment out a line, just put a **#** at the start of the line eg:

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Alpha amd64 (20100707)]/ maverick main restricted
```

The above example is what the line for the cdrom looks like in my sources.list file.

---

### Post by dystopiangirl on 2010-07-23
Whenever I run that code /etc/apt/sources.list shows up as blank, should it be doing that?

---

### Post by garvinrick4 on 2010-07-23
Just a typo: Post 2
Copy and paste this:

```
gksudo gedit /etc/apt/sources.list
```you forgot the s on the end of sources.

---

### Post by dystopiangirl on 2010-07-23
So, I made the changes you said I should, but now this is coming up when I open the Update Manager:

Could not initalize the package information
  ```
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid_multiverse_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
```

---

