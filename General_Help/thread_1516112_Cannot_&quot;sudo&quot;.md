---
title: "Cannot &quot;sudo&quot;"
date: 2010-06-23
forum: General Help
---

### Post by Swanage on 2010-06-23
Corrupt sudoers file - maybe?
The problem:-

sudo doesn't work - when I try it I get:-

  sudo: can't stat /etc/sudoers: Input/output error
  sudo: no valid sudoers sources found, quitting

Also "System > Administration > Synaptic Package Manager" doesn't work; it apprears to try to load but goes nowhere.

If I start "synaptic" from the command line I get a message "Starting without administrative privileges you will not be able to apply any changes"  

The background is that, with help from this forum, I managed to install Ubuntu 10.04 Alpha 3 as a persistent live image on a 16GB Pendrive partitioned to give 2GB for the OS and 14GB for data. All has been working brilliantly for over a month but suddenly sudo has stopped working! I had not tried to edit the sudoers file or consciously tried to modify root privileges. The last thing I was doing before I noticed the problem was trying to get a printer driver for an old Epson Stylus Color 600 working.
I've tried booting from the original Ubuntu 10.04 DvD live distro to try to edit the persistent image, as per <http://ubuntuforums.org/newreply.php?do=newreply&p=8630083>,
on the pendrive but it does not appear to be in a viewable or editable format.
Also the persistent image does not appear to have a recovery boot option.
Any ideas on how I can recover "sudo" or is this a Catch 22 scenario?

---

### Post by Kilz on 2010-06-23
Have you tried booting into recovery mode and adding yourself to the sudo file? The instructions for that can be [found here]("http://www.pendrivelinux.com/how-to-add-a-user-to-the-sudoers-list/")

---

### Post by WorMzy on 2010-06-23
I'm guessing you manually edited /etc/sudoers with gedit or something? You shouldn't do that, as you can easily break it. You should use visudo, as that makes sure that there are no errors before the changes are committed to /etc/sudoers

You can't fix the problem in normal mode, so reboot, and boot into the recovery option. Drop to a root shell and run ```
visudo
```
or
```
EDITOR=nano visudo
```
if you're not familiar with vi.

The contents should look like this:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

---

### Post by sisco311 on 2010-06-23
You don't have to boot in recovery mode. Backup the file:
```
pkexec mv /etc/sudoers /etc/sudoers-old
```

Create a new one:
```
pkexec visudo
```

With the following content:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults env_reset 

# Host alias specification 

# User alias specification 

# Cmnd alias specification 

# User privilege specification
root ALL=(ALL) ALL 

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d 

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

Press Ctrl+x, y, Enter to save the file and exit.

---

### Post by Swanage on 2010-06-23
Thanks WorMzy and Sisco311 for your very prompt responses. Unfortunately the persistent live image does not appear to have a Recovery mode, and typing:-

ubuntu@ubuntu:~$ pkexec mv /etc/sudoers /etc/sudoers-old
results in:-
/bin/mv: cannot stat `/etc/sudoers': Input/output error

ubuntu@ubuntu:~$ pkexec visudo
results in:-
visudo: /etc/sudoers: Input/output error

ubuntu@ubuntu:~$ pkexec visudo -c 
results in:-
visudo: unable to open /etc/sudoers: Input/output error

What next?

---

### Post by WorMzy on 2010-06-23
If you can get into the grub boot menu (Hold down Shift or Esc immediately after POST, depending on which version of Grub you have installed), you should find the recovery mode there. If not, then by editing the Ubuntu option and adding "single" to the end of the kernel line, then booting, will put you into recovery mode.

It's hard to describe what I mean, hopefully you'll understand, or someone else will be able to explain the process in a more articulate manner.

I don't much like the sound of this I/O error though, perhaps your problem isn't in the sudoers file itself, but maybe there's something else wrong.

---

### Post by Swanage on 2010-06-24
Thanks again WorMzy for your prompt reply. I have tried every way I can think of to get the persistent image to boot in recovery mode but it would seem that the "persistent live image" does not have a recovery boot option.
The file "sudoers" shows 0 length, won't open for viewing, and has a "?" against it in Midnight Commander - so I think it is well and truly corrupted especially as I cannot delete it, rename it, or move it.
I had hoped there would be a quick and easy solution to my problem but as this does not appear to be the case I think a re-install may be quicker. I'm sorry if I've wasted anybody's time with all the messing about but at least I did learn a new command "pkexec" which I had not come across before. My grateful thanks to all who responded.

---

### Post by WorMzy on 2010-06-24
I learnt about that command too, so thanks to you and sisco for that. Sorry we couldn't fix your problem though.

---

### Post by Swanage on 2010-06-25
Problem solved by re-install - thanks to all for your help and courtesy.

---

