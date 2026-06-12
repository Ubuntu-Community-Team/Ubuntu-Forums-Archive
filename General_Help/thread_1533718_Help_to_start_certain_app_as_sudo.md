---
title: "Help to start certain app as sudo"
date: 2010-07-18
forum: General Help
---

### Post by _Smiler_ on 2010-07-18
Hi, I seem to only be able to start checkgmail as root. I have it listed as a startup application, and in the command line I entered gksudo [path to file]. How do I make it remember the password at each startup?

---

### Post by bobcollard on 2010-07-18
> **_Smiler_ said:**
> Hi, I seem to only be able to start checkgmail as root. I have it listed as a startup application, and in the command line I entered gksudo [path to file]. How do I make it remember the password at each startup?
```
gksu application
```
is password protected because you are using root which requires a password every time it is accessed.

---

### Post by _Smiler_ on 2010-07-18
> **bobcollard said:**
> ```
gksu application
```
is password protected because you are using root which requires a password every time it is accessed.

But is there a way I can set just this command not to ask everytime? To clarify, I want gksudo /usr/bin/checkgmail to start without asking for the password.

---

### Post by MaxIBoy on 2010-07-18
First of all, the answer to your question is to change your sudo configuration to allow that specific command to run without a password. Use the "visudo" command to edit your /etc/sudoers config file. Look at the manpages for visudo and sudoers for details.

When you run a program as root, any files it touches are converted to root-access-only files. Why not try to find out what configuration files have been "infected" as a result of you running checkgmail as root? It's quite possible that you might be able to just fix this properly. The way I'd do this is with strace:
```
sudo apt-get install strace
strace checkgmail 2>&1 | grep "open"
```That should spit out a list of what files it's trying to open. You can then see if some of those have incorrect permissions.

---

### Post by _Smiler_ on 2010-07-18
> **MaxIBoy said:**
> First of all, the answer to your question is to change your sudo configuration to allow that specific command to run without a password. Use the "visudo" command to edit your /etc/sudoers config file. Look at the manpages for visudo and sudoers for details.

When you run a program as root, any files it touches are converted to root-access-only files. Why not try to find out what configuration files have been "infected" as a result of you running checkgmail as root? It's quite possible that you might be able to just fix this properly. The way I'd do this is with strace:
```
sudo apt-get install strace
strace checkgmail 2>&1 | grep "open"
```That should spit out a list of what files it's trying to open. You can then see if some of those have incorrect permissions.

Thanks to both of you for helping! I'll give strace a try first and see if I can figure it out. I've had Ubuntu for about a year now, but am a bit conservative with using the command-line.

---

### Post by bobcollard on 2010-07-18
> **_Smiler_ said:**
> But is there a way I can set just this command not to ask everytime? To clarify, I want gksudo /usr/bin/checkgmail to start without asking for the password.
Instead of using Terminal, another way to run it in Linux is press Alt f2 and type in checkgmail in  the run application box.  Alternately why don't you add checkgmail to your startup applications, it will ride in your system tray and be running all the time?  Either way you don't need a password.

---

### Post by _Smiler_ on 2010-07-18
> **bobcollard said:**
> Instead of using Terminal, another way to run it in Linux is press Alt f2 and type in checkgmail in  the run application box.  Alternately why don't you add checkgmail to your startup applications, it will ride in your system tray and be running all the time?  Either way you don't need a password.

I have it added in Startup Applications. Checkgmail keeps asking for root password though. I used strace and half of the output says things like: ```
open("/usr/share/locale/en_GB.utf8/LC_MESSAGES/gtk20-properties.mo", O_RDONLY) = -1 ENOENT (No such file or directory)

```

I can put the full output on Pastebin if someone is willing to help me out.

Thanks again

---

### Post by bobcollard on 2010-07-18
> **_Smiler_ said:**
> I have it added in Startup Applications. Checkgmail keeps asking for root password though. I used strace and half of the output says things like: ```
open("/usr/share/locale/en_GB.utf8/LC_MESSAGES/gtk20-properties.mo", O_RDONLY) = -1 ENOENT (No such file or directory)

```I can put the full output on Pastebin if someone is willing to help me out.

Thanks again
I notice you are using an uppercase letter for the application, that would be a mistake in either terminal or startup applications.  Perhaps that is why it says no such application?

---

### Post by _Smiler_ on 2010-07-18
> **bobcollard said:**
> I notice you are using an uppercase letter for the application, that would be a mistake in either terminal or startup applications.  Perhaps that is why it says no such application?

No, I use lowercase in terminal. I can't translate the output (e.g. I have no idea what "O_RDONLY) = -1 ENOENT" means), but it looks like the strace command is bringing up the files that checkgmail accesses, but then it says that these files/directories don't exist? I followed one such directory in Nautilus, (/usr/lib/perl/5.10/SAX.ini) and get to the 5.10 folder but the SAX.ini file doesn't exist. Do I need to reinstall perl then?

---

### Post by _Smiler_ on 2010-07-18
Here is the full output incase it helps. 

[http://pastebin.com/wdiBAvqk](http://pastebin.com/wdiBAvqk)

---

### Post by bobcollard on 2010-07-18
> **_Smiler_ said:**
> No, I use lowercase in terminal. I can't translate the output (e.g. I have no idea what "O_RDONLY) = -1 ENOENT" means), but it looks like the strace command is bringing up the files that checkgmail accesses, but then it says that these files/directories don't exist? I followed one such directory in Nautilus, (/usr/lib/perl/5.10/SAX.ini) and get to the 5.10 folder but the SAX.ini file doesn't exist. Do I need to reinstall perl then?
I use gmail-notify in my Panel and have Google Mail in my Cairo-dock to open it when I need it, so I cannot speak for the way your setup works, just a suggestion.  I doubt if Perl is your problem.

---

### Post by MaxIBoy on 2010-07-18
O_RDONLY means the file has been opened with read-only permissions. ENOENT means that the file wasn't found, and EACCES is a permission-denied error.

That's interesting, it's trying to do something with /etc/shadow (and it's getting a "permission denied" message.) As far as I can tell there's no reason why a mail program could possibly need to access that file. Also, it's trying to open a screenshot in your Desktop directory? This checkgmail program is *weird.* I'll have a look at the source code (though I don't really know Perl) and see if I can figure anything out...
EDIT: Not seeing anything out of the ordinary, maybe it's Perl itself.

---

