---
title: "Force Ubuntu to Automatically Mark Executables as Executable"
date: 2010-07-28
forum: General Help
---

### Post by Joseph Schwenker on 2010-07-28
By default, Ubuntu  10.04 does not mark executable files downloaded from the internet as executable.  This does nothing for me, as Ubuntu has few viruses or security issues, it doesn't work for executables extracted from internet .zip files, and it is a big annoyance to always mark files downloaded as executable.  Because most of the executables I download are from Portable Linux Apps, which approves applications before it hosts them, I would like to stop Ubuntu 10.04 32-bit from denying these applications default access to +x.  How can I make Linux extensionless executables from the internet automatically be marked as executable?

---

### Post by iponeverything on 2010-07-28
```
sudo echo umask 0027 >> /etc/X11/Xsession.d/55gnome-session_gnomerc
```

Adjust the 0027 mask to suite your needs and logout and back in.

---

### Post by iponeverything on 2010-07-28
> I would like to stop Ubuntu 10.04 32-bit from denying these applications default access to +x.

This made me laugh, I could not help thinking about all those poor applications with hurt feelings :)

---

### Post by Joseph Schwenker on 2010-08-03
```
joseph@joseph:~$ sudo echo umask 0027 >> /etc/X11/Xsession.d/55gnome-session_gnomerc
bash: /etc/X11/Xsession.d/55gnome-session_gnomerc: Permission denied
joseph@joseph:~$
```

I tried it in the root terminal next and received no output.  What do you mean "modify it to suit my needs"?  Am I supposed to open a file?  Please be more specific.  Neither one of the commands solved my problem.

---

### Post by dragos240 on 2010-08-03
> **Joseph Schwenker said:**
> ```
joseph@joseph:~$ sudo echo umask 0027 >> /etc/X11/Xsession.d/55gnome-session_gnomerc
bash: /etc/X11/Xsession.d/55gnome-session_gnomerc: Permission denied
joseph@joseph:~$
```I tried it in the root terminal next and received no output.  What do you mean "modify it to suit my needs"?  Am I supposed to open a file?  Please be more specific.  Neither one of the commands solved my problem.

For some reason, even with sudo, the echo command does this. Do this instead:
sudo -s

then

echo umask 0027 >> /etc/X11/Xsession.d/55gnome-session_gnomerc

I don't know why. But it works.

---

### Post by Joseph Schwenker on 2010-08-03
> **dragos240 said:**
> For some reason, even with sudo, the echo command does this. Do this instead:
sudo -s

then

echo umask 0027 >> /etc/X11/Xsession.d/55gnome-session_gnomerc

I don't know why. But it works.

Thanks.  I was able to run that command in the regular terminal.  Hopefully it will work tomorrow when I turn my computer on again.

---

### Post by Joseph Schwenker on 2010-08-04
I tried all of your suggestions, but none of them work.  "There is no application installed for executable files" still taunts me.

---

### Post by Vaphell on 2010-08-04
what kind of executables are we talking about exactly? 

i played a little with nautilus-actions (available in repos) and added right-click option to execute file which sets executable bit and then attempts to run the file right off the bat - no permission fiddling required.
i put **sh** as command and **-c "cd %d; chmod u+x %f; ./%f;"** as parameters

---

### Post by Joseph Schwenker on 2010-08-04
We are talking about extensionless executables like those available from [Portable Linux Apps]("http://portablelinuxapps.org/").  Debs do not need to be marked executable, so we are only focusing on extensionless executables.  Your solution is only a workaround; I need a file that I can edit to force all executables +x.

---

### Post by Joseph Schwenker on 2010-08-11
bump

---

### Post by bodhi.zazen on 2010-08-11
What you are asking for is a bit complex.

It is complex because not all files should be executable, and .deb are complex in that they contain binaries and scripts.

See:

[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

As you can see, a .deb is complex (again some .deb are more complex then others).

There are also security considerations. Sure you may not care, but the fact that you do not care does not change the fact that in linux files have ownership and permissions and you are going to somehow need to micromanage that.

You could possibly script it, if you downloaded a file in a Downloads, you could grep for a #! , test the file you discover to see if it is marked as executable, and if not, chomd +x

Start of a script - 

for i in `grep '#!' ./* | awk -F : '{ print $1 }' | uniq`

[ -x $i ] || chmod a+x $i

done

Good luck finding a solution.

---

### Post by Joseph Schwenker on 2010-08-12
In Ubuntu 10.04, there was a policy change to all executable files downloaded from the internet.  This includes .exe and extensionless ones.  In previous versions of Ubuntu (or if I download an extensionless executable in an archive) I could just download an extensionless executable and have it work.  The same thing with Wine applications.  Now, you have to edit their permission settings manually.  This can be overriden in Wine by setting the default application for .exe files to a custom command "wine".  Now, if I download an application from Portable Linux Apps, I get the error message that there is no application installed for executable files.  I have to manually enter properties and change the permissions, and it is extremely annoying.  Portable Linux Apps is supposed to make using applications faster, and this new policy makes it slower.  This is different from before.  It isn't a complex thing; it's changing a dumb policy back.  It's not going to make anything more secure to make people waste their time and energy changing the permissions of a downloaded file.

---

### Post by Joseph Schwenker on 2010-08-13
bump
What am I supposed to do to the file in /etc/X11?

---

### Post by probono on 2010-08-14
See the [PortableLinuxApps forum]("http://portablelinuxapps.org/forum/viewtopic.php?f=13&t=54") for a way to do it using pyinotify.

---

### Post by Joseph Schwenker on 2010-08-14
> **probono said:**
> See the [PortableLinuxApps forum]("http://portablelinuxapps.org/forum/viewtopic.php?f=13&t=54") for a way to do it using pyinotify.

Is this the only way?  I thought that in previous version of Ubuntu, you could do this.
I'll have to change the stuff to be used for the Desktop instead if I want to use it.  Thanks for the link.

---

### Post by choochoousmc on 2010-08-15
I'm a total newbie so some of the codes for terminal are strange to me.
 But I have the same basic problem.
I've downloaded a couple programs from the internet to enhance browsing, etc.
I've extracted the zip file. But the program is not installed.
And unlike Windows, there is no OBVIOUS .exe file to double click and either run the program or install it.

I D/l frost, Gnunet, thaw  Neither is working.
Real PIA to do work arounds, when they should have a install feature to begin with.

so my question is the same.
A command to run in terminal that permanently makes the executable run at startup
or a way to install the programs.

Like him you said modify the mask 0027, what do you mean and how would I know what  I would need?
TIA

---

### Post by mc4man on 2010-08-15
```
Is this the only way? I thought that in previous version of Ubuntu, you could do this.
```
I don't think this is just 10.04 - karmic is the same way.

There is a 'hack' around, whether advisable to do I'm not sure - I really don't see what the big deal is, you only have to set the permission once.

Out of curiosity did make it so any dl'ed portable app will run right away from a d. left click.

Used the prompt of 'no application ...' to tell it to use an 'application'  - the 'application' being a simple script in ~/bin that marks the file as executable and runs

Edit: decided it's not advisable to do so even though it works fine, there may be unintended consequences, there may not....

---

### Post by sdennie on 2010-08-15
I think this annoyance really is a valid security feature.  Someone above suggested changing your umask so that created files are u+x but, this kind of functionality is part of the reason why Windows has had so many security problems.  Is file foo (or foo.jpg.exe) with +x an executable or a picture?  Do you want it to run or open?

Someone above posted a link to a python script that leads me to believe that it's using the inotify interface to "listen" on things being added to a folder and mark them +x.  That's not a terrible solution but, it's still a security risk.  I understand that you are probably running a home machine and security isn't top priority but, that sentiment will quickly evaporate the first time a +x "document" turns out to really be an executable.

---

### Post by Joseph Schwenker on 2010-08-15
It's more of an annoyance than a security features.  First of all, there are almost no viruses for Linux.  If I download something, I just want to run it.  I am having trouble believing that it was like this in past versions of Ubuntu.  This security features does not work for files extracted from a ZIP file from the internet.  And, interestingly, after I extract the ZIP file, all executables are executable.  All standard documents are not.  See?
The only thing like this that I remember in previous versions was the dialog that asked you if you wanted to mark a .desktop file as executable, which I liked.  That's not in Ubuntu any more.  I wouldn't mind the non-executable executables as much if I didn't have to do so many clicks to get them running!  How about, instead of an error, executables should ask you if you want to mark them as executable, then run the file if you click yes.

Double click on file
File asks "Do you want to run this file?"
User clicks "Yes"
Ubuntu marks file as executable and runs the file.

---

### Post by sdennie on 2010-08-15
> **Joseph Schwenker said:**
> It's more of an annoyance than a security features.  First of all, there are almost no viruses for Linux.


And that's partly because of sane default settings in Linux/Unix.

> 
If I download something, I just want to run it.  I am having trouble believing that it was like this in past versions of Ubuntu.  This security features does not work for files extracted from a ZIP file from the internet.  And, interestingly, after I extract the ZIP file, all executables are executable.  All standard documents are not.  See?


Most archive/compression formats store file attributes in the archive.  When you unzip them, the attributes (like +x) are restored.

> 
How about, instead of an error, executables should ask you if you want to mark them as executable, then run the file if you click yes.

Double click on file
File asks "Do you want to run this file?"
User clicks "Yes"
Ubuntu marks file as executable and runs the file.

That might be a reasonable compromise but, it would have to be taken a step further.  You'd have to look at the magic number to determine if the file was meant to be executed.  My Spidey-Senses still make me think this is a security issue but, I will admit that I can't cite a reason why.

I understand your frustration but, what you are describing isn't a super-common use case.  Most users get software from the repos and everything magically works.

---

### Post by Joseph Schwenker on 2010-10-04
Computers need to change for humans.  Not the other way around.  It's explicitly obvious that Ubuntu can recognize executable files; hence the "executable files" in "There is no application installed for executable files".  So, obviously, there's a way to disable this anti-feature.  It takes more code to put this in than leave it out, and I've never seen this before.  Anyone found a solution yet?  Is this fixed in 10.10?

---

### Post by probono on 2011-01-02
Maybe this is what you're looking for?
[http://www.youtube.com/watch?v=uNmYrxjTkek](http://www.youtube.com/watch?v=uNmYrxjTkek)

---

### Post by Joseph Schwenker on 2011-01-02
> **probono said:**
> Maybe this is what you're looking for?
[http://www.youtube.com/watch?v=uNmYrxjTkek](http://www.youtube.com/watch?v=uNmYrxjTkek)

That's really neat!  Thanks for that.  I'll try using that.

---

