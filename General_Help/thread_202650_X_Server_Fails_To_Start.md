---
title: "X Server Fails To Start"
date: 2006-06-23
forum: General Help
---

### Post by SHodges on 2006-06-23
I was trying to get some eye candy with Dapper Drake, and I followed the tutorials pretty closely...and still something messed up.  When I try to boot into Ubuntu, MPD starts and I can hear my music playing, so I know my data is fine.  However, I get a message that says my X Server has failed to start which is on a blue screen, asking me something and allowing me to select "yes" or "no"...only I can't select anything, because it also brings up a little text only command line thing asking me to log in, and if I use the arrow keys it just puts weird text into that field instead of letting me select anything.  The good news though is that I can log in and all of that, but all I have is a black screen, white text command line, which quite frankly sucks.  So, is there anyway I can use the LiveCD to somehow fix this, or a command I can put into the command line and make it like it was before, anything?  I *REALLY* don't want to reinstall Ubuntu again, as this would be my third time since I started using the Dapper beta, and it's not a very fun process.  Any help is appreciated.

---

### Post by Joeb on 2006-06-23
By adding "eye candy" to Dapper, were you manually editing your xorg.conf?  If so, have you tried hitting ctrl-alt-F1 to switch to a virtual console and logging in?  From there you can manually undo your changes.

If not, what were some of the steps you did just before things broke?

---

### Post by SHodges on 2006-06-23
[QUOTE=Joeb]By adding "eye candy" to Dapper, were you manually editing your xorg.conf?  If so, have you tried hitting ctrl-alt-F1 to switch to a virtual console and logging in?  From there you can manually undo your changes.

If not, what were some of the steps you did just before things broke?[/QUOTE]
I'm going to try ctrl-alt-F1 (I was hitting ctrl alt backspace or something I think), but I can't really remember what I was editing, something in the x11 folder that I had to do a chmod on afterwards, I remember that, and I remember I had to edit my sources list (which I've done before, that's not an issue more than likely) and then copy and paste some things into the terminal to download compiz-gnome and all that.  I've had it working before, I'm not sure what happened with this install :confused:

---

### Post by vigleik on 2006-06-23
The file in question is /etc/X11/xorg.conf, and you should always make a backup before you edit it. In that case, if something goes wrong you can just replace your new file with the old one.

Anyway, you can also try "sudo dpkg-reconfigure xserver-xorg", and it'll give you a new /etc/X11/xorg.conf file (and even make a backup!) after you answer all the questions.

Vigleik

---

