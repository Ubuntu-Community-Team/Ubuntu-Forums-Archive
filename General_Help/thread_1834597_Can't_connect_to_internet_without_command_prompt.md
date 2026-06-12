---
title: "Can't connect to internet without command prompt"
date: 2011-08-27
forum: General Help
---

### Post by malenkylizards on 2011-08-27
When Ubuntu first loads after booting, I can't connect to the internet without first opening terminal and typing `sudo modprobe ndiswrapper`.  It's been long enough that I don't even remember how I came across this solution or how the problem started, but I think it happened when I switched to 11.04.  Before I do that, the connection menu shows "device not ready" under the wireless networks setting.

I've put this problem off for a while because I haven't been coding all summer, so I don't often use the terminal and it's simple to just go Ctrl+Alt+T, Up, password to repeat the last command.  School's about to start, so that's about to change.  Any way I can fix this problem?

---

### Post by captain_171 on 2011-08-27
You can add ndiswrapper to /etc/modules.
Go into your terminal and type.
```
gksudo gedit /etc/modules
```
then add ndiswrapper to that file. 

You also could just add
gksudo modprobe ndiswrapper
to your startup applications in your System/Preferences menu. This will ask you for your sudo password every time you boot after you log-in, but it's the most easiest.

---

### Post by malenkylizards on 2011-08-27
Thanks, Captain!

I got several error messages after I saved the file, such as:

Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.JAAJ0V': No such file or directory

They're all about missing directories.  Is this problematic?

---

### Post by malenkylizards on 2011-08-27
Flawless victory.  Thanks!

---

### Post by captain_171 on 2011-08-27
Not a big deal. "gedit" is trying to create a profile in root's home folder.
*"gedit is a simple text editor for GNOME"*

You can also use a command line tool such as nano or vi.
Using these tools would not give you that error.
*"GNU nano is a small and friendly text editor.*
[I]VI is the default editor that comes with the UNIX / Linux operating system"
[/I]
Make sure to add sudo in front of the command if you wish to edit any file not in the current user's home folder.
*"sudo allows a permitted user to execute a command as the superuser or another user, as specified in the sudoers file."*
 
If you wanted to make sure what you did was added to the file, open the command line and type:
```
cat /etc/modules
```
*"The cat command is a standard Unix and Linux program used to concatenate and display files."*

---

