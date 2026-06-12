---
title: "Run a compiled executable default?"
date: 2011-04-13
forum: General Help
---

### Post by oznick on 2011-04-13
Hi everyone!

I'm using intel fortran and c++ compilers on Ubuntu. When the code is compiled it spits out an executable.

Question:
Is it possible to tell the terminal to execute such a file by just writing it's name, without the './" ? (Right now it gives me a command-not-found error.)

Or at least associate some extension, like '.exe' to make them executable?


P.S. I know - I'm just being lazy. I never bothered with such a thing, until I started using a cluster at uni, which has some version of Ubuntu installed. And it runs these files without the "./" via ssh.

---

### Post by yetiman64 on 2011-04-13
> **oznick said:**
> Hi everyone!

I'm using intel fortran and c++ compilers on Ubuntu. When the code is compiled it spits out an executable.

Question:
Is it possible to tell the terminal to execute such a file by just writing it's name, without the './" ? (Right now it gives me a command-not-found error.)

Or at least associate some extension, like '.exe' to make them executable?


P.S. I know - I'm just being lazy. I never bothered with such a thing, until I started using a cluster at uni, which has some version of Ubuntu installed. And it runs these files without the "./" via ssh.

If you create a folder in your home folder and call it "bin" (without the quotes), logout and log back in. The ~/bin folder is in the system path. So dropping any executable (marked as executable in "Properties") in the new folder will allow its execution from terminal with just its name.

To check your system path use in terminal
```
echo $PATH
```To add other folders to your system path you can use the export command in ~/.profile.

an example from my ~/.profile file for the purpose of including 5 subfolders of ~/bin in the system path,

```
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$PATH:$HOME/bin"
fi

export PATH=$PATH:$HOME/bin/chroot
export PATH=$PATH:$HOME/bin/MyScripts
export PATH=$PATH:$HOME/bin/Radio
export PATH=$PATH:$HOME/bin/System
export PATH=$PATH:$HOME/bin/UDF
```Any scripts or programs dropped into the above 5 custom folders are useable from terminal by their names alone (if also marked as executable in their Properties).

---

### Post by oznick on 2011-04-13
Okay, got it. But it is possible export the current directory you are cd'ed in, instead of dropping files to a certain folder?

---

### Post by yetiman64 on 2011-04-13
> **oznick said:**
> Okay, got it. But it is possible export the current directory you are cd'ed in, instead of dropping files to a certain folder?

You would need that folder put in the system path using the info about ~/.profile. 

If you use the code to check out your current system path, your will notice only a handful of locations are there. I suspect putting too many folders in the system path may not be a good idea for stability or possibly even security reasons.

Edit: try using in the terminal (for a temporary path change) the code (adjust it to the folder you want)
```
export PATH=$PATH:/<your-folders-full-location-path>
```

On the next logout or reboot the path will return to normal.

---

### Post by oznick on 2011-04-13
But what if you remove the folder from the system path as soon as you cd out of it? Or does the list only get updated on terminal login?

---

### Post by yetiman64 on 2011-04-13
> **oznick said:**
> But what if you remove the folder from the system path as soon as you cd out of it? Or does the list only get updated on terminal login?

If you are talking about the temporary solution using the export command in terminal (my edit) it will only stick till the next logout. If you refer to the ~/.profile entries, they are permanent entries regenerated on each login.

AFAI understand it, to launch a script or program from terminal using just its name requires the script or program to be in the system path.

---

