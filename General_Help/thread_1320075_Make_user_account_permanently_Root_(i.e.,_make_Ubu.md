---
title: "Make user account permanently Root (i.e., make Ubuntu like Windows XP)"
date: 2009-11-08
forum: General Help
---

### Post by LordKelvan on 2009-11-08
Hi:

I'm interested in the following: I would like to make my regular user account a root account.  What I mean is that I want to emulate the behaviour of Windows XP (and older), where the default user account permanently has root privileges.  For example, I would like to be able to run "apt-get install packagename" as the default user without having to use "sudo".  

I've heard of changing the sudoers file so that the regular user doesn't need to enter a password for sudo, but I want to go even further.  I don't even want to have to type precede commands with sudo - I just want to be able to run any command and do whatever I want.

I realize the security implications of this, and I would like to politely state that I don't care.  I just want to know how to accomplish the above.

Thanks in advance,
LK

---

### Post by Gforce20 on 2009-11-08
```
sudo passwd root
```
Taken from [here](https://help.ubuntu.com/community/RootSudo#Enabling%20the%20root%20account). It looks like it isn't a very good idea, and you're probably better off just using "sudo su" in a terminal to perform many root-requiring operations at once.

---

### Post by LordKelvan on 2009-11-08
Thanks, but that isn't quite what I'm looking for.  That only enables the root account (and will allow me to log into my system as root), which I can already do.  What I want to do is be able to login as myself, but automatically have root privileges.  For example, in Windows XP, one can create a regular account (e.g., Joe), and make it an administrator account.  That account can now do whatever it wants.  I want to do the same for Ubuntu.

Let me describe the scenario.  I log into my Ubuntu machine as myself (i.e., Joe), and I can then run the command "apt-get install somepackage" at the terminal without having "sudo" before it and of course without entering a password.

---

### Post by 3rdalbum on 2009-11-08
I don't think there is any way to pervert the security system to do that.

---

### Post by scouser73 on 2009-11-08
It's certainly not advisable to take that course of action as it leaves you open to all sorts of problems.

As you probably know, Linux is designed in such a way as to not let viruses take hold of a PC and by you initiating that type of access would be a major mistake.

---

### Post by mdurham on 2009-11-09
Can't you guys read? LordKelvan knows all that security stuff, he just wants to know how to do something!

---

### Post by 3rdalbum on 2009-11-09
A lot of the software that needs to be run as root will check if it is root, not if it has the same permissions as root, before deciding to run. So as far as I know you can't/fool that software.

---

### Post by LordKelvan on 2009-11-09
mdurham: Thanks for understanding :)

3rdalbum: I see.

Ok... how about this: I start my GDM session by using "ssh -i [GDMSession]".  Since all processes that I start after logging in will be spawned (directly or indirectly) from this session, then I will no longer have to prepend "sudo" before any command.  

Does this logic work?  If so, can someone explain how to do this?

---

### Post by mdurham on 2009-11-09
What happens if you boot in 'recovery mode'? Does that do it somehow?

---

### Post by legatek on 2009-11-09
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by P4man on 2009-11-09
> **legatek said:**
> [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

Exactly.

For those who havent read it, a small extract:

> **Tutorials explaining how to enable the root account for a graphical login or autologin will not be supported on the forums and will be moved to the Jail.** 

<...>
[B]
Users posting such tutorials after this announcement will be given a warning or infraction at the discretion of the staff.[/B]

Please also read the motivation before complaining about this policy.

To the OP: You might want to look for another linux distro that doesnt use the sudo concept. Though frankly Im at a loss why you would want to achieve what you're trying. If typing sudo is too much work for apt-get then just make an alias. You cant run everything as sudo without *being* root it just wouldnt work since everything would use root's settings.

---

### Post by jocko on 2009-11-09
> **Gforce20 said:**
> ```
sudo xxxxx xxx
```Taken from ... It looks like it isn't a very good idea, and you're probably better off just using "sudo su" in a terminal to perform many root-requiring operations at once.
You should consider editing your post, as it is against forum policy to allow post that show how to activate the root account.
If a linux beginner reads your post and decides to try that command it is very likely he/she will later ruin his system by running everything as root... and then blame linux for the problem.

---

### Post by mdurham on 2009-11-09
> **jocko said:**
> You should consider editing your post, as it is against forum policy to allow post that show how to activate the root account.
If a linux beginner reads your post and decides to try that command it is very likely he/she will later ruin his system by running everything as root... and then blame linux for the problem.

It's even in the 'Community Documentation' [here]("https://help.ubuntu.com/community/RootSudo") I don't know what all the fuss is about.

---

### Post by Commander_Keen on 2009-11-09
If your looking for root access, I would advice you to look at Freespire. Its based of off Ubuntu.  The os is basicly Dead.  but the latest version still posted at [www.freespire.com](www.freespire.com)

---

### Post by LordKelvan on 2009-11-09
Err, I appreciate the warnings, but I think those of you warning me are missing the point.  I'm not asking how to activate the root account - I'm already aware of how to do that, but it doesn't do what I want.  

I want to log in as myself (e.g., Joe), but be automatically treated as **root** forever without having to enter a password.  I think the confusion comes from a difference in how Ubuntu does things and how Windows does things.  In Ubuntu, root is a separate account, whereas in Windows, Administrator is a type of account.  So, in Windows, its easy for me to make my account an Administrator-type account, whereas in Ubuntu I can't easily alias my account as the root account.  

Now, based on some of the documentation linked to by mdurham (again, thanks for your help), it seems that this "sudo -i" idea might be a bad idea, as there is an undesirable interplay between what $HOME points to, whose environment variables are used and who owns which files (e.g., I want $HOME to point to my own, and not root's, home directory).  This applies similarly to "sudo -s" and "sudo su".

P4man had an interesting idea of aliasing everything to use "sudo".  How exactly would this work?  Would I put the following in my alias file? 
```

alias *='sudo *'

```

Of course, there may be some commands that I don't want to use sudo in front of.  I think I get errors if I type "sudo cd [path]" or "sudo ls".  In addition, this wouldn't help me with graphical programs launched from the system menus (unless I went through each one and prepended gksudo), or enter certain directories or read certain files not owned by me (don't worry, I'm not referring to another human user, I mean like files owned by 'mysql' or something).

With regards to switching to another distro, that is not an option.  I like Ubuntu, and this problem is more pain-in-the-*** rather than make-or-break.

---

### Post by LordKelvan on 2009-11-09
Perhaps some of the confusion also stems from the "want X, but ask for Y" problem.

My original reason for wanting this is I'm tired of not being able to do what I want on my own system (sort of like what people experienced with UAC on Vista).  The following detail some of the frustrations:

[LIST]
[*] I open some file owned by root, but I forget to open it with sudo.  Now, I make a bunch of changes to the file, only to realize at the end when I try to save it that I can't.  Now I have to re-open the file with sudo, and re-apply all my changes.  
[*] I compile something from source.  Some stage of the compile fails with a cryptic error message.  Through random guessing, sometimes I discover that it needed to read/write to some place owned by root (the error message of course does not indicate this at all).  So, basically, when cryptic errors occur, I can never be sure what is causing it this time - is it the lack of "sudo" or something else?
[*] I want to move some files via nautilus, but I don't realize they're owned by root.  An error dialog pops up, and again, I have to re-open nautilus with gksudo.
[/LIST]

---

### Post by P4man on 2009-11-09
>  In Ubuntu, root is a separate account, whereas in Windows, Administrator is a type of account.  So, in Windows, its easy for me to make my account an Administrator-type account, whereas in Ubuntu I can't easily alias my account as the root account.  

Actually its more similar than that. In windows you also have a separate administrator account called administrator.  If you make your own user account part of the administrator group, its not unlike being in sudoers in ubuntu. At least if we are talking windows vista / 7  with UAC enabled, your apps will not run as administrator unless you right click "run as administrator" or the app pops a UAC popup asking permission to run as admin. Quite like putting sudo in front of it.

In windows you can log in as administrator, in linux you can log in as root (not recommended, nor endorsed or enabled by default on ubuntu). its really the same thing pretty much. 

> 

P4man had an interesting idea of aliasing everything to use "sudo".  How exactly would this work?  

an alias is just a typing shortcut. If for instance you find yourself typing "sudo apt-get install xxx" all day long you could create an alias 'inst xxx' to achieve the same.

[http://ss64.com/bash/alias.html](http://ss64.com/bash/alias.html)

I *really* would not combine that with elimination of the password prompt though.

```

Of course, there may be some commands that I don't want to use sudo in front of. 
```

No kidding.

> With regards to switching to another distro, that is not an option.  I like Ubuntu, and this problem is more pain-in-the-*** rather than make-or-break.

I really think you're making a mistake by subverting the sudo system and creating short aliases on top of that; you're gonna wreck your system sooner or later, so many people already manage to do that despite all the safe guards,  but its your choice I guess..

---

### Post by aysiu on 2009-11-09
> **LordKelvan said:**
> Err, I appreciate the warnings, but I think those of you warning me are missing the point.  I'm not asking how to activate the root account - I'm already aware of how to do that, but it doesn't do what I want. I think you're missing the point.

We don't support this on the forums here. Please re-read the policy again:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

