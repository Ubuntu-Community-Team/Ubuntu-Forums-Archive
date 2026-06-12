---
title: "Bash not running for new admin users on login"
date: 2009-06-27
forum: General Help
---

### Post by whittaker007 on 2009-06-27
Hi, I'm running Ubuntu 8 (Hardy Heron) running as a web server inside a Parallels VM on an Intel Mac. I set it up with bridged networking so that it appears as an independent machine on the network. I prefer to use my OS X terminal because it integrates better with my workflow, so I SSH into the box for shell access.

This has been working as expected. When I log in with the user I created when installing Ubuntu I get the Ubuntu customised bash shell. But I needed to create a couple of other admin users for the system, which I did with:

```
sudo useradd -d /home/username -m username
sudo passwd username
sudo adduser username admin
```I was able to log in as these users through SSH but I noticed the shell prompt was a plain "$" and the arrow and escape keys printed garbage on the screen. I tried modifying the user's .bashrc file but the changes didn't take. Echoing at the start and end of the .bashrc file showed that it wasn't being executed.

I created a .bash_profile file, but that didn't execute either. I put further echoes in the user's .profile and that was getting called. Examining further it seems that the trouble lies with the line:

```
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc"
    fi
#fi
```So $BASH_VERSION is either 0 or null, causing the .bashrc to be skipped. And that indicates to me that bash isn't running. Sure enough, changing that block to:

```
if [ -n "$BASH_VERSION" ]; then
    echo "bash detected"
else
    bash
fi
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc"
    fi
#fi
```With that change in place, if bash is not running then it is run and .bashrc is included. However if I type "exit" it includes .bashrc again and this time chokes on a number of commands. Not that this is all that important when I want to exit, but it indicates that my solution is just a dirty hack.

Tracing it back further to /etc/.profile I can see that it first looks for and executes any .sh shell script it can find under /etc/profile.d (there are none), then checks for $PS1 (which it finds) and then $BASH (which it doesn't) before formatting the $PS1 prompt and including /etc/bash.bashrc if available.

So the problem is that bash is not being started for these two users created through the command line, while bash runs without the hack for the first user I created when I installed Ubuntu.

There must be something I need to do to "turn on" bash for these users. Perhaps I need to add these users to a bash group or something?

---

### Post by whittaker007 on 2009-06-27
OK I figured it out. Looks like bash isn't the default shell according to ```
useradd -D
``` so I set the users shell with ```
sudo chsh -s /bin/bash username
``` - Problem solved!

---

### Post by sigmazero13 on 2009-08-12
I tried the above, and verified that my default shell is /bin/bash.  However, when I put some echo traces in the .profile file, it still seems to be failing the test for $BASH_VERSION, and it never runs.  However, the rest of the .profile file IS running.

---

