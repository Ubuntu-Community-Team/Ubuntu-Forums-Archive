---
title: "Need help, Used terminal to uninstall a package??"
date: 2010-03-27
forum: General Help
---

### Post by stratus75 on 2010-03-27
I was trying to remove a program "Freevo" using the terminal ( as i want to get the hang of using the terminal) and the command I used was *dpkg -r freevo*,

But after making sure that all other directories for Freevo where deleted (manually), I then proceeded to reinstall the package via the Software Center but it still says the Freevo is installed and an error pops up when I try to remove it saying " package isn't installed there is no need for removal"?? 

If I just reinstall the package via the terminal and then remove it via the Software Center would that sort things ??

What is the right command to use in the terminal to remove unwanted packages so that the software centre will also be updated about packages that are removed via the terminal or is that possible ??

Thanks 
for the help

Love this Os so much that I decieded to under the hood so to speak and start learning and hopefully spread the word!

---

### Post by nitstorm on 2010-03-27
i am a noob too but i use 
```

sudo apt-get remove programname

```
to remove the program, and

```

sudo aptitude remove programname

```
to remove the program and all of the packages and everything related to that program from the system

---

### Post by s_ø on 2010-03-27
dpkg is for installing packages you download manually.
If you install with apt use apt to remove.
apt, aptitude, synaptic, software center, add-remove... - shouldnt matter which you use. Each method resolves package-dependencies.
```
apt-get -h
```will give you the possible uses of apt.

```
sudo apt-get purge package-name
```will remove the package including config files.

Try to reinstall via apt, and see what happens
```
sudo apt-get install freevo
```

---

### Post by n0dix on 2010-03-27
> **stratus75 said:**
> 
If I just reinstall the package via the terminal and then remove it via the Software Center would that sort things ??

Don't should be. 
> **stratus75 said:**
> 
What is the right command to use in the terminal to remove unwanted packages so that the software centre will also be updated about packages that are removed via the terminal or is that possible ??

Try remove the whole package:
```
$ sudo apt-get purge <package_name> 
```
and installing again.

---

### Post by nothingspecial on 2010-03-27
> **nitstorm said:**
> i am a noob too but i use 
```

sudo apt-get remove programname

```
to remove the program, and

```

sudo aptitude remove programname

```
to remove the program and all of the packages and everything related to that program from the system

This may have changed but I remember reading (a long time ago) that mixing aptitude and apt-get can cause problems.

Like I said this advice might be obsolete now.

---

### Post by stratus75 on 2010-03-27
> **s_ø said:**
> 

```
sudo apt-get purge package-name
```will remove the package including config files



That seem's to have done the trick. Got freevo to install with out errors (now just need to configure it LOL )

Thanks to all for the help I'd say this is solved!!

---

### Post by s_ø on 2010-03-27
great. glad to help.
please mark the thread as solved.

---

