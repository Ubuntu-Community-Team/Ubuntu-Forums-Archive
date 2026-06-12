---
title: "can't log in"
date: 2011-01-20
forum: General Help
---

### Post by cam3roon on 2011-01-20
Hi guys. I have Ubuntu 10.10 that works fine and it's fully updated. Recently I had the idea to install KDE and during the installation I accidently changed the default to kdm. Obviously after that the splash screen and the login screen were from kdm. So after the installation I wanted to change back to gdm so I found on the internet that I should type 

[I]sudo dpkg-reconfigure gdm
[/I]
I did that and changed the default to gdm. Now when It starts, it still has the kdm splash screen but the login screen changed to the gdm login screen. The problem is that now when I try to login in, after typing the password and press 'enter' it appears a black screen and comes back to the login screen. I tried to change to other desktop session but it happens the same. 

How can I make it to work and change it like it was before with the gdm splash and login screen? 

Thanks a lot!

---

### Post by cam3roon on 2011-01-20
anybody? :cry:

---

### Post by achim_59 on 2011-01-20
I had a similar problem with 10.04 last year. It probably has nothing directly to do with the splash screen problem.

In my case the problem was a syntax error in my .profile file. I can't remember exactly how I fixed it but it was something along the lines of this:

1. At the login prompt there is an option to login to console mode. I logged in as root. (This is possible if you've run *sudo passwd* and entered a password for the root user. If you haven't done that it might still allow you to login as yourself.)

2. Go to your home directory on the console and try running the .profile file: *". .profile"*

3. If you get a syntax error, then that is your problem. If you're lucky it will be a fairly obvious thing and the message will give you a good clue where in the file to look.

4 Edit .profile with vi. If you don't know how to use vi, this could be a problem. My only suggestion then is to use a second machine if you have access to one (given that you made this post, you probably do). Then copy the contents of .profile (yes, you'll have to type it out (just leave out any comments... there are lots) and post it here. I can try to see if I  can locate the problem and post the answer. Alternatively you could try learning how to use vi. 
[http://www.cs.colostate.edu/helpdocs/vi.html](http://www.cs.colostate.edu/helpdocs/vi.html)

Good luck

Achim

---

### Post by achim_59 on 2011-01-20
Sorry, I'll write that commnd out properly this time.

```

. .profile

```

Make sure you have a space between the 2 dots.

I'm off to bed now. I'll check tomorrow to see if you've had any luck.

Achim

---

### Post by cam3roon on 2011-01-21
thanks for answering. I tried to use the recovery console, doesn't work either. 

I have an guest account, and the weird thing is that it works like it should to. But I can't see the home files because is encrypted :\

---

### Post by achim_59 on 2011-01-21
> **cam3roon said:**
> thanks for answering. I tried to use the recovery console, doesn't work either. 

I have an guest account, and the weird thing is that it works like it should to. But I can't see the home files because is encrypted :\

It seems a bit odd that your home folder is encrypted. On my machine that is certainly not the case. Did you do that yourself? If not, it might simply be a restriction on the guest account.

Whatever! If you can log on as a guest, you could try switching to your normal userid with the *su* command.

```
su <your_userid>
```

You will be prompted for your password. 

Even if the rest of your home folder is encrypted, the .profile should not be. I'm not all that clear on how it relates, but some people have suggested that .bashrc is also run at login. It has never worked for me and I just use .profile but you might want to check .bashrc, too.

Regards

Achim

---

### Post by cam3roon on 2011-01-21
I did it. When I installed Ubuntu 10.10 it asked me if I want to encrypt it.

I'll try now to change the user or find the .profile.

---

### Post by cam3roon on 2011-01-21
Ok. the su command worked and could acces the .profile file. This was the content


```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

```
I should uninstall kde better?

---

### Post by achim_59 on 2011-01-22
I cannot see any syntax errors. Just eye-balling usually isn't good enough, though. 

I tried running it as "test" in a terminal and got a really odd reply:
```
bash: ELF   : command not found
```

I thought this might be coming from my own .bashrc since the script you sent runs that file, too. However, running .bashrc directly gave no errors. 

If you want to try something else, then you could run the .profile and .bashrc files and post back the result.

```
. .profile
. .bashrc
```

Don't forget the space between the dots.

On the other hand, if you want to uninstall KDE, then I wish you luck. I don't know how I'd do it without access to Synaptic Package Manager. No doubt the Debian people have an appropriate "apt" command. You'll have to search for that, because I'm not clued up on package management with aptitude.

---

### Post by cam3roon on 2011-01-22
Runned them both. Nothing happened. It just passed to a new line, so, I'm guessing that it didn't had any errors.

---

### Post by achim_59 on 2011-01-22
> **cam3roon said:**
> Runned them both. Nothing happened. It just passed to a new line, so, I'm guessing that it didn't had any errors.

I'm thinking your guess is right. The thing is that a syntax error in any of the scripts which run at login time could cause the problem you describe. It is interesting that you don't get that odd error that I got when I ran your .profile as "test" but at least you've eliminated 2 possible sources for the problem.

Getting rid of KDE might solve the problem or might not. As mentioned, I'm no help to you there, because I get lost without Synaptic. Maybe some other helpful soul on these forums can give you a hint how to do it with aptitude, which is a command line system.

I just reread your .profile (something I should do with my .profile rather than simply adding my own stuff to the end :-) ) In the first few lines of comments it says:

> # ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.


This suggests you should also look to see if you have .bash_profile or .bash_login files in your home folder. If you do, then run those the same way you did with .profile and see if you get syntax errors.

Good luck

Achim

P.S. I guess we should also check exactly what shell you're running. You can do this as follows:
```
achim@ubuntu-desktop:~$ echo $SHELL
/bin/bash

```

---

