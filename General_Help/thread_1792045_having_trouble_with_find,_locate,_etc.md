---
title: "having trouble with find, locate, etc"
date: 2011-06-27
forum: General Help
---

### Post by huberthickey on 2011-06-27
I have several programs on my HP Pavilion (running Ubuntu 11.4) which revolve around not being able to find out where files are located on my computer.
For example, I downloaded and installed AVIRA virus and spyware checker for Linux.  I could not get something to work.  I was able to find the config files because of what they said in the manual, but I could not find the executables.  I did a search with the gnome search tool which is to be found in Applications-Accessories-Search for Files.
I put in the word 'avira'.  There are directories called avira in several places in the File System, yet the search engine found not one single one!  I then looked at the manual for this program and I noticed that it did not say specifically that it was looking for directories.  However, there are files that have the name avira in them and they were not found.  
This is only the tip of the iceberg.  More times than I care to think about, I have failed to find files that I knew were on my hard drive.  
I am wondering whether there is a known bug related to this, whether there is some config file that I have to edit, or ?  When I compare this performance with Windows, Windows wins hands down.  But, Linux/Ubuntu is way faster!
Thanks for any help,  Hubert Hickey

---

### Post by WorMzy on 2011-06-27
Before new files will show up in locate, they need to be added to the database that locate uses. You can do this manually by running
```
sudo updatedb
```
This task should run automatically every time you boot up Ubuntu, so you shouldn't need to worry about running manually it on a regular basis.

The find command doesn't use a database, which is why it takes considerably longer (depending on the number of files it needs to process). But because it doesn't use a database, find shouldn't miss any new files. Make sure you're using it correctly though; find is a lot more complicated to use than locate.

```
sudo find / -iname "*avira*"
```
will find any files with "avira" in their name. The "sudo" part may or may not be necessary on Ubuntu, but it will stop a lot of "permission denied" errors from showing up when find searches through folders that your user doesn't have read permissions to.

If you're looking for executables, then you probably want to be looking in /usr/bin,/usr/local/bin, or /opt. Running a seperate find search on each of these specific directories will be a lot quicker than running a single search of /.

---

### Post by drs305 on 2011-06-27
For exectuables, a handly command is "which". It shows where the executable file is located. Of course you have to know the actual name, but TAB completion can help in that regard.

```
which <appname>
```
Example:
> which gimp
returns:
> /usr/bin/gimp

The "whereis" command, used similarly, shows where the apps files are located.
```
whereis gimp
*gimp: /usr/bin/gimp /etc/gimp /usr/lib/gimp /usr/lib64/gimp /usr/share/gimp /usr/share/man/man1/gimp.1.gz*

```

If you prefer GUI, opening synaptic, typing in the package, and selecting the "Installed files" tab of Properties can also help.

---

### Post by Dave_L on 2011-06-27
> **huberthickey said:**
> ... I could not find the executables ...

If the application was installed using the package manager, an easy way to find the executables is to look up the package in synaptic, and then view the installed files.

---

