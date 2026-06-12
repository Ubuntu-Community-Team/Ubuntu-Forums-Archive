---
title: "Adding ./ to the PATH Variable"
date: 2010-02-25
forum: General Help
---

### Post by madmax.santana on 2010-02-25
First of all, what is a PATH variable???

What I know is, it is a directory / list of directories where the executable binaries are present. When you type any command, the kernel searches the listed directories for a binary of that name and if it finds it, it is executed as a command. Maybe /usr/local/bin is an example of such directories.
Am I mistaken? Please elaborate.

Secondly, how do I change PATH variable in any UNIX based system? And where exactly does PATH variable reside?

Lastly, if I add ./ to PATH variable, I have obvious but somehow non-significant advantages. Instead of typing ./binary-name I can just type binary-name and it will execute. As we might know that it has no significant advantages, what are the major disadvantages of this thing?
Is it evil? Evil like in a threat to system security? Or is it unstable or something? I need your comments, please...

---

### Post by Tibuda on 2010-02-25
edit your ~/.bashrc file. this is the relavant part on mine:
```
export PATH="$HOME/bin:/var/lib/gems/1.8/:/opt/android-sdk/tools:$PATH"
```

---

### Post by jocko on 2010-02-25
> **madmax.santana said:**
> First of all, what is a PATH variable???
> **wikipedia said:**
> PATH is an [environment variable]("http://en.wikipedia.org/wiki/Environment_variable") on [Unix-like]("http://en.wikipedia.org/wiki/Unix-like") [operating systems]("http://en.wikipedia.org/wiki/Operating_system"), [DOS]("http://en.wikipedia.org/wiki/DOS"), [OS/2]("http://en.wikipedia.org/wiki/OS/2"), and [Microsoft Windows]("http://en.wikipedia.org/wiki/Microsoft_Windows"), specifying a set of [directories]("http://en.wikipedia.org/wiki/Directory_%28file_systems%29") where executable programs are located. In general, each executing [process]("http://en.wikipedia.org/wiki/Process_%28computing%29") or [user session]("http://en.wikipedia.org/wiki/Login_session") has its own PATH setting.
> **madmax.santana said:**
> Secondly, how do I change PATH variable in any UNIX based system?
You can add a path to the PATH variable by running this command:
```
PATH=/path/you/want/to/add/:"${PATH}"
```
Note that this will be lost when you log off, so to get it to stick (for your user only), you can add the command to your ~/.bashrc

> **madmax.santana said:**
> And where exactly does PATH variable reside?The system wide settings are in /etc/environment, but can be changed for specific users in their ~/.bashrc.


> **madmax.santana said:**
> Lastly, if I add ./ to PATH variable, I have obvious but somehow non-significant advantages. Instead of typing ./binary-name I can just type binary-name and it will execute. As we might know that it has no significant advantages, what are the major disadvantages of this thing?
No idea if there would be any disadvantages. One thing is of course that if you have two different executable files with the same name, but different paths, you would have to type the full path every time you wanted to run the one that is not in your home directory.
But it should be perfectly safe to try it temporarily by running:
```
PATH=./:"${PATH}"
```
Or more permanently by adding the same line to your ~/.bashrc

---

### Post by Simian Man on 2010-02-25
You would add it with:
```

export PATH=$PATH:.

```

In you .bashrc.

What the poster above showed you adds "." to the beginning of your PATH which means that the current directory is searched first.  What I have above adds "." to the end of your path.  It can be argued that this is safer since, if somebody gives you a malicious script called "ls", you won't accidentally run it by trying to run the real ls program.

---

### Post by undecim on 2010-02-25
putting ./ in your path is generally considered a bad idea, because someone could put a file in the directory you're working on that will run malicious code.

For example, you download a tar.gz file that has instructions to extract it and run a seemingly innocent command, such as cp. If there is an executable named cp in the current directory, and ./ is at the beginning of your PATH variable, it will run the cp that came in the .tar.gz rather than the one from /bin/

If you really don't like typing that ./ at the beginning of commands you are running in your directory, you could add ./ to your PATH variable, but make sure it's at the end of the path variable.

---

### Post by jwbrase on 2010-02-25
> **madmax.santana said:**
> First of all, what is a PATH variable???

What I know is, it is a directory / list of directories where the executable binaries are present. When you type any command, the kernel searches the listed directories for a binary of that name and if it finds it, it is executed as a command. Maybe /usr/local/bin is an example of such directories.
Am I mistaken? Please elaborate.

This is pretty much correct. You can see exactly what your PATH contains with:

```
echo $PATH
```

Which means "Write whatever PATH contains to the terminal".

> 
Secondly, how do I change PATH variable in any UNIX based system? And where exactly does PATH variable reside?

Well, each open shell has its own path variable that is created from settings in configuration files, and can be changed during use (you can have two different terminals open with different path variables, but if you close one and open another, the new one will have the default path).

You can change the path variable in a single running shell by typing:

```
export PATH=".:$PATH"
```,

Which means "change PATH to ./, plus whatever is already in the path" (if you just did PATH=".", it would forget the other directories that had been in PATH, and you'd only be able to run executables that were in the current directory).

You can change the default path that your shells start with by typing the following into a terminal:

```
echo export PATH=".:$PATH" > ~/.bashrc
```

Which means "Write 'export PATH=".:$PATH" to my .bashrc file".

You can also do it a bit more neatly by going into .bashrc with a text editor, finding the line danielrmt mentioned, and changing

```
PATH="whatever:your:path:is"
```

to

```
PATH=".:whatever:your:path:is"
```

> 
Lastly, if I add ./ to PATH variable, I have obvious but somehow non-significant advantages. Instead of typing ./binary-name I can just type binary-name and it will execute. As we might know that it has no significant advantages, what are the major disadvantages of this thing?
Is it evil? Evil like in a threat to system security? Or is it unstable or something? I need your comments, please...

There is a slight security disadvantage, and people argue back and forth all the time over whether it's enough of a problem that one shouldn't put ./ in PATH.

I personally don't think it's that big of a hole, especially on a GUI-based system. About the only times it might be a problem are:

A) If you're writing and compiling a new version of a system program from source, and, while working in the directory you're compiling the binary in, absentmindedly call the new version, thinking you're calling the standard version on your computer, and the new version has a bug in it that causes it to do something nasty.

or

B) If you download a compressed file from the internet, unzip it from the command line, and then call "ls" to list the contents of the directory, but the compressed file contains an executable called "ls" that's actually a malware package. This could also happen if it contained a malware-ized version of some other system program, and you didn't call ls first to see what was in the directory. 

Both scenarios can be mitigated by putting ./ at the end of your PATH, instead of the beginning, where I put it earlier (eg, PATH="$PATH:." instead of PATH=".:$PATH"), and scenario B doesn't apply if you do unpacking of compressed files through the GUI. (Or at least look at what was uncompressed from a file through the GUI). In most cases, seeing a program with the same name as a system program (e.g, ls, grep, cat, gunzip, sudo), would be a warning sign, and as long as you saw that such a program was there before typing its name at the command prompt from within that directory, you would know something was fishy before it did any damage.

So some people think it's a security risk, but I don't think it's much of one.

---

### Post by jwbrase on 2010-02-25
> **undecim said:**
> For example, you download a tar.gz file that has instructions to extract it and run a seemingly innocent command, such as cp. If there is an executable named cp in the current directory, and ./ is at the beginning of your PATH variable, it will run the cp that came in the .tar.gz rather than the one from /bin/

As I said in my direct reply to the OP, that only happens if you extract it with CLI tools, rather than the GUI, where you'd see suspiciously named files when you opened up the tarball, and even then, gunzip -l, tar -t, and similar options in command line tools for other formats will let you list the files in a compressed file without extracting it.

And even then, if you're *really* paranoid, you can always specify /bin/cp, /bin/ls, etc, whenever you carry out those operations in the directory you unzipped a file to.

---

### Post by Simian Man on 2010-02-25
> **jwbrase said:**
> As I said in my direct reply to the OP, that only happens if you extract it with CLI tools, rather than the GUI, where you'd see suspiciously named files when you opened up the tarball, and even then, gunzip -l, tar -t, and similar options in command line tools for other formats will let you list the files in a compressed file without extracting it.

And even then, if you're *really* paranoid, you can always specify /bin/cp, /bin/ls, etc, whenever you carry out those operations in the directory you unzipped a file to.

Or you could just add "." to the *end* of your PATH like I said.

---

### Post by jwbrase on 2010-02-25
> **Simian Man said:**
> Or you could just add "." to the *end* of your PATH like I said.

Sure, I mentioned that in my first post too. But honestly, even having it at the front of your path doesn't seem to me to be that big of a hole. I find the conditions where it would be a problem to be fairly extreme and easily avoidable.

---

