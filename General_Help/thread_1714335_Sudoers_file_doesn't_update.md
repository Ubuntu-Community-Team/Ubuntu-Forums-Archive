---
title: "Sudoers file doesn't update?"
date: 2011-03-25
forum: General Help
---

### Post by NertSkull on 2011-03-25
So I'm trying to run a script that needs root privileges without typing in the password.

Basically I want to copy a file from my documents folder into /etc/X11 to overwrite my xorg.conf.  I do this because I will have my computer switch from my monitors to my TV when I watch a movie.  But I'd like to be able to make it a clickable icon so I don't have to type in cp /... /etc/...

This is my "script"

```
sudo cp /home/nertskull/Documents/xorg.conf_TV /etc/X11/xorg.conf
```

Then I read a lot of places that said to add this to the sudoers file (sudo visudo)

```
nertskull ALL = NOPASSWD: /home/nertskull/Documents/switch_TV.sh
```

I've done all that, and I still get asked for my password when I run that file.

I've tried

nertskull ALL = ...
%nertskull ALL = ...
%users ALL = ...
%admin ALL = ...

I'm sure it's something simple I'm overlooking, but I've read 5 different threads on this, and I can't find anything they did that I'm not doing.

Can someone point me in the right direction?

Also, here is my sudoers file, because I know location within the file matters.  But what I read said I should be putting my stuff at the end.

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
nertskull ALL = NOPASSWD: /home/nertskull/Documents/switch_TV.sh

```

---

### Post by WorMzy on 2011-03-25
Take "sudo" out of the script, and then call the script with sudo.

If you run the script as a normal user, then it will still ask you for your password when it reaches the line containing "sudo" because the command that's trying to run is "cp", not "/home/nertskull/Documents/switch_TV.sh". If you run the script as the super user (by way of sudo), then it won't ask for your password when it gets to that line (even if you left the "sudo" in) because the whole script would be running as root already.

---

### Post by MooPi on 2011-03-25
It may just be a slight edit job as here is my working sudoers addition, ```
%grift ALL=(ALL)NOPASSWD:/sbin/shutdown
```

---

### Post by NertSkull on 2011-03-25
> **WorMzy said:**
> Take "sudo" out of the script, and then call the script with sudo.

If you run the script as a normal user, then it will still ask you for your password when it reaches the line containing "sudo" because the command that's trying to run is "cp", not "/home/nertskull/Documents/switch_TV.sh". If you run the script as the super user (by way of sudo), then it won't ask for your password when it gets to that line (even if you left the "sudo" in) because the whole script would be running as root already.

So I'm not sure I understood 100% what you meant by all that.  But maybe, this is what I did and it still doesn't work.

I created a new file called copy_xorg_TV.sh that says this

```
cp /home/nertskull/Documents/xorg.conf_TV /etc/X11/xorg.conf
```

Then I created another script to call that one.  Because it sounded from what you said that I can't "run the script as a normal user".  So the 2nd one called switch_TV.sh looks like this

```
sudo bash /home/nertskull/Documents/copy_xorg_TV.sh
```

Then for good measure I put both of those in the sudoers file

```

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
nertskull ALL = NOPASSWD: /home/nertskull/Documents/copy_xorg_TV.sh
nertskull ALL = NOPASSWD: /home/nertskull/Documents/switch_TV.sh

```

But still, if I double click on switch_TV.sh in nautilus and run in terminal it doesn't work.  Maybe I didn't understand though what exactly I was supposed to do.

---

### Post by NertSkull on 2011-03-25
> **MooPi said:**
> It may just be a slight edit job as here is my working sudoers addition, ```
%grift ALL=(ALL)NOPASSWD:/sbin/shutdown
```

I tried formatting like that, and still no go for me.

---

### Post by WorMzy on 2011-03-25
> **NertSkull said:**
> But still, if I double click on switch_TV.sh in nautilus and run in terminal it doesn't work.  Maybe I didn't understand though what exactly I was supposed to do.

No, I didn't explain it very well.

Your changes in sudoers says that, when you run the script with sudo, it shouldn't ask you for a password. But you're not running the script with sudo, you're calling sudo from inside the script.

> ```
sudo bash /home/nertskull/Documents/copy_xorg_TV.sh
```
This example won't work because you're calling *bash* with sudo, not the script.

> nertskull ALL = NOPASSWD: /home/nertskull/Documents/copy_xorg_TV.sh
nertskull ALL = NOPASSWD: /home/nertskull/Documents/switch_TV.sh
Both of these say that, when you run

```
sudo /home/nertskull/Documents/copy_xorg_TV.sh
```
or
```
sudo /home/nertskull/Documents/switch_TV.sh
```

sudo shouldn't ask you for your password.

I hope that makes things clearer. You don't need the second script, you just need to put "sudo /home/nertskull/Documents/switch_TV.sh" as the launcher's command.

---

### Post by NertSkull on 2011-03-25
SUCCESS!

That makes much more sense now.  And now I have it working.  Thats much easier, and now my wife can't complain that she can't switch to watch TV without me.

Thank you for the help!

---

