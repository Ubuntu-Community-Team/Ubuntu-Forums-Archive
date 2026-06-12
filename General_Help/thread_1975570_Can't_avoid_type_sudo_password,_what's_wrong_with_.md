---
title: "Can't avoid type sudo password, what's wrong with my sudoers file?"
date: 2012-05-07
forum: General Help
---

### Post by tigre.dragon on 2012-05-07
Hello,

In previous versions of Ubuntu, I remember that I could just add a line for my username in the sudoers file and avoid typing the sudo password.

However, since last versions of ubuntu, this trick does not work for me anymore. I am particulary annoyed that in 12.04 I cannot use sudo without typing the password for any command. Of course after typing it I can continue using sudo in the very same terminal without typing it.

So, here it is my sudoers file:

> 
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

josem ALL=(ALL) NOPASSWD:ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD:ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d



My username is josem, which belongs to the group josem. I have also tried all varians like (ALL:NOPASSWD) ALL and many other variants, but nothing works... just keeps asking for my password.

Does anyone knows how I could debug this?

Thanks! :guitar:

---

### Post by tigre.dragon on 2012-05-07
I added the line at the end of the file and now works.

By any reason, some of the lines was overwriting mine, althought can't understand how this is possible...

---

### Post by Cheesemill on 2012-05-07
Lines in sudoers are applied in the order they appear, and take precedence over previous lines.

In your case the 'josem ALL=(ALL) NOPASSWD:ALL' line was being applied correctly, but because you are also a member of the sudo group the '%sudo   ALL=(ALL:ALL) ALL' line further down meant you still had to enter your password.

---

### Post by Ilo1 on 2012-06-05
> **Cheesemill said:**
> Lines in sudoers are applied in the order they appear, and take precedence over previous lines.

In your case the 'josem ALL=(ALL) NOPASSWD:ALL' line was being applied correctly, but because you are also a member of the sudo group the '%sudo   ALL=(ALL:ALL) ALL' line further down meant you still had to enter your password.
I've been struggling with this problem for at least 4 hrs today. I just want to say thanks! This was my problem as well. Someone should do something to fix that.

---

### Post by Cheesemill on 2012-06-05
> **Ilo1 said:**
> I've been struggling with this problem for at least 4 hrs today. I just want to say thanks! This was my problem as well. Someone should do something to fix that.
To fix what?

That is the expected and documented behaviour.
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

