---
title: "removing  a string of files"
date: 2011-04-26
forum: General Help
---

### Post by kaykav on 2011-04-26
good evening
            I don,t know how to do this,yet. I have a list of files in my home directory. About one-third of them have a similar string in their names (text files). I want to remove them with one command. example:  
.bash_logout
.bash_logout.before_restore_2011-03-21_07.15.36.372112
.bash_profile
.bash_profile~
.bash_profile.before_restore_2011-03-21_07.15.36.372112
     The files with the... restore_2011.....are the files I want to remove. I'm not sure of the correct command....Thank you

---

### Post by cipherboy_loc on 2011-04-26
From the terminal:

```

rm ~/.bash_*restore*

```
should do it. 


Cipherboy

---

### Post by kaykav on 2011-04-26
Hi again
          actually I have files with different beginning names:

.gtk-bookmarks.before_restore_2011-03-21_07.15.36.372112
.gvfs
.hardinfo
.ICEauthority
.ICEauthority.before_restore_2011-03-21_07.15.36.372112
          As you can see the beginning names are different,but they all have (.before_restore_2011-03-21_07.15.36.372112) at the end of each file. If they all began with  (.bash_) your recommendation would do fine. So how do I isolate those particular files to remove them..Sorry for the confusing statements....Thank you

---

### Post by Kurisu86 on 2011-04-26
Do this
```
rm *.before_restore*
```This will remove all files that have the term ".before_restore" somewhere in the file name. The * acts as a wildcard.

You could also
```
rm *.before_restore_2011-03-21_07.15.36.372112
```If you want to just remove ones with that specific date and you have other backups with the same naming convention.

Hope this helps.

---

### Post by kaykav on 2011-04-27
Good morning
             Tried it. I get an error message:
$rm *.before_restore_2011-03-21_07.15.36.372112*
rm: cannot remove `*.before_restore_2011-03-21_07.15.36.372112*': No such file or directory
   I type the command   ls -a|less
   (I took part of the list to show you the files do exist)
.gtk-bookmarks
.gtk-bookmarks.before_restore_2011-03-21_07.15.36.372112
.gvfs
.hardinfo
.ICEauthority
.ICEauthority.before_restore_2011-03-21_07.15.36.372112
.icons
.idlerc
.isomaster
.isomaster.before_restore_2011-03-21_07.15.36.372112
.java
.joe_state
.joe_state.before_restore_2011-03-21_07.15.36.372112 
   I then type command  rm *.before_restore_2011-03-21_07.15.36.372112*
I get an error   rm: cannot remove `*.before_restore_2011-03-21_07.15.36.372112*': No such file or directory
   If I use GUI I can move them to trash easily.
       I'm sure there is an easy answer,but some time easy answers are hard to find.
   I'll pursue this to the end........Thanks again

---

### Post by Vaphell on 2011-04-27
remove * at the end. That timestamp you got there is the last thing in the filename but additional * assumes there is something else to match while your files end right there.

*abc* = <anything>abc<anything>
*abc = <anything>abc

---

### Post by cipherboy_loc on 2011-04-27
* matches everything including nothing. Try the following:

```

rm *before_restore*

```


Cipherboy

---

### Post by cipherboy_loc on 2011-04-27
Example:

```
cipherboy@ubuntu-basement:/tmp/example$ touch blank .blank .blank3
cipherboy@ubuntu-basement:/tmp/example$ la
blank  .blank  .blank3
cipherboy@ubuntu-basement:/tmp/example$ rm *blank*
cipherboy@ubuntu-basement:/tmp/example$ la
.blank  .blank3
cipherboy@ubuntu-basement:/tmp/example$ rm ./.*blank
cipherboy@ubuntu-basement:/tmp/example$ la
.blank3
cipherboy@ubuntu-basement:/tmp/example$ rm .*blank*
cipherboy@ubuntu-basement:/tmp/example$ la
cipherboy@ubuntu-basement:/tmp/example$ 


```
Cipherboy

---

### Post by kaykav on 2011-04-27
OK
       I made some dummy files and used  rm *dummy files*. All turned out as expected,with removal of files.But for some reason
not on my target files.I removed them one by one. Strange...
    This situation will come up again (when I restore a set of files),then I'll be back...to the forum...Thank you  for your help.

---

### Post by cipherboy_loc on 2011-04-27
Whoops. Try this (next time):

```

rm** ./.***before_restore*

```

You need the starting ./. because by default * doesn't match hidden files.


Cipherboy

---

### Post by Kurisu86 on 2011-04-27
Sorry, I didn't realize it wouldn't match hidden files, but that makes sense. Guess we all learned something here. Good luck kaykav, I'm sure you'll use this information soon and things will be easier for you.

---

