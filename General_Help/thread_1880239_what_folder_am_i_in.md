---
title: "what folder am i in"
date: 2011-11-13
forum: General Help
---

### Post by tzahi2010 on 2011-11-13
i want to know what is my folder direction like C:\
its just says tzahi2010 (my username) or Home so what does it mean?
ohh and whats the file which is like an .bat in linux?
not .exe

---

### Post by WorMzy on 2011-11-13
```
pwd
```

will tell you your current directory, but if your prompt says <username>@<hostname>:~$, or something like that, then the "~" means you're in your home directory (/home/<username>).

Like most files on Linux, shell scripts don't need *any* extension, but .sh is commonly used.

---

### Post by BillyBoa on 2011-11-13
Well here is Linux and the system is different.

If you go to Nautilus (is the Linux Explorer) and in View scroll down to sidebar then right choose Tree. Now to the left pane you can scroll down the tree to understand where you are.

In general there are two main parts, the file system in which is installed the system and you need root privileges (password) to make changes and Home directory (which is included in file system) and there is stored all your personal staff.

To execute a file should have an extension usually .deb or .scr but it doesn't matter because the programs are executed mainly from the graphics display.
If you like to execute a program through terminal, you open the terminal CTRL+ALT+T and write the name of the program .e.g nautilus

---

### Post by Paddy Landau on 2011-11-13
> **tzahi2010 said:**
> i want to know what is my folder direction like C:\
its just says tzahi2010 (my username) or Home so what does it mean?

The file structure in Linux is quite simple. Everything starts with "root" which is represented by a forward-slash:
```
/
```Your home drive is (usually) your user name within the home folder, thus:
```
/home/tzahi2010
```That means "folder *tzahi2010* within *home* under *root*".

Be aware that folders and file names in Linux are case-sensitive; so, the following are all different folders:
```
/home
/Home
/HOME
```> **tzahi2010 said:**
> ohh and whats the file which is like an .bat in linux?
not .exe
File extensions are not meaningful in Linux; they are useful only for you, the human being. Thus, a file does *not* need any extension at all to be (say) a PDF file or an executable.

Every file (and folder) comes with a set of **permissions**. What's more, for each file (or folder), these are applied separately to the owner, the group and everyone else. They are:

[LIST]
[*]Read-access
[*]Write-access
[*]Execute-access
[/LIST]
You'll learn more about this as you go along (or you can Google it).

To be executable, all you need to do is set the *execute permission* on the file.

A folder is a bit different; it needs execute permission to be able to look inside it.

The equivalent of a command file (.bat or .cmd) in Windows is a *script*. There are several different scripting languages you can use (Linux is very flexible), but the most popular is Bash because of its compromise between flexibility and simplicity. Bash is the default in Ubuntu, but you can use any of the available scripting languages.

---

