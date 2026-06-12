---
title: "why doesnt this bash command work?"
date: 2010-04-08
forum: General Help
---

### Post by Søren on 2010-04-08
cd /Desktop/

??


I can change to just about any dir of my file system with cd /filename/

eg cd /var/ or cd /opt/
it will skip me up or down the tree to get there

but when if go cd /Desktop/ 
or 
cd /myuseraccount/

is get:  bash: cd: /Desktop/: No such file or directory
i have to be right next to the directory to get there.

i dont get it. :(

why is this?

---

### Post by philinux on 2010-04-08
Just use 

cd Desktop

Desktop is not directly off / root it's in /home/username/Desktop

/home is and /etc is directly off /

You can only use cd /directory to a directory that is at level one off /.

---

### Post by Søren on 2010-04-08
ahh. i dont understand. isnt everything a sub of /root?

no big deal i can just use cd home/me/Desktop to nav from anywhere.
cd Desktop will only work if you are next door to directory.

was just curious mostly.

cheers.

---

### Post by CharlesA on 2010-04-08
Everything is located off the root directory, but the original command is telling it to cd into a folder located off the root.

The Desktop folder is located in your home directory, which can be cd'd to by just using "cd."

You can also use cd ~/Desktop from anywhere.

---

### Post by cjhabs on 2010-04-08
If you start a path with "/" you are anchoring that path to start at the root of the file system.
If you start a path without the "/" it is interpreted as relative to your current directory.
If you start a path with "~/" it is interpreted relative to your user home folder (typically /home/username where username is your user account).
So you want "cd ~/Desktop". Simply "cd Desktop" will work _if_ you are in your home directory, which is where you are by default when you start a new shell.

HTH

---

### Post by slakkie on 2010-04-08
BTW, cd ~/Desktop will not work in a script, use $HOME instead of the ~. cd $HOME/Desktop will work in scripts and with normal usage.

---

### Post by Søren on 2010-04-08
ahh ha!

got it.

chees guys.

---

