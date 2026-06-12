---
title: "How should I update the sudoers file to allow 'nopassword' for a program?"
date: 2009-07-15
forum: General Help
---

### Post by Pipps on 2009-07-15
I would like to write a script for automatic local system backups to a second local drive using Rdiff.

I understand that such a script will require 'sudo' permission. However, as I would like the operation of this script to be automated, I would like the system to not prompt me for a password before it is able to perform it.

I understand that in order to achieve this, I should update my 'sudoers' file to grant nopassword permission specifically to Rdiff.

My /etc/sudoers file currently comprises the following:

> 
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

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


I have read lots of threads and comments on how to update the sudoers file, but I am now more confused than ever about what I should do. Especially with the seemingly double or triple negative in the final line!

I understand that the relevant line of my command should include the following:
```
ALL = NOPASSWD: /usr/bin/rdiff-backup
```
But should this be preceded by '%admin' or '%myusername'?

Also, where should this entire line be inserted into the current sudoers file?

And when I have inserted this line, what should be amended sudoers file look like? If anyone could give me an example of this, it would be tremendously useful for me.

I hope I have been able to explain my request adequately. I should be most grateful for any advice. Thank you.

---

### Post by SteveDee on 2009-07-16
> **Pipps said:**
> I would like to write a script for automatic local system backups to a second local drive using Rdiff.

I understand that the relevant line of my command should include the following:
```
ALL = NOPASSWD: /usr/bin/rdiff-backup
```
But should this be preceded by '%admin' or '%myusername'?

Also, where should this entire line be inserted into the current sudoers file?

And when I have inserted this line, what should be amended sudoers file look like? If anyone could give me an example of this, it would be tremendously useful for me.

I hope I have been able to explain my request adequately. I should be most grateful for any advice. Thank you.

I'm no expert on this, but at the very least this will bump your thread!

I recently did something similar by writing a simple Gambas app to auto shutdown my system. Assuming you only want admin accounts to run your backup, I'd suggest adding this line to the end of your sudoers file:-
```
%admin ALL = NOPASSWD: /usr/bin/rdiff-backup
```
My understanding is that placing this line at the end of this file will override any conflicting lines that occur before this line. So don't worry about the existing content of the file.

To run your script from a terminal or launcher use the command:-
```
sudo  /usr/bin/rdiff-backup
```
...or to run auto at a certain time I guess you'd use this command with cron.

---

