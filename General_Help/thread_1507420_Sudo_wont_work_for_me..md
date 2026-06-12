---
title: "Sudo wont work for me."
date: 2010-06-11
forum: General Help
---

### Post by INSANENEIVIESIS on 2010-06-11
Ok im in the middle of building my android ROM from source in Ubuntu 10.04. and  i  enter the repo command

[PHP]repo init -u git://android.git.kernel.org/platform/manifest.git -b eclair[/PHP]

and i get this error 

```
exec: 23: python: not found
```so i need to install python so i enter the command 

```
sudo apt-get install python
```and i get this error message back

```
Command 'sudo' is available in '/usr/bin/sudo'
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
sudo: command not found
```any help is really appreciated.

---

### Post by oldos2er on 2010-06-11
Can you post the output of ```
echo $PATH
``` ?

---

### Post by WorMzy on 2010-06-11
After doing what oldos2er said, check the output. It should say ```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
``` If it doesn't then run this: ```
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
``` You should be able to run sudo (and other executables) again.

---

### Post by INSANENEIVIESIS on 2010-06-11
this is what i got back from

echo $PATH

```
/bin:/home/aaroncarpinteri/bin
```

---

### Post by kevin.krenz on 2010-06-11
The value of the PATH variable is a list of the directories that the shell will search for any commands that you give. Since the sudo command isn't in any of the directories in your PATH variable and it's not a built-in command, it doesn't work.

Did you do anything to change the value of this variable? Maybe in the .bashrc or .bash_profile files in your home directory? Using WorMzy's suggestion should fix it for you.

---

### Post by oldos2er on 2010-06-11
> **INSANENEIVIESIS said:**
> this is what i got back from

echo $PATH

```
/bin:/home/aaroncarpinteri/bin
```

You haven't changed any system permissions, have you?

---

