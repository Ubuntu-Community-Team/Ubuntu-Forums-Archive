---
title: "bash-completion working 100%... I think!"
date: 2012-08-05
forum: General Help
---

### Post by leemaster81 on 2012-08-05
Well After half the night installing latest version of git from ppa. i noticed that git completion wasn’t working. So I started my troubleshooting methods; Google. I saw post from various forums with solutions that sourced /etc/bash_completion.d/git in ~/bashrc. I tried it and it worked. In the process of all this i looked through the directory of /etc/bash_completion.d/ and there are around 150 or so files for various programs, some of which I’m sure aren’t installed on my box. so out of curiosity i chose a random file from that dir and enter the command in terminal followed by [TAB] [TAB] to see if  auto completion would work. to my surprise it didn’t work. So i chose another which was the command dpkg; [TAB] [TAB] auto completion worked! Some worked, most didn’t. I then thought of how tedious it would be to source every single file inside my ~/.bashrc. so I began looking through my ~/.bashrc... At the bottom is:

~/.bashrc BEFORE

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi

So after looking at this for along time I looked through /etc/bash_completion which is a bunch of stuff I really didn’t follow. but after all those lines, why isn’t /etc/bash_completion sourcing all files in /etc/bash_completion.d/? So since I’m a little familiar with bash scripts(very little) I began looking at ~/.bashrc again, and I changed it to look like this:

~/.bashrc AFTER

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -d /etc/bash_completion.d/ ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi

saved the edited ~/.bashrc, closed then reopened terminal. I first tried git [TAB] [TAB] and completion worked! I tried dpkg, it worked! I tried rsync it worked! I tried a few more and they “all” work now. The “-f” switch = if <file> exists. The “-d” = if <directory> exists. and “ changed /etc/bash_completion.d/ because that directory exists. 

I’m not sure if its a bug in /etc/bash_completion or not. I’m using ubuntu 10.04(64-bit) on a Dell Latitude D620. If anyone else has problems with auto completion of any command listed in /etc/bash_completion.d/ give this a try all you have to do is copy/paste. Let me know if this helped you.

:guitar:-leemaster81

---

