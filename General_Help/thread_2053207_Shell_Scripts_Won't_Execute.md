---
title: "Shell Scripts Won't Execute"
date: 2012-09-04
forum: General Help
---

### Post by temporos on 2012-09-04
I'm sure this is a simple fix, but I can't figure it out.  I have a shell script called [COLOR="Green"]wom.sh[/COLOR] in the directory [COLOR="Blue"]~/wom_linux[/COLOR].  When I double-click the file in *PCManFM*, I am asked if I want to open, execute, or run in terminal.  Opening the file opens it in Leafpad for editing.  Executing and executing in terminal both do nothing.  Also,

```
$:~/wom_linux$ wom.sh
wom.sh: command not found
```
It **will** run if I use "./wom.sh", though.  How do I execute from the GUI?

---

### Post by dcstar on 2012-09-05
> **temporos said:**
> I'm sure this is a simple fix, but I can't figure it out.  I have a shell script called [COLOR="Green"]wom.sh[/COLOR] in the directory [COLOR="Blue"]~/wom_linux[/COLOR].  When I double-click the file in *PCManFM*, I am asked if I want to open, execute, or run in terminal.  Opening the file opens it in Leafpad for editing.  Executing and executing in terminal both do nothing.  Also,

```
$:~/wom_linux$ wom.sh
wom.sh: command not found
```
It **will** run if I use "./wom.sh", though.  How do I execute from the GUI?

Like with **all** Unix/Linux files, set the Execute bit.

Everything is working exactly as it should.

```
man chmod
```

---

### Post by pr0misc on 2012-09-05
> **temporos said:**
> I'm sure this is a simple fix, but I can't figure it out.  I have a shell script called [COLOR="Green"]wom.sh[/COLOR] in the directory [COLOR="Blue"]~/wom_linux[/COLOR].  When I double-click the file in *PCManFM*, I am asked if I want to open, execute, or run in terminal.  Opening the file opens it in Leafpad for editing.  Executing and executing in terminal both do nothing.  Also,

```
$:~/wom_linux$ wom.sh
wom.sh: command not found
```
It **will** run if I use "./wom.sh", though.  How do I execute from the GUI?

You must read about linux directory structure and what is a binary on a *nix system.

1) Set the eXecution bit to the permissions of your script: 

chmod +x wfm.sh

2) Create a symbolic link to your script into , i.e., /usr/local/bin:

ln -s /home/whatever/folder/wom_linux/wom.sh /usr/local/bin/wom.sh

3) Profit.

---

### Post by Wim Sturkenboom on 2012-09-05
> **dcstar said:**
> Like with **all** Unix/Linux files, set the Execute bit.

How does that help if *_./wom.sh_* works ?

---

### Post by efflandt on 2012-09-05
> **pr0misc said:**
> 2) Create a symbolic link to your script into , i.e., /usr/local/bin:

ln -s /home/whatever/folder/wom_linux/wom.sh /usr/local/bin/wom.sh

WHY?

Personal scripts or binaries should go into ~/bin/, which once it is created and you have have logged in again, is automatically in your $PATH.

Note that in Linux, your current directory is NOT in your $PATH by default for your own safety, to avoid accidentally executing something you do not intend to.

---

### Post by temporos on 2012-09-05
> **pr0misc said:**
> Create a symbolic link to your script into , i.e., /usr/local/bin:
ln -s /home/whatever/folder/wom_linux/wom.sh /usr/local/bin/wom.sh
Did that already.  No joy.  Still works only when I execute it using "./wom.sh" while in the directory.


> **dcstar said:**
> Like with **all** Unix/Linux files, set the Execute bit.
The x-bit is already set.  If it wasn't, then "./wom.sh" wouldn't work, either.

---

### Post by drmrgd on 2012-09-05
Since I usually execute scripts in a terminal window, I'm not sure I'm an expert on this.  Also, I don't know how different Kubuntu is from your DE.  I think, though, that just double clicking .sh scripts to run is not enabled by default.  I think you either can:

1.  Right click on it, choose to open with another application, and choose to run it from the terminal.  On Kubuntu, you can create an association with that file type there too, which I presume will allow one to double click and launch .sh scripts from then on (not tested this, though).

2.  Create a launcher or shortcut for the script.  I found this on the LDXE wiki page:

[http://wiki.lxde.org/en/LXShortCut](http://wiki.lxde.org/en/LXShortCut)

Hope that helps!

---

### Post by spjackson on 2012-09-06
> **temporos said:**
> Executing and executing in terminal both do nothing.
Of course the script is executable because ./wom.sh works. Simply typing the name in a terminal will not work - this is completely normal behaviour because ~/wom_linux is not in your path. If you want to be able to run it from the command line without specifying a path, then do
```

PATH=~/wom_linux:$PATH

``` and add it to ~/.bashrc . However, that will not solve your original problem.

How do you know that selecting the options "execute" amd "execute in terminal" do nothing? What is the script supposed to do? Perhaps add
```

date >> ~/wom_linux/wom.log

```at the top of the script to test whether it is actually running. If the script is running but not doing what you expect, then you'd probably need to post the script for further help.

---

