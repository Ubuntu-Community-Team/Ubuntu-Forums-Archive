---
title: "How does Ubuntu know where a program is installed"
date: 2010-06-29
forum: General Help
---

### Post by Benchrest on 2010-06-29
I've just been playing with the whereis command. For a program installed with synaptic package manager or comes preinstalled, whereis finds the path to the program. These programs in applications menu or startup applications don't need directory information, somehow linux must have them in some kind of a directory or something. For a program extracted from a .bz file, linux has no idea where the program is and I must give directory information. 
So how does linux find programs that are installed normally? It can't just search through files, that would seem to be slow. Is there a table or directory where program location is stored?

---

### Post by stderr on 2010-06-29
Hi

```
echo $PATH
```

You can append to $PATH as you would any other BASH variable.

edit: I guess I should say something more. In searching for an app (let's say you try and execute "gedit" in the terminal), it searches through the $PATH variable directories. So, for my setup, which is:

```
$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

Ubuntu would try, in order:

 1. /usr/local/sbin/gedit  (doesn't exist)
 2. /usr/local/bin/gedit (doesn't exist)
 3. /usr/sbin/gedit (doesn't exist)
 4. /usr/bin/gedit (DOES exist)

Here it would stop, and execute /usr/bin/gedit, passing any parameters that you provided to the command "gedit".

Finally, slightly tangentially related, I'd just mention that **apt-file** provides a handy interface for finding which package a particular file is in. As an example, I'll demonstrate finding the package that contains the apt-file application itself. To reduce apt-file output, I'm adding a whereis command first, so I'm searching for one specific file, as opposed to any file path containing the string "apt-file".

```
$ whereis apt-file
apt-file: /usr/bin/apt-file /usr/share/apt-file /usr/share/man/man1/apt-file.1.gz
$  apt-file search /usr/bin/apt-file
apt-file: /usr/bin/apt-file
```

So apt-file is provided by a package called, surprise surprise, apt-file, and os could be installed with:

```
sudo apt-get install apt-file
```

And should you want to find what files a package you've already installed provides, you can use

```
sudo dpkg -L <package_name>
```

Just be slightly careful with the arguments to dpkg...

---

