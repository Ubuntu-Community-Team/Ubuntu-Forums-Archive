---
title: "Need help editing a file"
date: 2010-09-21
forum: General Help
---

### Post by WiReIs on 2010-09-21
Hello, im finding it hard to edit a file, its probably a common practice with most people on this forum so your help would be very much appreciated :)

Ive installed a VLC Remote App to my Blackberry which can control my VLC player from any computer over my Wireless network however.. im having trouble figuring out how to edit a certain file its telling me to edit..

> #
# Access-list for VLC HTTP interface
# $Id$
#

# localhost
::1
127.0.0.1

# link-local addresses
#fe80::/64

# private addresses
#fc00::/7
#fec0::/10
#10.0.0.0/8
#172.16.0.0/12
#192.168.0.0/16
#169.254.0.0/16

# The world (uncommenting these 2 lines is not quite safe)
#::/0
#0.0.0.0/0


The instructions tell me to edit this file which can be found /usr/share/vlc/http/.hosts

How do i find this file :confused:

I need to remove the '#' on each private address like so..

> #
# Access-list for VLC HTTP interface
# $Id$
#

# localhost
::1
127.0.0.1

# link-local addresses
#fe80::/64

# private addresses
fc00::/7
fec0::/10
10.0.0.0/8
172.16.0.0/12
192.168.0.0/16
169.254.0.0/16

# The world (uncommenting these 2 lines is not quite safe)
#::/0
#0.0.0.0/0

Any help would be really appreciated :)

---

### Post by WiReIs on 2010-09-21
solved :) 

open terminal:

> sudo gedit/usr/share/vlc/http/.hosts

edit & save

---

### Post by ajgreeny on 2010-09-21
Try ```
gksudo gedit /usr/share/vlc/http/.hosts
``` in terminal which will open the file in the normal text editor (gedit) with root permissions, allowing you to save any changes.

make a backup first with ```
sudo cp gksudo gedit /usr/share/vlc/http/.hosts gksudo gedit /usr/share/vlc/http/.hosts.backup
``` just in case you need to revert back.

All this is a result of linux file ownership and permissions, which are for your own well-being and stop you doing things to system files without root permission.  Using sudo in front of a command gives you root permissions as long as you, ie your username, is a member of the admin group.

See "Root sudo" in my signature for more info.

Note that is should be **gksudo** not **sudo** as shown by WiReIs in the first command.  Again, see my signature link for the reasons for this.

---

### Post by Scunizi on 2010-09-21
Actually to make the backup type... sudo cp /usr/share/vlc/http/.hosts /usr/share/vlc/http/.hosts.backup

---

### Post by ajgreeny on 2010-09-22
Whoops!  Sorry for that typo about the backup command.

That's what you get for using a middle click to paste, and not checking what you have just highlighted to fill the copy buffer.  Scunizi has the correct command for the backup.

---

