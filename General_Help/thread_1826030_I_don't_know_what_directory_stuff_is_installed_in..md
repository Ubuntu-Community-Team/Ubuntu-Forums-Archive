---
title: "I don't know what directory stuff is installed in."
date: 2011-08-16
forum: General Help
---

### Post by Worlds Tallest Engineer on 2011-08-16
I've gotten myself stuck using the terminal.  There are 3 similar command line prompts, and I don't know how to deal with them.  

                          ```
   Enter the directory postgre is installed in (ie. /usr/local/pgsql): 

   Specify the location of boost and pqxx libraries: 

   Specify the location of the php interpreter:

```I've tried using the locate command, but I'm not sure what exactly I should be searching for.  How do I figure out what this program wants?

---

### Post by Lars Noodén on 2011-08-16
'which' should find postgresql for you:

```

which pgsql

```

---

### Post by Wim Sturkenboom on 2011-08-16
```
locate boost |grep lib
```
as an example. Not sure if they will work.

You might have to run *_sudo upgradedb_* first

---

### Post by smurphy_it on 2011-08-16
apt-file can be used for such operations. If you know the 'exact name' of the package, it makes it easier.  However, you can get it to work either way.

first install it.
```
sudo apt-get install apt-file
```
then update it
```
sudo apt-file update
```

Then, if you know the name of the package you can search for it like so:
```
sudo apt-file list php5-pgsql
```

Or if you don't know the name of the package, but know it has "pgsql" in it, then you can search the repositories for that.  That command will output all of the files it finds within the relevant packages.

```
sudo apt-file search pgsql
```

---

