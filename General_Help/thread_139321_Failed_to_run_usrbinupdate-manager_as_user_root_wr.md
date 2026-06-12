---
title: "Failed to run /usr/bin/update-manager as user root: wrong password"
date: 2006-03-03
forum: General Help
---

### Post by MikeE99 on 2006-03-03
Hi all,

I just installed Ubuntu 5.10 on a Dell Inspiron 3500 (P2, 256Mb RAM, 10Gb HDD, CD) and I want to perform various administrator tasks.  My problem is the system's failure to recognize the root password I entered on system installation.  

If I open a terminal and type su - and then enter my root password, the prompt does go to my root directory, but if I try to update from the GUI my root password fails.

I tried logging on as root, but my system responded that I could not log on as administrator from the logon screen.  When I try to open any of the system/administration utilities like /Users and Groups/, I get the same dialog box requesting my password, which is then rejectedby the system.

Do I have a system installation problem or am I just misusing Ubuntu?

---

### Post by joshuapurcell on 2006-03-03
Ubuntu uses the sudo command, and by default you aren't asked to set a password for the root user. You can set a password for this user though, but for the most part using **sudo whateverRootCommand** will do the trick. A password prompt will come up, but the password being asked for is the current user's password, not root's password.

---

### Post by MikeE99 on 2006-03-04
[QUOTE=joshuapurcell]Ubuntu uses the sudo command, and by default you aren't asked to set a password for the root user. You can set a password for this user though, but for the most part using **sudo whateverRootCommand** will do the trick. A password prompt will come up, but the password being asked for is the current user's password, not root's password.[/QUOTE]

Hi Joshua,

Thanks for answering my post.  I was prompted to and did set a root, user, and Grub password when I installed Ubuntu, but none of the passwords allow me to run administrative tasks from the GUI.  The root password will allow me to run apt-get from a terminal window.  What I cannot figure out is how to configure or repair Ubuntu to allow me administrator privileges from the GUI.  Even sudo does not recognize any of my passwords from the GUI.  Any thoughts on what might be the problem?

---

### Post by MikeE99 on 2006-03-04
Joshua,

Just to clarify my observations, the title error message appears when I use my root and my grub password.  When I use my user password the dialog box disappears and the system returns to the desktop, but no other action takes place.  The end result is that I cannot use any of the administrator functions from the GUI.

---

### Post by EastKY_DO on 2006-03-04
That's exactly the problem I'm having.  I posted for help in the System -> Administration woes thread.  I hope we can find a solution.  I really think I would like ubuntu if I can get this (and maybe others) glitch worked out.

Doc

---

### Post by joshuapurcell on 2006-03-04
[QUOTE=MikeE99]The root password will allow me to run apt-get from a terminal window.[/QUOTE]
So you are able to run commands requiring root privileges from a command prompt while logged in (and not using the **sudo** command). Are you logged in as root at the time? I assume so, and I'm guessing that you logged in through this command:```
sudo su
```The above command would ask you for the password of the non-root user that you were logged in to begin with, but afterword you would be logged in as root (typing **whoami** would verify which user you are logged in as). What happens when you try to run an administrative command (which needs root privilege) at a command prompt using sudo?```
sudo apt-get update
```I'm not sure if any of this will help, but I'll go ahead and post this:
By default, Ubuntu does set a password for the root user, but in all the time that I have installed Ubuntu I have never had it ask me specifically for the root password. The password that is set for root is usually not known, and instead users commands which require the root password with the **sudo** command. This command then displays a password prompt that asks for that current user's password (not the root user's password). You can set the root user's password to something that is known by typing **sudo su** followed by **passwd** (just running **sudo passwd** may do it but I'd have to verify). Let me know if any of this helps.

---

### Post by MikeE99 on 2006-03-05
Hi again Joshua,

While in the terminal window I execute an su, which makes me a superuser during the time I'm actively using the terminal window.  If I move out of the terminal window to the GUI I still cannot download updates or open administrator windows without getting the demand for a password.  When I type in my root or grub password, I get the title failure message.  When I type in the user password, the password dialog box dissappears, the cursur rests on the desktop and nothing else happens; the administrator task never opens.

If I open a terminal window, execute an su command, enter my root password, and execute a whoami command, the system returns root.  If I then exit the window without any other action, reopen the window, and execute a whoami command, the system returns the user name.  Evidently, when the terminal window closed the system reverted back to the logged in user.

My problem with passwords may be one of misunderstanding which password to use when, but my problem with inability to perform administrator tasks from the GUI seems systemic.  How can I, for instance, get the system to open the /System/Administration/Networking/ dialog box?  Currently, whether I'm logged in as user or as root in the terminal window, when I navigate through the GUI System, Administration, and Networking buttons, the clocklike busy symbol appears at the cursor for about 12 seconds then dissappears without any further action.  I cannot execute any administrative actions from the GUI.  

It appears I'm not the only person afflicted by this; see EastKY's post...  Thanks to EastKY for moral support, and again to Joshua for helping me through this initial installation of Ubuntu.

---

### Post by joshuapurcell on 2006-03-05
I'm interested to see how the **sudo** and **gksudo** commands function for you. At a command prompt while logged in as your regular user, type this:```
sudo apt-get update
```The above should ask for your current user's password and then continue to run the command as root (which only updates what packages are available... not what is installed). If that works correctly, then hit Alt-F2 and type:```
gksudo synaptic
```This should pop a graphical window asking for the current user's password, and then bring up the synaptic application. What happens for you?

---

### Post by MikeE99 on 2006-03-05
Hi Joshua,

I followed EastKY_Doc's thread, did what worked for him and it also worked for me;  for the benefit of those that follow, let me outline the process.

1) Open a terminal window; Applications/Accessories/Terminal/

2) Type su <enter> and enter the root password when prompted

3) From the root directory, use vi to open sudoers - vi /etc/sudoers

4) Type i to enter text insert mode then at the end of the file add the lines:

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%adm ALL=(ALL) ALL

5) Hit escape to exit insert mode and then type :w! to override read only mode and save the changes

I now can perform administration functions from the GUI and so far everything seems to be working OK.  For the benefit of other new users, please comment on my process where I did something dangerous or could have done something better in some way.

To answer your questions, I did apt-get under su and it worked fine (when I had the problem).  I did not run gksudo under the problem conditions, so I do not know how the system would have reacted.

Thanks for your help and patience.

---

### Post by cjj on 2006-03-07
Thanks MikeE. This was exactly my problem too and I am now happily admining away!:mrgreen:

---

### Post by agboifo on 2006-03-19
This post has been a life saver.  I have spent days trying to solve precisely this problem (which almost scared me off Ubuntu).  Now I can open all the menus.

I'd suggest it be made sticky cos probably many other people have this same problem.

Thanks a billion!

---

### Post by EastKY_DO on 2006-03-19
Hey Guys,

I learned along the way to use the visudo command to edit the sudoers file.  It actually doesn't bring up vi, but instead I think the editor it brings up is nano, which is (in my opinion) easier to use as it provides help.

Later . . .
Doc

---

### Post by joshuapurcell on 2006-03-19
[QUOTE=EastKY_DO]Hey Guys,

I learned along the way to use the visudo command to edit the sudoers file.  It actually doesn't bring up vi, but instead I think the editor it brings up is nano, which is (in my opinion) easier to use as it provides help.

Later . . .
Doc[/QUOTE]
The **visudo** command uses either the $EDITOR or $VISUAL environment variables to decide which terminal text editor to use. I think by default it's set to nano. You can find out by typing this:```
echo $EDITOR && echo $VISUAL
```If you want vim (or nano if it's not already set to that), then type:```
export EDITOR=/usr/bin/vim
```Change vim above to nano if that's what you want.

---

