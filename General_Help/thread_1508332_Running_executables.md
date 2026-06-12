---
title: "Running executables"
date: 2010-06-12
forum: General Help
---

### Post by raac on 2010-06-12
Hi, I'm new with linux, and I'm wondering why in order to run executables after compilation i have to type 

>"./executableName" I want it to type it just like 

>"executableName" (with no "./")

Can someone explained me in detailed (as I said I'm new with linux) how can i fix that??

I don't know if this matters but I'm using tcsh for my shell...

Thanks a lot

---

### Post by llawwehttam on 2010-06-12
I don't think there is a way to fix that and anyway its more of a feature than a bug.

The ./ means run  the file in the current directory, wheras without the ./ it will try to run it from /bin the programs folder.

---

### Post by raac on 2010-06-12
I friend of mine told my something about changing the PATH by adding "." or something like that. I didn't quite get that though

---

### Post by llawwehttam on 2010-06-12
Not sure what he meant by that. "." means the current directory in unix code (windows copied it at some point) wheras ".." is the directory above.

You can usually replace "./" with "sh" if you want to.

---

### Post by diesch on 2010-06-12
Unlike DOS/Windows the Linux shell by default doesn't look at the current directory for a program to run. You *can* change this by adding *.* to the $PATH environment variable - but for security reasons you shouldn't: The current directory may be created by someone else (maybe it's an archive you just unpacked) and could contain commands named after typical typos (like *sl* instead of *ls*).

Using an explicit path path (like you do with ./something ) if you want to run a program located in a special directory also makes sure you really run *that* program and not another one with the same name located somewhere else. A famous example is *test*, which is a shell built-in command, /usr/bin/test and a name often used for small programs to just test something.

---

### Post by Lucky. on 2010-06-12
> **raac said:**
> I friend of mine told my something about changing the PATH by adding "." or something like that. I didn't quite get that though

It seems like I remember something like this back in a college class in 2005.  I used it to help transition from Windows to Linux.  Can't remember how it went though...

---

### Post by WorMzy on 2010-06-12
After compiling a program, you generally "install" it, copying the executable and other output files to the system directories, putting the executable in one of the /bin or /sbin folders. You can create a symbolic link to an executable in one of the /bin or /sbin folders and it will work as a normal command.

---

