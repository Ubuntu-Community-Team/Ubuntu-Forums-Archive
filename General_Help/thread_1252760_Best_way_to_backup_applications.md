---
title: "Best way to backup applications?"
date: 2009-08-29
forum: General Help
---

### Post by Jackelope on 2009-08-29
Hello,

I want to create a backup of all my installed applications so that I can quickly reinstall when (not if) I destroy my system. Here's the catch. I'm on 32 bit, and when I reinstall someday I want to use x64. I imagine using Aptoncd will backup the 32 bit apps and won't reinstall on x64. Will exporting a list of packages from Synaptic also have this limitation, or would it be the better choice? Other options you recommend? Thanks.

---

### Post by mike555 on 2009-08-29
What I do is just make a list , sure it's more trouble to download and install but you get the latest versions and the right bit version .

---

### Post by jonnan on 2009-09-23
Is there any way to export a list of the items that *you* have installed from synaptic/apt? Preferably along with any repositories/keyfiles you have added?

That would be the ideal (for me at least) way to do it, just export (Or even just have synaptic keep a copy of) that list to your home directory, install the next version, then do you're updates and let synaptic look at the list and reinstall everything.

Jonnan

---

### Post by StuartN on 2009-09-23
> **jonnan said:**
> Is there any way to export a list of the items that *you* have installed from synaptic/apt?

You can save a list of everything that is installed with File->Save markings as.. in Synaptic. If you had saved one on fresh install, then you could subtract it from the current list to get only the packages that you installed or caused to be installed.

However, it doesn't matter too much because when you run File->Read markings.. in Synaptic it will only install the remaining packages required to match the list.

---

### Post by Lars Noodén on 2009-09-23
Here is one way to get a list of *all* packages you have, including the dependencies:

[INDENT]```
$ dpkg --get-selections \
  | egrep 'install$' \
  | egrep -v 'deinstall$' \
  | awk '{print $1}' \
  > ~/mylistofpackages.txt

```[/INDENT]


Alternately, more slowly,
 [INDENT]```
$ apt-show-versions \
  | sed -e 's/\/.*$//' \
  > ~/mylistofpackages.txt

```[/INDENT]

To re-install, inefficiently:

[INDENT]```
$ sudo apt-get install `cat ~/mylistofpackages.txt`
```[/INDENT]

---

### Post by philinux on 2009-09-23
Or use synaptic.

File>Save Markings As

But make sure to tick the box "Save full state etc".

Then

File >Read markings.

---

### Post by wojox on 2009-09-23
And yet another way:

```
$sudo dpkg --get-selections > myPackages
```

```
$sudo dpkg --set-selections < myPackages && sudo apt-get dselect-upgrade
```

---

