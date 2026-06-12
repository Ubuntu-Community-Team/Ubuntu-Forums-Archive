---
title: "Change Application Specific User-Data Files Default Location of /home/user/.appname"
date: 2012-09-30
forum: General Help
---

### Post by own3mall on 2012-09-30
Hi All,

Is there a way to change the default location of where application specific user-data files are stored for a particular user?  I created a user that manages game servers, and the log files for these game servers end up in the /home/user/.gamename directory rather than staying in the current directory of /servers/gamename/user1.  Is there a way to prevent application specific files from ending up in hidden directories in the user's home?  I want them to stay in the current directory.

Where are these settings stored, and where can I edit them?

Please let me know.  All help is appreciated.

---

### Post by rai4shu2 on 2012-09-30
Actually, I think that's just a convention. Most applications will use a folder in your $HOME folder, though it's really up to the upstream devs. Some applications use $HOME/.$appname folders, some use $HOME/.$appname file as their configuration storage, and some apps use $HOME/.config/$appname folder for configuration (this is a relatively new convention).

---

### Post by Vaphell on 2012-09-30
you can try cheating the game by symlinking its default /home/user/.gamename to another location.
Move the files, delete /home/user/.gamename and create a symlink with **ln -s** command in its place
```
ln -s /some/dir/with/game/config /home/user/.gamename
```
from now on .gamename is a fake directory linking to another place, but for the game nothing will change

---

### Post by own3mall on 2012-09-30
> **Vaphell said:**
> you can try cheating the game by symlinking its default /home/user/.gamename to another location.
Move the files, delete /home/user/.gamename and create a symlink with **ln -s** command in its place
```
ln -s /some/dir/with/game/config /home/user/.gamename
```from now on .gamename is a fake directory linking to another place, but for the game nothing will change

Cool, I'll give that a shot.  Thanks!

[quote=rai4shu2]Actually, I think that's just a convention. Most applications will use a  folder in your $HOME folder, though it's really up to the upstream  devs. Some applications use $HOME/.$appname folders, some use  $HOME/.$appname file as their configuration storage, and some apps use  $HOME/.config/$appname folder for configuration (this is a relatively  new convention). 	[/quote]

So is this a setting in the game server's code itself?  There's no hard coded way to change it for all apps?

---

### Post by rai4shu2 on 2012-09-30
You could change the $HOME variable itself, but I can't promise that'll work. Symlinking will probably prove to be more effective.

---

### Post by own3mall on 2012-10-03
> **rai4shu2 said:**
> You could change the $HOME variable itself, but I can't promise that'll work. Symlinking will probably prove to be more effective.

Unfortunately, I have 4 of the same game servers running on my box with different IP addresses.  They each want to write their log file in /home/user/.mohaa rather than using their current directory and writing to qconsole.log.  This creates a problem, as I only have 1 log file for as many MOHAA servers as I run.  

Is there no way that you know of to force applications to write in their currently running directory rather than using a specific /home/user/.app path?

---

### Post by own3mall on 2012-10-15
I'm guessing this is the application's behavior, or is this some king of deep setting in Ubuntu.  Wish someone knew.  Symlinks won't cut it.

---

### Post by Vaphell on 2012-10-15
i think it's the program's behavior. Some programs i have write to ~/.program, some write to ~/.config/program so i don't think it's the system that sets the rules.

Can't you have 4 different accounts each running single server?

---

