---
title: "File associations"
date: 2011-04-09
forum: General Help
---

### Post by Ranko Kohime on 2011-04-09
I've got two separate things I'd like to clear up.

First, is a file association to a program that will only run in it's own directory.  (Arobas' Guitar Pro, if you're curious).  The link created by the installer leads to a shell script, which cd's to /opt/GuitarPro6, then executes the program there.

Attempting to call the program from outside that directory fails, as the program cannot find it's libraries.  It starts normally otherwise.

Passing a file name to the program via the command line works fine, IF you start with the working directory as above.

The question is, what can I do to pass the filename to the command line in the shell script, so that double-clicking in Nautilus brings up the program with the file?  (Currently, just associating with the shell script gives me the program, with no loaded file).

Second issue is files with an .hjt extension.  They're essentially text files, following a specific format used by Treepad.  Nautilus recognizes them as text files.  When I change their association to Treepad, regular .txt files follow this change, and when I change the .txt's back to Leafpad, the .hjt's follow.

How can I separate the .hjt's from the .txt's?

---

### Post by spikoley on 2011-04-10
When you try to run the command outside of that directory are you using the whole path or just the command?  If the path to that command is not in the [$PATH variable]("https://help.ubuntu.com/community/EnvironmentVariables") then it will not work.  Try running the command with the whole path and let us know if it works.

I don't have any ideas on your second question, but I do recommend in the future to post only one question in a thread.  That way one of the questions won't accidently get ignored.

---

### Post by Ranko Kohime on 2011-04-11
> **spikoley said:**
> When you try to run the command outside of that directory are you using the whole path or just the command?  If the path to that command is not in the [$PATH variable]("https://help.ubuntu.com/community/EnvironmentVariables") then it will not work.  Try running the command with the whole path and let us know if it works.

I don't have any ideas on your second question, but I do recommend in the future to post only one question in a thread.  That way one of the questions won't accidently get ignored.

I wasn't quite sure about making two threads nearly simultaneously on nearly the same topic.  :)

Anyway, do you mean using the full path, as in $ /opt/GuitarPro6/./GuitarPro, from any directory?  If so, that fails.  GuitarPro insists on the working directory being /opt/GuitarPro6.

Also, I found a site that described a built-in feature of shell scripts, of passing command-line parameters and picking them up with $1, $2  and so on after the command within the script, but this also fails, with paths that have spaces (whether escaped, or quoted)

---

### Post by spikoley on 2011-04-12
When you specify the full path you do not use ./ in front of the command.

If you path is correct and GuitarPro is the command then this should work.
```
/opt/GuitarPro6/GuitarPro
```

---

### Post by Ranko Kohime on 2011-04-13
> **spikoley said:**
> When you specify the full path you do not use ./ in front of the command.

If you path is correct and GuitarPro is the command then this should work.
```
/opt/GuitarPro6/GuitarPro
```
Added /opt/GuitarPro6 to /etc/environment.  (It took me a while to digest that page about environment variables you linked)  I can now invoke the GuitarPro binary from any directory.  But it still complains about missing libraries if the working directory is not /opt/GuitarPro6, even if I use the full path to the binary.

Recalcitrant little program, isn't it?  :D

---

### Post by spikoley on 2011-04-13
> **Ranko Kohime said:**
> Added /opt/GuitarPro6 to /etc/environment.  (It took me a while to digest that page about environment variables you linked)  I can now invoke the GuitarPro binary from any directory.  But it still complains about missing libraries if the working directory is not /opt/GuitarPro6, even if I use the full path to the binary.

Recalcitrant little program, isn't it?  :D

Thats weird about it still complaining.  I have no idea why it has that library issue.

Maybe you could remove the environment variable and create a symbolic link instead.  Its just a thought and worth a shot.  This is ugly, but a its possible work around if you cannot find the real solution.

```
ln -s /opt/GuitarPro6/GuitarPro /new/path
```

---

### Post by Ranko Kohime on 2011-04-17
> **spikoley said:**
> Thats weird about it still complaining.  I have no idea why it has that library issue.

Maybe you could remove the environment variable and create a symbolic link instead.  Its just a thought and worth a shot.  This is ugly, but a its possible work around if you cannot find the real solution.

```
ln -s /opt/GuitarPro6/GuitarPro /new/path
```
Even a symbolic link does not work.  :(

And here I was going to file a bug report with Arobas, so I was doing some testing with the launcher script, and suddenly it works now, when the exact same setup did not work previously.  :confused: :confused:

Weird.

---

### Post by spikoley on 2011-04-18
> **Ranko Kohime said:**
> Even a symbolic link does not work.  :(

And here I was going to file a bug report with Arobas, so I was doing some testing with the launcher script, and suddenly it works now, when the exact same setup did not work previously.  :confused: :confused:

Weird.

Did you run any updates?

---

### Post by veggen on 2011-04-18
<ignore please, I didn't realize you solved the problem>

---

### Post by Ranko Kohime on 2011-04-18
> **spikoley said:**
> Did you run any updates?
Nope, no updates.  Just sorted itself.  I hate when software does that.  :confused:

---

