---
title: "How is Linux documentation organized?"
date: 2012-09-28
forum: General Help
---

### Post by ladasky on 2012-09-28
I know that I have user manuals for many of my installed software packages hiding on my hard drive.  I spend a lot of time hunting for them.  I've taken to making links to the manuals because I simply cannot remember where to find them again!  If it's HTML documentation, I bookmark it in my browser.  If it's in PDF, I make a symbolic link on my desktop.

But then, when my system suffers a crash, I have lost many of these links, and have had to look for the documentation all over again!  (My next round of backups should include the links.)

I'm trying to read the _[Linux filesystem hierarchy standard]("http://www.pathname.com/fhs/pub/fhs-2.3.html")_, and so far it hasn't helped me to understand where to look.

I don't understand most of the "documentation" that I find in /usr/share/doc.  It looks like you will always find documentation which explains how to *install or build* the various packages, but you may not find the user manuals.

Several of the Python packages that I use do install their user manuals inside /usr/share/doc.  Biopython's user manuals, for example, are found in /usr/share/doc/python-biopython-doc.  The manuals for python itself are not found in a folder named /usr/share/doc/python-doc, however... nor do they appear to be inside /usr/share/doc/python2.7.

It seems silly to keep visiting python.org, when I know that I have a local copy of the Python language docs.

My question isn't limited to Python packages.  I have non-Python applications whose manuals hide from me, too.

Thanks for any pointers you can provide!

---

### Post by HiImTye on 2012-09-28
most often the easiest way is just to type 'man' and the name of the tool, such as:
```
man python
man grep
```etc

---

### Post by agillator on 2012-09-28
The nature of the beast is that documentation will be wherever the author wants it to be. Yes, this sometimes makes things a little difficult. However, most authors are wise enough to use the man system. In that case you don't have to worry about where it is, you access it as indicated in the message above by entering 'man <program name>' on the command line (try 'man man' for example). You can sometimes find documentation with 'info <program name>'. Other than that look at the various doc directories when you install something. Usually the installation package will have a 'doc' directory. Actually the best thing to do for most software is to use the documentation on the web. It is always current and probably more complete than anything on your machine.

---

### Post by ladasky on 2012-09-29
> **HiImTye said:**
> most often the easiest way is just to type 'man' and the name of the tool, such as:
```
man python
man grep
```etc

I figured that the man pages weren't what I was looking for, but I looked ayway.  

And I was right, at least for Python, that's definitely not the documentation that I want.  The man pages are, appropriately, directions for how to invoke Python from the shell.  I'm looking for the complete language reference.

Yes, I can always just visit the Python web site.  But I actually lost web access for about two hours yesterday.  Since I wasn't doing any web-based programming, my local documentation copy (IF I could find it again...) would have allowed me to continue working.

---

### Post by jwbrase on 2012-09-29
You can find a list of the files and directories that a package includes with:

```
dpkg -L insert_package_name_here
```

You can also do it in Synaptic by right-clicking on the package, going to "Properties", then to the "Installed Files" tab. I'm not sure how to check that with Software Center (which I don't use because it's horribly dumbed down compared to Synaptic; It may well not have a way to check a package's installed files).

Anyways, I think what you're looking for is the files in the python-doc package. Install python-doc (or python3-doc for python 3), and it will pull in the package python2.7-doc as a dependency (or whatever the latest version number is). Use the instructions above to get a file list for python2.7-doc.

On my system (Ubuntu 10.04), the index is under /usr/share/doc/python2.6/html/index.html , once python-doc has been installed.

Anyways, the quality/existence of the documentation for an application, and how easy that documentation is to find, depends entirely on the developers of that application.

---

### Post by HiImTye on 2012-09-30
> **ladasky said:**
> The man pages are, appropriately, directions for how to invoke Python from the shell.  I'm looking for the complete language reference.
sometimes you can find extra information in man pages, for instance, in the 'SMB.CONF' man page, there's a list of other pages:
```
SEE ALSO
       samba(7), smbpasswd(8), swat(8), smbd(8), nmbd(8), smbclient(1),
       nmblookup(1), testparm(1).
```
but of course, it depends on the maintainer what to make man pages for, unfortunately

---

### Post by whatthefunk on 2012-09-30
Another good option is --help.  For example:
```
 python --help
```

This usually gives you a more compact list of commands than you would find in the man pages.  Sometimes programs also have a --help-all command to give all the options.

---

### Post by ladasky on 2012-10-01
> **jwbrase said:**
> You can find a list of the files and directories that a package includes with:

```
dpkg -L insert_package_name_here
```

You can also do it in Synaptic by right-clicking on the package, going to "Properties", then to the "Installed Files" tab. I'm not sure how to check that with Software Center (which I don't use because it's horribly dumbed down compared to Synaptic; It may well not have a way to check a package's installed files).

Right, so my first order of business when I install Ubuntu, since the Software Center became the default package manager, is to get Synaptic.  The Software Center might work for some users, but not for me.  Yes, I know how to look at the Installed Files list.  You still have to take some educated guesses.  The Python "documentation" that appears in /usr/share/doc is on the installed files list, but... it isn't the documentation that I need.

But, you gave me the hint that I did need:

> **jwbrase said:**
> Anyways, I think what you're looking for is the files in the python-doc package.

Yes, that's it, thank you!  I didn't download the separate document package after my latest crash and rebuild.  Duh.  And the files install where you might expect them to go, in /usr/share/doc/python2.7-doc.

---

