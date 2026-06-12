---
title: "Parsing for configfile not working"
date: 2011-08-15
forum: General Help
---

### Post by jjpcexpert on 2011-08-15
EDIT: Why is no-one replying?

I am having trouble creating a parser for a configuration file format I created in my bedroom. Maybe reinventing the wheel, but hey, at least I have created a possibly already created config format..
Here the (debugging) parser is so far:
```
#!/bin/bash
IFS=" "
while read optname option ; do
    eval $optname=$option
    if [ $optname != program ] ; then
        echo "Setting $optname is $(echo $option | tr -d \")"
    fi
done < filegoeshere.rc
```filegoeshere.rc:
```
program "Test file"
message0001 "Hello everyone."
message0002 "Blah, blah, blah..."
opt1 "yes"
opt2 "no"
```Attempts to use the memory outputs (didn't exist):
```
jack@radio-player:~/Desktop$ ./confparser.sh 
/home/jack/.themes/SeriousShiki-Attmp2/gtk-2.0/panel.rc:9: Unable to locate image file in pixmap_path: "./Panel/panel-bg.png"
Setting message0001 is Hello everyone.
Setting message0002 is Blah, blah, blah...
Setting opt1 is yes
Setting opt2 is no
jack@radio-player:~/Desktop$ echo -e "$message0001\n$message0002"


jack@radio-player:~/Desktop$ echo -e "$message0001 $message0002"
 
jack@radio-player:~/Desktop$ echo "$message0001 $message0002"
 
jack@radio-player:~/Desktop$ ./confparser.sh 
Setting message0001 is Hello everyone.
Setting message0002 is Blah, blah, blah...
Setting opt1 is yes
Setting opt2 is no
jack@radio-player:~/Desktop$ ./confparser.sh 
Usage: file [-bchikLNnprsvz0] [--apple] [--mime-encoding] [--mime-type]
            [-e testname] [-F separator] [-f namefile] [-m magicfiles] file ...
       file -C [-m magicfiles]
       file [--help]
./confparser.sh: line 4: everyone.: command not found
Setting message0001 is Hello everyone.
./confparser.sh: line 4: blah,: command not found
Setting message0002 is Blah, blah, blah...
Setting opt1 is yes
Setting opt2 is no
jack@radio-player:~/Desktop$ ./confparser.sh 
Setting message0001 is Hello everyone.
Setting message0002 is Blah, blah, blah...
Setting opt1 is yes
Setting opt2 is no
jack@radio-player:~/Desktop$ ./confparser.sh 
Setting message0001 is Hello everyone.
Setting message0002 is Blah, blah, blah...
Setting opt1 is yes
Setting opt2 is no
jack@radio-player:~/Desktop$ ./confparser.sh 
Setting message0001 is Hello everyone.
Setting message0002 is Blah, blah, blah...
Setting opt1 is yes
Setting opt2 is no
jack@radio-player:~/Desktop$ echo $opt1

jack@radio-player:~/Desktop$ 
```The problem lies in setting the optname variable to the option.
Could somebody create a parser based on this one that actually does the following things:
 - Tells us the option name and it's value
 - Sets the option name, as a variable, to the option value
 - Preferably uses a function that may be embedded in other bash programs

Language of the echo prompt may be any, it just MUST output my config file's option names and values, and must put them in that terminal's memory.

Helpful would be a writer program for this.

It cannot be too complicated (i.e. must use only commands found on a base Debian installation and nothing more) because the test system for me is Debian Squeeze with some extras, e.g. Compiz and the non-free firmware microcode.:(

---

