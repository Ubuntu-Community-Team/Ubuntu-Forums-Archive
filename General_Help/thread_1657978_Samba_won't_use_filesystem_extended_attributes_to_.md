---
title: "Samba won't use filesystem extended attributes to store DOS attributes"
date: 2011-01-01
forum: General Help
---

### Post by JohnnySkidmark on 2011-01-01
I am having problems with [FONT="monospace"]Samba[/FONT]'s support for [FONT="monospace"]DOS[/FONT] attributes.  By default, [FONT="monospace"]Samba[/FONT] maps the archive, hidden, and system attributes to *nix file permissions, and I've confirmed that works correctly.  However, when I enable [FONT="monospace"]Samba[/FONT]'s support for storing [FONT="monospace"]DOS[/FONT] permissions in extended attributes...it just simply doesn't work.  From a 64-bit [FONT="monospace"]Windows 7 Professional[/FONT] client, when I try to set the archive, hidden, and/or system attributes for a file (either through the [FONT="monospace"]Properties[/FONT] dialog, or using [FONT="monospace"]attrib.exe[/FONT]) nothing happens.  No [FONT="monospace"]user.DOSATTRIB[/FONT] extended attribute is created for the file, and if I reopen the [FONT="monospace"]Properties[/FONT] dialog the checkboxes that I'd just checked will now be cleared.  If I use [FONT="monospace"]setfattr[/FONT] to manually create [FONT="monospace"]user.DOSATTRIB[/FONT], or for files that already have that extended attribute, it still has no effect; [FONT="monospace"]Samba[/FONT] just completely ignores that extended attribute.  As for the read-only attribute, if I set it on a file then I can see that it's actually removing the user's write access from the *nix permissions, though upon reopening the [FONT="monospace"]Properties[/FONT] dialog the read-only attribute still appears as unset.

I've spent hours searching and everyone seems to just list the same set of configuration parameters that need to be set to make this work, but I've set mine that way and it just won't work.  The only lines in the logs that are vaguely helpful are...
```
get_ea_dos_attributes: Cannot get attribute from EA on file ./..: Error = Operation not supported
```
...and...
```
get_ea_dos_attributes: Cannot get attribute from EA on file .: Error = Operation not supported
```
...though that's not really lead me [anywhere]("http://lists.samba.org/archive/samba/2009-March/147102.html").  The machine in question is a guest of [FONT="monospace"]VirtualBox[/FONT] 4.0.0, with both host and guest running 64-bit [FONT="monospace"]Ubuntu Server[/FONT] 10.10 with kernel 2.6.35-24-server.  It's a pretty vanilla installation, with the only changes/additions (as best as I can remember) being [FONT="monospace"]VirtualBox Guest Additions[/FONT] and the following packages in [FONT="monospace"]Aptitude[/FONT]: [FONT="monospace"]acl[/FONT] (2.2.49), [FONT="monospace"]attr[/FONT] (2.4.44), [FONT="monospace"]dkms[/FONT], [FONT="monospace"]ntp[/FONT], [FONT="monospace"]openssh-server[/FONT], [FONT="monospace"]samba[/FONT] (3.5.4), and [FONT="monospace"]winbind[/FONT] (3.5.4).  This virtual machine has actually taken over file-serving duties from an old 64-bit [FONT="monospace"]Ubuntu Server[/FONT] 10.04 virtual machine on which [FONT="monospace"]DOS[/FONT] attributes worked, which is why I have existing files with the proper extended attributes, though I've not been able to find any differences between the two configurations that would explain why the new server has this problem.

Can someone who has extended attributes working with [FONT="monospace"]Samba[/FONT] post their [FONT="monospace"]smb.conf[/FONT], or take a look at mine?

```
user@Hostname:~$ grep XATTR /boot/config-`uname -r`
CONFIG_EXT2_FS_XATTR=y
CONFIG_EXT3_FS_XATTR=y
CONFIG_EXT4_FS_XATTR=y
CONFIG_REISERFS_FS_XATTR=y
# CONFIG_JFFS2_FS_XATTR is not set
CONFIG_UBIFS_FS_XATTR=y
CONFIG_SQUASHFS_XATTRS=y
CONFIG_CIFS_XATTR=y
```
```
user@Hostname:~$ grep /data/media /etc/fstab
/dev/media-audio        /data/media/audio       ext3    defaults,acl,data=journal,errors=remount-ro,relatime,user_xattr 0       2
/dev/media-graphics     /data/media/graphics    ext3    defaults,acl,data=journal,errors=remount-ro,relatime,user_xattr 0       2
/dev/media-video        /data/media/video       xfs     defaults,relatime       0       2
```
```
user@Hostname:~$ testparm -sL Hostname
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[Audio]"
Processing section "[Graphics]"
Processing section "[Video]"
Loaded services file OK.
Server role: ROLE_DOMAIN_MEMBER
[global]
        workgroup = DOMAIN
        realm = DOMAIN.TLD
        netbios aliases = Hostname
        server string = %h server (Samba, Ubuntu)
        interfaces = lo, bridged0, hostonly0
        bind interfaces only = Yes
        security = ADS
        map to guest = Bad User
        password server = 10.0.0.2
        restrict anonymous = 2
        client NTLMv2 auth = Yes
        log level = 1
        log file = /var/log/samba/%m.log
        max log size = 1000
        smb ports = 139
        server signing = auto
        load printers = No
        printcap name = /etc/printcap
        os level = 0
        local master = No
        domain master = No
        remote announce = 10.0.0. 10.10.10.
        panic action = /usr/share/samba/panic-action %d
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        winbind separator = .
        winbind enum users = Yes
        winbind enum groups = Yes
        winbind use default domain = Yes
        winbind offline logon = Yes
        invalid users = root
        hosts allow = 10.0.0., 10.10.10., 127.

[Audio]
        path = /data/media/audio
        read only = No
        create mask = 0751
        ea support = Yes
        hide dot files = No
        hide special files = Yes
        hide unreadable = Yes
        map archive = No
        map readonly = no
        store dos attributes = Yes

[Graphics]
        path = /data/media/graphics
        read only = No
        create mask = 0751
        ea support = Yes
        hide dot files = No
        hide special files = Yes
        hide unreadable = Yes
        map archive = No
        map readonly = no
        store dos attributes = Yes

[Video]
        path = /data/media/video
        read only = No
        create mask = 0751
        ea support = Yes
        hide dot files = No
        hide special files = Yes
        hide unreadable = Yes
        map archive = No
        map readonly = no
        store dos attributes = Yes
```

(Note that [FONT="monospace"]map hidden[/FONT] and [FONT="monospace"]map system[/FONT] are off by default, which is why they don't appear in the above [FONT="monospace"]testparm[/FONT] output, even though I've explicitly disabled them in the configuration file.)

To summarize, [FONT="monospace"]DOS[/FONT] permissions do not work in the above configuration, however if I substitute the following configuration parameters...
```
ea support = no
store dos attributes = no
map archive = yes
map hidden = yes
map readonly = yes
map system = yes
```
...for each share then [FONT="monospace"]DOS[/FONT] attributes work properly.  I've got extended attributes working at the filesystem level, I just can't seem to convince [FONT="monospace"]Samba[/FONT] to actually do anything with them.

Thanks for the help.

---

### Post by MitjaT on 2012-01-11
I had the same problem and it take me some time to solve...

When you make a share the underlying filesystem must support extended attributes, but in your case . and .. does not support this attributes.
I solved sharing a subfolder of the mount point.

---

