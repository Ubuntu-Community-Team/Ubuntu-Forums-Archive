---
title: "backup script help"
date: 2009-12-18
forum: General Help
---

### Post by boabby on 2009-12-18
hi people i am starting a college course in january and linux is a part of it, so trying to get some experiance be fore starting got a hold of some linux tutorials but have got stuck at scripting, what i have to do is create a backup/restore script for users to backup files in the appropriate directory. types of files/direcectories ar word processing, spreadsheets and picture files, do not know where to start even with google searches, still lost. so was hoping someone could write a script with explanations so i could understand it.
thanks for any help.

---

### Post by xifer on 2009-12-18
Hi,

to start with type 

man tar

in a terminal window

then

man cpio


Search this site for tar examples - there are quite a few about.

---

### Post by boabbyrab on 2009-12-18
hiya thanks for quick reply, i have seen tar being used a in few scripts and i understand i would need it but still dont understand the basis of it and other commands like else and if and what to put into the script, and dont even know if scripting will be getting taught in class but want to cover all the bases and its the last question of the tutorial. cheers

---

### Post by indytim on 2009-12-18
Here's a couple of older links I had laying about for getting started in BASH programming.  Hopefully it will give you enough to get started.

[http://http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html]("http://http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html")

[http://http://linux.org.mt/article/terminal]("http://http://linux.org.mt/article/terminal")

[http://http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html]("http://http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html")

IndyTim

---

### Post by xifer on 2009-12-18
> **boabbyrab said:**
> hiya thanks for quick reply, i have seen tar being used a in few scripts and i understand i would need it but still dont understand the basis of it and other commands like else and if and what to put into the script, and dont even know if scripting will be getting taught in class but want to cover all the bases and its the last question of the tutorial. cheers

Hi - explaining IF and ELSE is a bit out of scope here - suffice to say every programming/scripting language has a version of this.  Test some condition and when it is true perform a set of instructions when it is false perform a different set. e.g.
here's an extract from a script of mine - it creates a bunch of stuff in various databases from sql script files
First define the shell to use for the script then some variables
then it creates directories
some user input of variables
sort of gives you an idea of how stuff works

```

#!/bin/bash
#these are the targets
var1=/cygdrive/r/scripts/mychoice_oracle_re01p3
var2=/cygdrive/r/scripts/mychoice_sqlserver_re01p3
#base for version control
var3=/cygdrive/c/_subversion/re01p03/mychoice
#create targets
mkdir -p $var1 
mkdir -p $var2
echo -n "enter top level directory [$var3]: " 
read var4
if [ "$var4" = "" ]; then
   var3=/cygdrive/c/_subversion/re01p03/mychoice
else
   var3="$var4"
fi
echo -n "oracle or sqlserver [oracle] ?"; read dbtype
if [ "$dbtype" = "" ]; then
   dbtype="oracle"
#else
 #  dbtype="sql server"
fi

```

---

### Post by boabbyrab on 2009-12-18
cheers for help, i have seen a few of those links before but i think the question on tutorial wants options  i.e press 1 for backup 2 for restore.
i know what i want is probably staring at me right in the face but i just cannot see it. i can make the directories word processing etc and put files in each of the directories but its the coding inbetween the bin/bash and fi bit that throws me and does the script make the directories automatically.
sorry for this dont really have anyone to ask for at least 3 weeks and was hoping to have it finished for weekend if possible.
again sorry for being a noob and probably asking stupid questions

---

### Post by xifer on 2009-12-18
> **boabbyrab said:**
> cheers for help, i have seen a few of those links before but i think the question on tutorial wants options  i.e press 1 for backup 2 for restore.
i know what i want is probably staring at me right in the face but i just cannot see it. i can make the directories word processing etc and put files in each of the directories but its the coding inbetween the bin/bash and fi bit that throws me and does the script make the directories automatically.
sorry for this dont really have anyone to ask for at least 3 weeks and was hoping to have it finished for weekend if possible.
again sorry for being a noob and probably asking stupid questions

no worries - we all have to start somewhere!

as for 1 to backup, 2 to restore - you can do that by adjusting the echo lines in the extract I posted.

as for creating dirs  - check out the command 'test' if it exists use it else create it.

so you want a structure something like this - ( I'm not going to do the exact syntax here)

if [inputvar = 1] then
   if [test [...] ] then
      mkdir
   fi
   tar cf
else
   tar xf
fi

---

