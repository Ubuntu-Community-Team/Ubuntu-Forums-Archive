---
title: "is there something like .bat scripts for linux"
date: 2006-04-22
forum: General Help
---

### Post by cosmoshell on 2006-04-22
.bat sripts dont seem to work in linux???

---

### Post by IYY on 2006-04-22
Shell scripts. They are far more advanced than bat scripts. It's just a regular text file with the line *#!/bin/sh* in the beginning.

For example:

```
#!/bin/sh
echo "My first script!"
```

could be saved as myscript.sh. Then you'd make it executable: 

```
chmod +x myscript.sh
```

And run it:

```
./myscript.sh
```

---

### Post by Face1 on 2006-04-22
Yes, as the above poster noted, shell scripts are the linux equivalent of batch files, but better.  [Here]("http://www.freeos.com/guides/lsst/") is a tutorial to get you started.

---

### Post by cosmoshell on 2006-04-22
just woundering but what does chmod -x actualy do?? i know it makes someting executeable but what does it do to make it executeable. by the way thanks for the help

---

### Post by htinn on 2006-04-22
Using chmod +x will permit the user to execute the file. Otherwise, you will be denied permission to do so.

---

### Post by IYY on 2006-04-22
+x just changes the permissions on the file to make it executable by the user. It doesn't compile it or anything, just tells the system "the owner of this file is allowed to execute it".

-x would remove the execute permissions. 

Other permission changes you can do are r and w, standing for "read" and "write".

---

### Post by Ramses de Norre on 2006-04-22
It's a permission, it gives you the right as user to execute what's in the file, just like the read permission gives you the right to read the file.

And as a side note: a script doesn't have to start with #!/bin/sh, there are other shells to write scripts for too (and scripts will still run without specifying the shell).

---

### Post by cgjones on 2006-04-22
Basically, chmod +x just sets the permissions on the file so that a user can run it. It doesn't actually change the file in any way. And depending on who needs to be able to run this script, you can set finer permissions on it.

If only the user who owns the script needs to run it:
```
chmod u+x *scriptname*
```

If the group the script belongs to needs to run it:
```
chmod ug+x *scriptname*
```

If everyone and their grandmother needs to run it:
```
chmod ugo+x *scriptname*
```

It's better to restrict who can run a script to just those who really need it.

---

### Post by GeneralZod on 2006-04-22
Most UNIX commands have a corresponding "manual" page, which can be accessed by typing "man" followed by the command name; e.g.

```

man chmod

```

---

### Post by cosmoshell on 2006-04-22
[QUOTE=Ramses de Norre]It's a permission, it gives you the right as user to execute what's in the file, just like the read permission gives you the right to read the file.

And as a side note: a script doesn't have to start with #!/bin/sh, there are other shells to write scripts for too (and scripts will still run without specifying the shell).[/QUOTE]

what other shells are there that you can wright scripts for?

---

### Post by IYY on 2006-04-22
The most common shells are: sh (the simplest), bash (Ubuntu's default), csh (good for long programs), tcsh, ksh ... I believe there are others too.

---

### Post by GeneralZod on 2006-04-22
[QUOTE=cosmoshell]what other shells are there that you can write scripts for?[/QUOTE]

[bash](http://en.wikipedia.org/wiki/Bash) is one of the most commonly-used ones, but there are a few others, some of which are listed [here](http://en.wikipedia.org/wiki/Unix_shell) and [here](http://cbbrowne.com/info/unixshells.html).

I'd also recommend reading [In The Beginning Was The Command-Line](http://www.cryptonomicon.com/beginning.html), which is a very interesting bit of history and philosophy of the command-line.  Seriously, check it out! :D

---

### Post by Face1 on 2006-04-22
I believe (I'm sure I'll be quickly corrected if I'm wrong) that some other shells are php and perl, so you could have a PHP shell script, if you wanted.

Er...In light of the last couple posts, I think I'm probably wrong.

---

### Post by Gustav on 2006-04-22
Well, they are not really shells, but you can use them in the same way (same goes for for example python)

---

### Post by Face1 on 2006-04-22
[QUOTE=Gustav]Well, they are not really shells, but you can use them in the same way (same goes for for example python)[/QUOTE]
Ah, okay, thanks...I'm glad I wasn't totally wrong ;).

---

### Post by Gustav on 2006-04-22
I don't know if you can use php like this though

---

### Post by Face1 on 2006-04-22
I believe that I read somewhere that you can.  I know for sure that there is *a* way to run a php script as a shell script...maybe you do it in a different way?

---

### Post by DoktorSeven on 2006-04-22
Sure, you just need the php4-cli or php5-cli package installed.

Then you can do something like this:
```

#!/usr/bin/php
<?php
echo ("Moo\n");
?>

```

```

$ chmod +x moo.php
$ ./moo.php
Moo
$

```

---

