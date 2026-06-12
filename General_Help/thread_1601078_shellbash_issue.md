---
title: "shell/bash issue"
date: 2010-10-19
forum: General Help
---

### Post by U_buntu on 2010-10-19
How do you get scripts to run from anywhere in terminal instead of the directory in which it was created?

---

### Post by amauk on 2010-10-19
either use an absolute path
eg. instead of```
cd ~/scripts
./my_script
```
do```
~/scripts/my_script
```

Or, put the scripts in one of the $PATH directories
Eg. /usr/local/bin

---

### Post by gmargo on 2010-10-20
> **U_buntu said:**
> How do you get scripts to run from anywhere in terminal instead of the directory in which it was created?

Place them in a directory along your $PATH.

If it's something that a lot of people want, usually you'd put it in /usr/local/bin/ (which is included in the default $PATH).

If it's something just for you, then put it in $HOME/bin/ (if it exists, it is added to $PATH by the default $HOME/.profile).

---

### Post by U_buntu on 2010-10-20
Neither work, the second gives me a permission error.

---

### Post by Cuddles McKitten on 2010-10-20
Did you make sure that the script is executable?

```
chmod +x /filename/goes/here
```Alternately, you can always just call the script with whatever binary will be running it: e.g.

sh script.sh
awk -f thingy.sh
perl script.pl

---

### Post by bodhi.zazen on 2010-10-20
> **U_buntu said:**
> Neither work, the second gives me a permission error.

1. Put the scripts in a generic location. This is best if the scripts are shared. IMO the "default" location would be:

/usr/local/bin

2. If the scripts are for you as a single user, put them in ~/bin (you will need to make the directory).

Then add ~/bin to your path. It should already be in ~/.bashrc, but if not, add these lines:

```
if [ -d "$HOME/bin" ]; then
  PATH="$PATH:$HOME/bin"
fi
```

You then will need to start a new shell or log off and back on.

To make a script executable, use chmod

```
chmod a+x ~/bin/*
```

---

### Post by U_buntu on 2010-10-20
Yes it is executable, and i tried to move it to the bin folder but i dont have the "permission", though i do.

---

### Post by WorMzy on 2010-10-20
You don't have permission to move files into /usr/local/bin, that directory is owned by root (and should remain as such). You can copy/move your file there by adding "sudo" to the start of your cp/mv command. e.g.

```
sudo mv ~/myscript.sh /usr/local/bin/
```

---

### Post by bodhi.zazen on 2010-10-21
IMO, any script outside of your home should be owned by root.

You can set permissions so others can read or execute the script, but IMO only root should have write permissions.

This applies to /usr/local/bin

You should not keep personal scripts / files in /bin or /sbin , use /usr/local/bin (Other distros use /opt rather then /usr/local).

Scripts in ~/bin I keep with permissions of 700.

---

