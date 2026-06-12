---
title: "startup script not executing?"
date: 2010-10-26
forum: General Help
---

### Post by ryanfx on 2010-10-26
Hello all,

```

ryan@TehLaptop:~$ uname -a
Linux TehLaptop 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux
ryan@TehLaptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick

```

I have a start up script which remaps a key on my keyboard.  It is currently in /etc/init.d/

```

ryan@TehLaptop:~$ ls -l /etc/init.d/fixkeys 
-rwxr-xr-x 1 ryan ryan 91 2010-06-18 21:09 /etc/init.d/fixkeys

```

the contents of the file are as follows:

```

#!/bin/bash
#Fixes the stupid key setup on my laptop
xmodmap -e "keycode 108=Alt_R"
exit 0

```

I have it in my system -> preferences -> startup applications as the command "/etc/init.d/fixkeys" however it is not being executed at startup (I have to manually run the script every time I login).  If I manually run it, it works perfectly.  I have tried moving it to a directory in my home folder but that did not solve anything.

Any ideas of what I might be doing wrong?  Or am I not understanding what a startup application actually is?

---

### Post by trikster_x on 2010-10-26
have you set manually set the program to be executable in the permissions tab of the properties menu?

---

### Post by ryanfx on 2010-10-26
> **trikster_x said:**
> have you set manually set the program to be executable in the permissions tab of the properties menu?

See (now) attached picture in first post.

---

### Post by trikster_x on 2010-10-26
You do have it set up in the startup applications menu correctly, what might be wrong is the executable bit might not be set.  Type in a terminal:

```
sudo chmod 770 /etc/init.d/fixkeys
```

---

### Post by ryanfx on 2010-10-26
> **trikster_x said:**
> You do have it set up in the startup applications menu correctly, what might be wrong is the executable bit might not be set.  Type in a terminal:

```
sudo chmod 770 /etc/init.d/fixkeys
```

also in the first post, I had done an ls -l for that very reason =P

---

### Post by gunsten on 2010-10-26
The command should be: bash /etc/init.d/fixkeys
or however you usually run your scripts.

The problem isnt in permission mode, or you wouldnt be able to execute the script manually either.

Edit: Perhaps I need to clarify, on the command line in *Edit Startup Program *you should run the command as you usually do in the terminal.

Perhaps you run scripts with ./ syntax, why this wouldnt be as evident. That will probably work aswell, I dont know.

---

### Post by trikster_x on 2010-10-26
So you did :D

The only thing I cn see that might mess it up is your shebang.  Try putting a space after the !

```
#! /bin/bash
```

@gunsten:  You actually can run a script from the command line without making it executable.  You just won't be able to run on double click or run it through a launcher or as a startup program. And proper entry syntax in a terminal would be /etc/init.d/fixkeys.

---

### Post by ryanfx on 2010-10-26
> **trikster_x said:**
> So you did :D

The only thing I cn see that might mess it up is your shebang.  Try putting a space after the !

```
#! /bin/bash
```

@gunsten:  You actually can run a script from the command line without making it executable.  You just won't be able to run on double click or run it through a launcher or as a startup program. And proper entry syntax in a terminal would be /etc/init.d/fixkeys.


Neither putting a space in the she-bang, or executing with 'sh' works... its baffling me.

---

### Post by trikster_x on 2010-10-26
have you tried just entering the terminal command into the startup command space, instead of using a script?

---

### Post by gunsten on 2010-10-26
> **trikster_x said:**
> So you did :D
@gunsten:  You actually can run a script from the command line without making it executable.  You just won't be able to run on double click or run it through a launcher or as a startup program. And proper entry syntax in a terminal would be /etc/init.d/fixkeys.


Well, I had just the same issue quite recently. I got bash in front of my script in the command entry, solved it.

Also there seems to be different characteristics to different shells: I've written some scripts that couldnt be execed with either ./ or sh, but works fine with bash. Just try putting bash in on the command line and see if that works, assuming you got the permissions correct.

---

### Post by ryanfx on 2010-10-26
> **gunsten said:**
> Well, I had just the same issue quite recently. I got bash in front of my script in the command entry, solved it.

Also there seems to be different characteristics to different shells: I've written some scripts that couldnt be execed with either ./ or sh, but works fine with bash. Just try putting bash in on the command line and see if that works, assuming you got the permissions correct.

Well I did some more troubleshooting and added a: "touch /home/ryan/test" line to my bash script.  It appears as if the script IS running, however the key is not getting remapped like it should.  Perhaps the script is running too early?  Anyone have an idea of how to properly fix this?

---

### Post by gunsten on 2010-10-26
> **ryanfx said:**
> Well I did some more troubleshooting and added a: "touch /home/ryan/test" line to my bash script.  It appears as if the script IS running, however the key is not getting remapped like it should.  Perhaps the script is running too early?  Anyone have an idea of how to properly fix this?

A quick (but not very proper) fix would be to put a long sleep in the beginning of the script. It is probably not fool proof, but still a good next step in the troubleshooting.

For a proper fix, there should be a configure file where you can do the mapping.

---

### Post by ryanfx on 2010-10-26
> **gunsten said:**
> A quick (but not very proper) fix would be to put a long sleep in the beginning of the script. It is probably not fool proof, but still a good next step in the troubleshooting.

For a proper fix, there should be a configure file where you can do the mapping.

sleep was definitely something I wanted to avoid =/

---

### Post by ryanfx on 2010-10-27
Any further ideas?

---

### Post by gunsten on 2010-10-29
> **ryanfx said:**
> Any further ideas?

As I said earlier, try adding the sleep command. At least it will help you determine if you're right in the assumption that the issue is in fact that the script is loaded too early in the boot process.

---

