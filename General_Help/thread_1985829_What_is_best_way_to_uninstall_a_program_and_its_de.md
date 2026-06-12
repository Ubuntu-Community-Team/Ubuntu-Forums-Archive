---
title: "What is best way to uninstall a program and its dependencies at the same time?"
date: 2012-05-23
forum: General Help
---

### Post by charleswb on 2012-05-23
What is best way to uninstall a program and its dependencies at the same time? **Is there a way to uninstall the program, its dependencies, and its config files all from one command?**

Will uninstalling dependencies cause problems for other programs?

Like in Windows, uninstalling a program often results in being as if I want to uninstall shared files. I learned to say NO and leave shared files because other programs might need them. Is this a concern with uninstalling dependencies?

If I uninstall a program and its dependencies, can uninstalling dependencies cause problems for other programs that rely on those files?

---

### Post by Enigmapond on 2012-05-23
The easiest way is with Synaptic.  When you remove a programme with that it usually lists any dependencies to be removed with it.

---

### Post by infectedorganism on 2012-05-23
I haven't found ONE command to uninstall a package and all of its dependencies, but maybe some else has. To uninstall a program, I run:

```
sudo apt-get purge packagename
```

After uninstalling the program, I run this to clean any leftover, unused packages.

```
sudo apt-get clean && sudo apt-get autoremove --purge -y $(dpkg -l | grep '^rc' | awk '{print $2}') >remove.txt
```

Credit goes to user: batharoy

Also, here is a good thread to check out:

[HOWTO: Cleaning up all those unnecessary junk files...]("http://ubuntuforums.org/showthread.php?t=140920")

Next, I do not believe there is any way to automatically remove config files. You will have to browse your home folder for any config files that were left behind after uninstalling the program -- they will typically be hidden in your home folder, so be sure to check 'show hidden files' in your file manager.

Lastly, I've never had an issue with a dependency being deleted when it is needed by another program.

---

### Post by charleswb on 2012-05-29
Not trying to disagree, but my Ubuntu Unleashed book for U11.04 says "remove" takes out the program and all its dependencies and warns me that removing those dependencies remove other programs (dependencies) that I want.

It says "purge" does the same, but also removes "configuration" file(s).

I'm wondering if there is a safe way to remove and/or purge without causing issues for other programs. i.e. - **how can I know if removing a dependency will cause unwanted removal or disabling of another program I want?**

So far, I don't have an answer (or not one I understand) regarding command line, but I have recently discovered that Synaptic seems to be working for me in this regard, and also the Ubuntu Software Center too. So maybe I don't need to understand this for command line, but I still want to learn command line stuff as much as possible.

**To say that another way,**[COLOR=Black] I want to clean out all unnecessary files/programs/dependencies, [/COLOR][COLOR=Black]but am concerned that I might [/COLOR]**[COLOR=DarkRed]accidentally uninstall some files/programs/dependencies that are necessary to other programs I want to keep.[/COLOR]**This type problem often occurs on Windows machines if I uninstall a program and choose option to remove shared files. Uninstalling shared files can cause problems for other programs that I still want. [COLOR=DarkRed]**I am concerned that I might create this same type problem in U11.04 of missing shared files (missing dependencies) for programs I want to keep".**[/COLOR]

---

### Post by Cheesehead on 2012-05-29
> **charleswb said:**
> how can I know if removing a dependency will cause unwanted removal or disabling of another program I want?

The system will tell you, and give you a chance to stop.

For example, let's try removing a fairly important package.
```
$ sudo apt-get remove python2.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR="Blue"]The following package was automatically installed and is no longer required:
  libqt4-opengl
Use 'apt-get autoremove' to remove them.[/COLOR]
[COLOR="Green"]The following packages will be REMOVED:
  idle-python2.6 libpython2.6 python2.6 virtualbox-4.1[/COLOR]
0 upgraded, 0 newly installed, 4 to remove and 22 not upgraded.
After this operation, 140 MB disk space will be freed.
Do you want to continue [Y/n]? n
```

Everything in [COLOR="Green"]green[/COLOR] will be immediately removed. In this case, I want to keep virtualbox, so I better not do this.

Everything in [COLOR="Blue"]blue[/COLOR] will be orphaned, but not removed at this time.


> **charleswb said:**
> I want to clean out all unnecessary files/programs/dependencies, but am concerned that I might accidentally uninstall some files/programs/dependencies that are necessary to other programs I want to keep.

Use 'sudo apt-get purge' to get rid of packages, including the config files in /etc. The config files in your /home WON'T be removed automatically by any automated tool (there are very good reasons for this).

Use 'sudo apt-get autoremove' to get rid of those [COLOR="Blue"]orphans[/COLOR] (like the orphan in the example above).

Use 'apt-cache depends packagename' and 'apt-cache rdepends packagename' (no sudo needed) to see the first-level of dependencies of any package. For example,

```
$ apt-cache depends hello
hello
  Depends: libc6
 |Depends: dpkg
  Depends: install-info

$ apt-cache rdepends hello
hello
Reverse Depends:
  junior-system
    hello-debhelper
  hello-debhelper
    hello-debhelper
  hello-debhelper

```
So if you try to purge dpkg, it will take hello with it, and that will take hello-debhelper with them.

Package management is pretty easy. If you're keeping up with the orphans, then there is probably little cruft in your system - just about everything is there for a reason. And if you don't know why something is there, apt-cache it to figure it out.

---

### Post by charleswb on 2012-05-29
I see what you mean about scary warnings sometimes occuring when removing dependencies. I got one that wanted to remove hundreds of things I need. I almost wet myself. Thank goodness for the scary warning. That's the first scary one I've got.

I think from now on, I'll tinker test my guest operating system installations of Ubuntu (I use Virtual Box) and not tinker test my host op sys anymore. The scary message occurred on my host and nearly gave me heart failure. It'll be much safer to do my messing with my guest op systems in future.

===

Now with regard to rest of my questions about uninsalling, your advice is good, but I think I already figured this out on my own by studying Man, and trial and error testing by repeatedly reinstalling and uninstalling Brasero (for a test subject, I don't use Brasero anymore since discovering Xfburn). Each time I uninstalled Brasero I tried different things. 

Please have a look at the below and see if I'm on the right track now. Here is what I think I learned:

===

There are two key parts of removal (to remove app, config file, and dependencies), which were not obvious to me until after much trial and error testing. The purge command must be run before autoremove, and the two must be run as seperate commands. They cannot be run using one command. See below:

===

This does what I want. It removes the app file, its config file, and its dependencies.

sudo apt-get purge brasero && sudo apt-get autoremove brasero

===

This also works.

sudo apt-get purge brasero

sudo apt-get autoremove brasero

===

This does NOT work. How come? Apparently these things have to be done as two separate commands since they are separate things.

sudo apt-get remove --purge --auto-remove brasero

---

### Post by charleswb on 2012-05-29
I will further study what you said regarding:

apt-cache depends packagename' and 'apt-cache rdepends packagename'

Thanks for your advice.

---

