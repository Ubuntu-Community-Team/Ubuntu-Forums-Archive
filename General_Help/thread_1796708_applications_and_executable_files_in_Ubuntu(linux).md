---
title: "applications and executable files in Ubuntu(linux)"
date: 2011-07-04
forum: General Help
---

### Post by p3aul on 2011-07-04
In windows OS I can see every file. That includes executables(exe) files also. Applications are generally stored in a folder called Program Files. Why can't I see these same sorts of files in Ubuntu? A perl script is required to have the path to the Perl interpreter  at the top. I tried navigating to that folder in Ubuntu and I got to usr/local/bin/perl but there was no folder or file named perl. What gives? the code ran just fine from the terminal.
Are executable files in binary form in linux or are they just source code(like Perl) that are run through interpreters by the OS?
Thanks,
Paul

---

### Post by mastablasta on 2011-07-04
in nautilus file manager press crtl+h to show or hide hidden & system files.
 
programms in linux go all over the place. they have shared libraries (share them with other programmes). as a result they are much smaller but this brings other problems.
 
yes there are binaries in linux as well.

---

### Post by dandnsmith on 2011-07-04
The executable (binary)files, usually don't have any extension, and live in /bin, /usr/bin, /sbin, /usr/local/bin (but not exclusively).
Perl scripts are (very) roughly equivalent to .bat files in Windows, and can be anywhere, as long as the path gets to them (often gets added to on istallation, just as in Windows).
Ther is a useful terminal command, file, which will give the type of file (very roughly), so *file xxxx* will show the type of content of xxx.
HTH

---

### Post by CatKiller on 2011-07-04
> **p3aul said:**
> In windows OS I can see every file.

No you can't. Windows hides things from you.

> That includes executables(exe) files also. Applications are generally stored in a folder called Program Files. Why can't I see these same sorts of files in Ubuntu?You can. Linux doesn't hide things from you, but you need to know where to look. You might find [this page]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") a useful introduction.

> A perl script is required to have the path to the Perl interpreter  at the top. I tried navigating to that folder in Ubuntu and I got to usr/local/bin/perl but there was no folder or file named perl. What gives? the code ran just fine from the terminal.If you want to know what the path is for a given executable, you can use which.

```
which perl
```

Ubuntu tends to use /usr/bin. Other distributions might use /usr/local/bin.

---

### Post by p3aul on 2011-07-04
Thanks,
I'm trying to uninstall Netbeans 6.9 according to the website you go to the Netbeans install directory, and execute a shell script. I can't find this directory! I ececuted "which netbeans" in the terminal. this gives me: /usr/bin/netbeans I clicked on home  in the launcher: clicked on Filesystem usr/binary and then got stuck there was no directory called netbeans. I then tried to cd to usr/bin/netbeans in the terminal. I got "No such directory" Where do I go from here? :(
Paul

---

### Post by p3aul on 2011-07-04
> No you can't. Windows hides things from you.

Yes but you can choose to unhide folders and files and their extensions. Just an aside, I still like Ubuntu better if it weren't so obtuse!

I did find the netbeans executable under that File system -> user/bin but there was nothing ending in .sh that was an uninstall script.
Paul

---

### Post by SeijiSensei on 2011-07-04
> **p3aul said:**
> Yes but you can choose to unhide folders and files and their extensions. Just an aside, I still like Ubuntu better if it weren't so obtuse!

I did find the netbeans executable under that File system -> user/bin but there was nothing ending in .sh that was an uninstall script.
Paul

Did you install netbeans from the repositories?  If so, a "sudo apt-get purge netbeans" ought to do the trick.

It's generally not a good idea to install software outside the repository structure unless you need a more recent version that hasn't yet been released for your distribution.  Packages in the repositories have been tested to work with the distribution for which they have been released, and they're generally reviewed for security holes as well.

---

### Post by CatKiller on 2011-07-04
> **p3aul said:**
> Thanks,
I'm trying to uninstall Netbeans 6.9 according to the website you go to the Netbeans install directory, and execute a shell script.

That would be for if you've installed from source. Which you probably haven't. If you installed it from the repositories, which is the recommended way to install anything, you can do uninstall it in Synaptic, or run ```
sudo apt-get purge netbeans
``` in a Terminal.

> 
I ececuted "which netbeans" in the terminal. this gives me: /usr/bin/netbeans I clicked on home  in the launcher: clicked on Filesystem usr/binary and then got stuck there was no directory called netbeans. I then tried to cd to usr/bin/netbeans in the terminal. I got "No such directory"/usr/bin/netbeans isn't a directory. It's an executable file. Which is exactly what you were after, earlier.

Files are organised by function, not what put them there. So binary files go in the bin directories, documents go in the doc directories, configuration files go in the etc directories, temporary files go in the tmp directories, running processes can be accessed through /proc, devices can be accessed through /dev, and so on.

It's different to what you're used to, so there's a learning curve.

> **p3aul said:**
> Yes but you can choose to unhide folders and files and their extensions. Just an aside, I still like Ubuntu better if it weren't so obtuse!

System Volume Information. I'm sure there are others, but I haven't used Windows in over 6 years, so I couldn't tell you what they are.

The largest hurdle new users have is unlearning the things they've learned with Windows. It gets significantly easier as you go. At least you're enjoying it, which is the main thing. And you've got this forum and all sorts of other resources to help you along. You'll get there.

---

