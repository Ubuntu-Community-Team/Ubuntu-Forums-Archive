---
title: "Figuring out 9.04 programming"
date: 2009-12-06
forum: General Help
---

### Post by alvinmoneypit on 2009-12-06
Hi,

I'd just like to know a little about programming.  I have a Lenovo N500 with 9.04 freshly installed and updated.  

Iknow there is a graphical method to delete or unmount packages, is there a way or ways to undo commands given through the terminal like the ones so often posted on these forums?  I suspect the answer is, "sometimes". but I'd like to hear, "yes".  But tell me the awful truth.

Thanks for all replies.

---

### Post by alvinmoneypit on 2009-12-07
bumpinski... 

can commands issued through the terminal later be revoked?  If so, what method accomplishes this.

---

### Post by t0p on 2009-12-07
Generally speaking, the only way to "undo" commands is to manually reverse their effects.  You issue a command, the command is done.

In your OP you talk about "deleting or unmounting" packages.  I don't know what you're getting at there.

---

### Post by blur xc on 2009-12-07
> **alvinmoneypit said:**
> bumpinski... 

can commands issued through the terminal later be revoked?  If so, what method accomplishes this.

I don't think there is any way to undo terminal commands at all, but I'm not an expert either.

If you rm -rf * your home directory, you are hosed.  There are complicated ways to recover deleted data, but from what I've read it can be a pita and not 100% reliable.

BM

---

### Post by alvinmoneypit on 2009-12-07
t0p,

you said, "your OP you talk about "deleting or unmounting" packages. I don't know what you're getting at there."

what I mean is the "packages" people and the documentation refer to are simply a list of commands and software clustered together in "packages" to achieve a narrow objective, such as viewing a standard encrypted DVD, right?  There is a graphical interface where I can 'unmount' those or add new ones in 'synaptic package manager'.

What my whole point is:  If I have a specific problem I'm trying to solve, and the documentation states to install certain packages, then I feel safe because I can go into the 'package manager' and disable that package if it causes problems in the rest of my system.

But if I go on these forums and someone recommends to run a command or set of commands, there is no way to undo that, right?  So I'm hosed if it doesn't work or causes instability.  It appears my best option in this case is to wipe my drive and start over.  

So I'm just trying to gage how much risk I want to incur for whatever I want to do because I have this system about where I want it on this new installation except for a few things like my onboard camera doesn't work yet.  

a feature that might be beneficial to people is 'system backup' or 'system recovery' that XP used to have.  That way you could go back to running what your were yesterday if you added a mistake or otherwise corrupted your system.  I don't know how much trouble or insecurities this would cause as I'm not a programmer, but I imamgine something like system recovery could at least eat up a bunch of space.

---

### Post by t0p on 2009-12-07
> **alvinmoneypit said:**
> 
...if I go on these forums and someone recommends to run a command or set of commands, there is no way to undo that, right?  So I'm hosed if it doesn't work or causes instability.  It appears my best option in this case is to wipe my drive and start over.  


There's no reason to suppose that any commands suggested by forum members will "cause instability" or "hose" your machine.

Members suggest commands that they think will solve the problem you're reporting.  Usually, if the command doesn't work, that doesn't mean it's going to break anything.

It's true that there's no simple way to "undo" commands.  But it is often pretty simple to reverse the effects of a command.  The one time that's not so true is if you delete or edit a system configuration file incorrectly or needlessly.  But when someone tells you to delete or edit a file, you just need to remember to **back up** that file first.  For instance: someone might tell you to make changes to the file /etc/X11/xorg.conf.  So, before you make any changes to that file, you first make a back up, by doing something like:

```
cp /etc/X11/xorg.conf xorg.conf.bak
```That makes a copy of /etc/X11/xorg.conf, called "xorg.conf.bak" placed in your home directory.  So if the changes to /etc/X11/xorg.conf don't work as hoped, you can simply restore the file to its previous state.

Usually you can trust the commands suggested in these forums.  In the past there have been cases of nasty people suggesting commands that damaged systems.  But admins and more experienced forum members keep an eye out for this type of malicious behaviour.  There's also [a sticky on the subject]("http://ubuntuforums.org/announcement.php?f=326") that you ought to read.

So: don't worry yourself needlessly about hosing your system with a wrong command.  It probably won't happen.  But make back-ups of system files before you edit them, just in case.

---

### Post by The Cog on 2009-12-07
It depends what the commands are. If the command is (as you suggest) just to install a package, like this:
> sudo apt-get install ubuntu-restricted-extras
then the same could be done with a GUI (a different GUI depending on whether you're using Ubuntu, Kubuntu or Xubuntu and maybe UNR). Such a package installation could be undone using synaptic to find and remove whatever package was installed again. In fact, synaptic will launch apt-get in the background to do the real work once it knows what you want done.

Some other commands do things that can't be done in a GUI. Other commands may have effects that can also be done with a GUI but are irreversible, such as deleting a folder full of your files. So whether the actions of commands can be reversed sepends primarily on what the commands did, and only if the action can be reversed at all can you ask if it can be reversed by using a GUI.

The command line isn't magical.  It's neither white nor black magic. It's just a different way of getting the computer to do something you want it to do. And it's not programming - that's totally different to just knowing a few commands, just as saying "Sit!" to a dog isn't the same as dog breeding.

---

### Post by alvinmoneypit on 2009-12-07
t0p,
Thanks for your thorough response.
I did look at that sticky back in March or April when I was considering going to Ubuntu.   
The command language is like a foreign language to me, maybe it is best that I learn a few words in that language so I at least have an inkling about what is going on when these are executed.

I'll look at that link you posted, "common linux commands".

The Cog,

Thats for your lucid post. 
 I understand that commands are not the same as programming and that the graphica interface merely provides a convenient method of issuing commands.

---

### Post by The Cog on 2009-12-08
> **alvinmoneypit said:**
> 
The Cog,

Thats for your lucid post. 
 I understand that commands are not the same as programming and that the graphica interface merely provides a convenient method of issuing commands.
Hope I didn't offend.

The vast majority of the commands posted in these forums are just the names of executables, and you can look at the manual pages on these, e.g. if someone says to do:
sudo tar cvf /media/backup/backup.tar /home
you should know that **sudo** launches a command as root (administrator) so it has full system rights and is thus more powerful/dangerous than normal. **tar** is the executable, and you can see the manual by entering the command **man tar**. The manuals are often somewhat cryptic, but you should at least get a feeling for what you are being asked to do.

---

### Post by alvinmoneypit on 2009-12-08
The Cog,
no offense taken.

I'm new at this, and I'm pretty old, too, so that makes learning a little more difficult.  I try to absorb as much as I can, but many things sink through the cracks.  For instance, you mentioned the "manuals" in terminal mode.  I knew there was a list of commands, but I didn't realize there are true manuals.

I'll have to look, I bet they are better than the DOS descriptors.

---

### Post by Iowan on 2009-12-08
> **alvinmoneypit said:**
>  There is a graphical interface where I can 'unmount' those or add new ones in 'synaptic package manager'. There are ways to remove (or un-install) packages. Some work better than others. It's important to stick with an installer (Synaptic, Aptitude, or apt-get) as the different installers don't necessarily share information about packages they've installed.  There's another thread around that better explains it...

---

