---
title: "deleted the wrong package? not anymore!"
date: 2010-07-20
forum: General Help
---

### Post by d3v1150m471c on 2010-07-20
If you're a fallible creature like myself you will sometimes uninstall packages using apt-get commands and then scratch  your head when a dependency is missing and something that normally worked on your computer no longer does. So... I wrote this bash script that I think a lot of you will find more than useful. Execute this script before using any apt-get command and any package that is removed will be logged appropriately in ~/.oops . If you later find that something no longer works you can reinstall those packages ;). Just remember the "oops" script will continue to run until you turn it off. This can be done by pressing Ctrl+C while in your terminal.

[IMG]http://i264.photobucket.com/albums/ii174/Tempestas_Lingua/oops.png[/IMG]

```

#!/bin/bash
####################################################
# Make a directory for oops to function in or skip
# if the directory is already there.
if [ -e ~/.oops ]
  then
     sleep .01
  else
     mkdir ~/.oops
fi
####################################################
# Create a function to sift out apt-get commands
# from other commands and then capture apt-get's
# removed packages.

OOPS_TERMINAL() {
clear
name_log="$(date +%T)_$(date +%d%b%Y).log"
# Add a really annoying oops label to the terminal
# so the user doesn't forget it's on.
echo "
                       _ 
  ___   ___  _ __  ___| |
 / _ \ / _ \| '_ \/ __| |
| (_) | (_) | |_) \__ \_|
 \___/ \___/| .__/|___(_)
            |_|          "
echo
cd ~/.oops
if [ "$(ls ~/.oops)" ]
  then
     echo "Most recent packages removed
on `ls -lrt | awk '{ f=$NF }; END{ print f }' | awk -F "." '{print $1}'`: "
     cat `ls -lrt | awk '{ f=$NF }; END{ print f }'`
     echo
  else
     sleep .001
fi
cd $OLDPWD
read -p "$USER@$HOSTNAME:oops-$PWD$ " new_command

if [[ $new_command == *apt-get* ]]
  then
     echo "processing, please wait..."
     $new_command -y > ~/.oops/.step1
     sed -n '/REMOVED:/,/upgraded/p' ~/.oops/.step1 > ~/.oops/.step2
     awk 'FNR>1' ~/.oops/.step2 > ~/.oops/.step3
     sed '$d' < ~/.oops/.step3 > ~/.oops/$name_log
  else
     $new_command
fi
find ~/.oops/* -size 0c -exec rm {} \;
}

while [ 1 ]; do
OOPS_TERMINAL
done

```

---

### Post by lkjoel on 2010-07-20
Nice script!
Just to tell you, it exited with status 1. (exit 1)
Not good for Terminal Enhancements.
Usually you should exit with status 0. (exit 0)
If you want to know what is the difference, after you exit, type:
```
echo $?
```

---

### Post by d3v1150m471c on 2010-07-20
> **lkjoel said:**
> Nice script!
Just to tell you, it exited with status 1. (exit 1)
Not good for Terminal Enhancements.
Usually you should exit with status 0. (exit 0)
If you want to know what is the difference, after you exit, type:
```
echo $?
```

Thanks for the compliment. I'm aware of the exit statuses but i usually just go with exit 0. The oops script above is part of a small program I'm working on and the apps I work on report their own detailed errors. Nonetheless, thanks for the heads-up

Here's the first version of that program btw: [B][Apt-oops]("https://sourceforge.net/projects/apt-oops/")

[/B]

---

### Post by lkjoel on 2010-07-20
I think that you should post this in the Tutorials and Tips section of Ubuntu Forums.

---

### Post by d3v1150m471c on 2010-07-20
i totally forgot about it. hopefully one of the mods can switch it over for me.

from apt-oops 1.0:
```

d3v11@laptop:~/Projects/apt-oops_1_0_0$ oops

                                 _ 
            ___   ___  _ __  ___| |
           / _ \ / _ \| '_ \/ __| |
          | (_) | (_) | |_) \__ \_|
           \___/ \___/| .__/|___(_)
                      |_|          

apt-oops_1.0.0: supplements the usage of apt-get commands
by providing safer usage and a logging and recovery 
system of removed packages.

usage: oops [ -O, -F, or -R ]
                   OR
       oops [ -S ] [ -O, -F, or -R ]
                   OR
       oops [ -v, -c, or -h ]

-S Turns off the safety switch. apt-oops will not allow
   you to use apt-get commands if packages will be
   removed. To allow the removal of packages for
   the following options you must set this flag.

-O Runs apt-oops in interactive mode. Use this mode
   prior to running apt-get commands. oops will
   log all the removed packages in /home/d3v11/.oops
   Most non apt-get commands can be used while in
   interactive mode but it is not recommended.
   Press Ctrl+C to exit interactive mode.

-F Reinstalls packages from a specific list created
   in /home/d3v11/.oops . Example:

   oops -F ~/.oops/11:54:27_20Jul2010.list

-R Reinstalls the most recently removed list of
   packages logged in /home/d3v11/.oops .

-M Provides a list of the most recently removed
   packages.

-v Provides the version of apt-oops.

-c Provides contact information for the apt-oops
   author.

-h Gives a brief summary of the program, its usage, and its
   options.

```

---

