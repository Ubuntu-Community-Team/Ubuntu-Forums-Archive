---
title: "ushare - no content via Xbox 360"
date: 2012-01-02
forum: General Help
---

### Post by Face-Ache on 2012-01-02
I have a similar issue to the one posted here;
[http://ubuntuforums.org/showthread.php?t=1693330](http://ubuntuforums.org/showthread.php?t=1693330)

However, the media directory path is correct i believe, so i am at a loss as to why there is no content when i try and access from the Xbox 360.

I've named it 'ubuntu PC' and it comes up on the Xbox360, but no content at all.

This content is stored on an external 1tb WD Elements drive, and can be accessed by VLC with no issue. Could it possibly be that i need to specify the partition for this WD Elements drive?  It's under media/elements/music, but do i need to also note  /dev/sdf1 somewhere?

Would appreciate any help!  :)

Here's my config file for ushare;
# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=Ubuntu PC

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=wlan0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49200

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=media/elements/music/

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
USHARE_ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
USHARE_ENABLE_TELNET=

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
USHARE_ENABLE_DLNA=no

---

### Post by Face-Ache on 2012-01-03
Update - i got this figured out, but its generated another problem.

The config file is case sensitive, so i needed to enter the path as media/Elements/Music. Once done, and with the Pictures folder also listed, my media started showing on the Xbox 360. Heh.

That's great, but nothing has been ordered via the artist-album-songfile folder structure, just all lumped into one location. I can't figure out how to get ushare to maintain the folder structure/hierarchy of the media folders.

I see a couple of others have also had this problem and posted on the interwebs, but no real solutions it seems. Anyone have any ideas?

Wow, get one thing figured out, and then another issue. All starting to get a bit hard really!  :)

---

### Post by Face-Ache on 2012-01-03
I've spent quite some time now trying to get some basic media sharing going using Ubuntu, and i have to say, it's been an exercise in frustration.

I believe that something as simple as media sharing on a network should not be this hard, so i have now uninstalled Ubuntu, and will stick with Windows.

---

