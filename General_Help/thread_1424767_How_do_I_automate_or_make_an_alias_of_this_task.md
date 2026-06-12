---
title: "How do I automate or make an alias of this task?"
date: 2010-03-08
forum: General Help
---

### Post by Rytron on 2010-03-08
Hi.
Could I make an alias of this task?

I want an alias to move [COLOR="Navy"]~/.sportstracker[/COLOR] to [COLOR="Navy"]~/Documents/Software/SportsTracker_4.1.1[/COLOR] and then zip it and name the zip file like this [COLOR="Indigo"]SportsTrackerBackup_yyyy-mm-dd[/COLOR] (example: [COLOR="Indigo"]SportsTrackerBackup_2010-03-08[/COLOR])

Note: I don't mind how the archive is compressed, 7z, rar, zip, tar, etc. Although the higher the compression the better.

Else, is there a way to automate this daily or once a week?

---

### Post by falconindy on 2010-03-08
i'd write it as a bash function. It works the same and goes in the same place, but follows slightly different rules:

```
stracker() {
  gzip ~/.sportstracker
  mv -v ~/.sportsracker.gz ~/Documents/Software/SportsTracker_4.11/SportsTrackerBackup_$(date +%F)
}
```

If you wanted this automated, you could take the two real commands out of this and throw them into a script file for use as a cron job. There would be some further changes necessary though.

---

### Post by Rytron on 2010-03-08
Thank you falconindy. It does not work though.

Just a quick correction on your code:

```
stracker() {
  gzip ~/.sportstracker
  mv -v ~/.sports**[COLOR="Cyan"]t[/COLOR]**racker.gz ~/Documents/Software/SportsTracker_4.11/SportsTrackerBackup_$(date +%F)
}
```

I made this file like so from your code [attached].

---

### Post by Rytron on 2010-03-11
Does anyone know how to solve this?

Is it possible to combine two commands in one alias? For example, something to do this:

[LIST=1]
[*]gzip ~/.sportstracker
[*]mv -v ~/.sportsracker.gz ~/Documents/Software/SportsTracker_4.11/SportsTrackerBackup
[/LIST]

I am not certain the above syntax is 100% correct though.

---

### Post by sisco311 on 2010-03-11
you have to add the function to the ~/.bashrc file & (re)source the file:
```
. ~/.bashrc
```or start a new bash session.

if you plan to write more function, you may want to keep them in a separate file (i.e. ~/.bash_functions) & add something like:
```
[ -f ~/.bash_functions ] && . ~/.bash_functions
```
to the ~/.bashrc file.

See:
```
man bash | less +/"\. *filename *\[arguments\]"
```

---

### Post by Rytron on 2010-03-29
I'm lost.

I just want an easy way to archive [COLOR="DarkSlateBlue"]~/.sportstracker[/COLOR] & move it to the [COLOR="Navy"]SportsTrackerBackup[/COLOR] at [COLOR="Indigo"]~/Documents/Software/SportsTracker_4.11/SportsTrackerBackup[/COLOR]

---

### Post by ScarletWyvern on 2010-03-29
Why are you trying to make an alias run multiple commands?

An easier way is to make a shell script that performs all the actions you need, and have the alias just run the script.

Although, if you wanted to, you could probably use "command 1 && command 2" but I'm not entirely sure.

---

### Post by Rytron on 2010-03-30
I tried this:
```
:~$ gzip ~/.sportstracker && mv -v ~/.sportsracker.gz ~/Documents/Software/SportsTracker_4.11/SportsTrackerBackup
```

The output was:
```
gzip: /home/rytron/.sportstracker is a directory -- ignored
```

---

### Post by Bachstelze on 2010-03-30
You cant gzip a directory. You want something like

```
tar czvf ~/sportstracker.tar.gz ~/.sportstracker
```

---

### Post by Rytron on 2010-03-30
**Input:**
```
tar czvf ~/sportstracker.tar.gz ~/.sportstracker && mv -v ~/.sportsracker.tar.gz ~/Documents/Software/SportsTracker_4.11/SportsTrackerBackup
```

**Output:**
```
tar czvf ~/sportstracker.tar.gz ~/.sportstracker && mv -v ~/.sportsracker.tar.gz ~/Documents/Software/SportsTracker_4.11/SportsTrackerBackup
tar: Removing leading `/' from member names
/home/rytron/.sportstracker/
/home/rytron/.sportstracker/sport-types.xml
/home/rytron/.sportstracker/weights.xml
/home/rytron/.sportstracker/st-options.xml
/home/rytron/.sportstracker/notes.xml
/home/rytron/.sportstracker/exercises.xml
/home/rytron/.sportstracker/st.dlg.statistic.session.xml
/home/rytron/.sportstracker/st.dlg.overview.session.xml
/home/rytron/.sportstracker/st.dlg.options.session.xml
/home/rytron/.sportstracker/st.dlg.weight.session.xml
/home/rytron/.sportstracker/st.dlg.sporttype_list.session.xml
/home/rytron/.sportstracker/st.dlg.sporttype.session.xml
/home/rytron/.sportstracker/mainFrame.session.xml
/home/rytron/.sportstracker/st.dlg.exercise.session.xml
/home/rytron/.sportstracker/st.dlg.statistic_results.session.xml
mv: cannot stat `/home/rytron/.sportsracker.gz': No such file or directory
```

I got the same output for just:
```
tar czvf ~/sportstracker.tar.gz ~/.sportstracker
```

---

### Post by Rytron on 2010-03-30
Eureka!

```
tar czvf ~/Documents/Software/SportsTracker_4.1.1/SportsTrackerBackup.tar.gz ~/.sportstracker
```

All thats left is to put this into an alias.
```
alias stb='tar czvf ~/"Documents/Software/SportsTracker_4.1.1/SportsTrackerBackup.tar.gz" ~/.sportstracker'
```

:popcorn:

---

### Post by Rytron on 2010-03-30
The only downside is that it backs the .sportstracker file in an archive with this structure:
[COLOR="Indigo"]/home/rytron/.sportstracker/[/COLOR]
Do I need to change something in the [COLOR="RoyalBlue"]tar czvf[/COLOR] part (or use another form of compression?). It's no big deal but if I could only backup the .sportstracker without the full path structure, it'd be better.

---

### Post by kaibob on 2010-03-30
> **Rytron said:**
> ..Do I need to change something in the [COLOR="RoyalBlue"]tar czvf[/COLOR] part (or use another form of compression?). It's no big deal but if I could only backup the .sportstracker without the full path structure, it'd be better.

I use zip rather than tar, but zip saves relative directores. For example, if the working directory is my home directory, the following command saves the documents directory and all files in the documents directory but not the full path. 

```
zip test.zip documents/*
```

If I unzip test.zip, it creates the documents directory in the current working directory.

Zip also has an option that ignores all directories, but if I understand correctly you want to retain the one directory.

---

### Post by Rytron on 2010-03-31
> **kaibob said:**
> I use zip rather than tar, but zip saves relative directores. For example, if the working directory is my home directory, the following command saves the documents directory and all files in the documents directory but not the full path. 

```
zip test.zip documents/*
```

If I unzip test.zip, it creates the documents directory in the current working directory.

Zip also has an option that ignores all directories, but if I understand correctly you want to retain the one directory.

How do I get zip to **ignore all directories**? What **option** do I use?

This kept the full path structure also just like tar did. The only difference was the better compression ratio that zip offered.
```
alias stb='zip ~/"Documents/Software/SportsTracker_4.1.1/SportsTrackerBackup.zip" ~/.sportstracker'
```

---

### Post by pbrane on 2010-03-31
try bzip2

```

tar cjvf ~/Documents/Software/SportsTracker_4.1.1 SportsTrackerBackup.tar.bz2 ~/.sportstracker

```

Also the way to get only the files in ~./sportstracker is to *cd* to that directory and archive from there.

```

cd ~/.sportstracker && tar cjvf ~/Documents/Software/SportsTracker_4.1.1/SportsTrackerBackup.tar.bz2 *

```

---

### Post by kaibob on 2010-03-31
> **Rytron said:**
> How do I get zip to **ignore all directories**? What **option** do I use?

This kept the full path structure also just like tar did. The only difference was the better compression ratio that zip offered.
```
alias stb='zip ~/"Documents/Software/SportsTracker_4.1.1/SportsTrackerBackup.zip" ~/.sportstracker'
```

You use the -j option, which is described in the man page as:

> Store  just  the  name  of a saved file (junk the path), and do not store directory names. By default, zip will store the full  path  (relative  to the current path).

Thus, for example

```
zip -j test.zip /home/kaibob/documents/*
```

As to your second question, execute the following in a terminal window while the current working directory is the parent directory of .sportstracker. This is a bit cumbersome with an alias and might best be handled as a function or separate shell script. 

```
zip ~/"Documents/Software/SportsTracker_4.1.1/SportsTrackerBackup.zip" .sportstracker/*
```

---

### Post by Rytron on 2010-04-01
Thank you all for your assistance. Cheers.

---

