---
title: "SFTP: Received message too long 1466264675"
date: 2010-12-31
forum: General Help
---

### Post by klikevil on 2010-12-31
Well struggled with this for a few hours so figured I'd post it here in case someone else makes a newbie mistake like me.

After customizing my .bashrc for a nice pretty shell locally I decided I wanted it to look nice remotely too so I created a ~/.bash_profile in my home directory so I wouldn't have to type bash upon logging in I'd just be greeted with my colors and customizations.  I placed the files on 2 remote locations and ssh'd in and worked just like it wanted it to, later that same day I tried to sftp in to one of the locations and it kept disconnecting me after i'd input my password, but I could still ssh in just fine.

After trying a few suggestions from the web like [http://autosys.us/misc/sftp_received_message_too_long.html](http://autosys.us/misc/sftp_received_message_too_long.html) with no success i decided to ask some friends.  They narrowed it down to the motd and echo's in my .bashrc.  Finally I asked a very experienced developer about it and so without further adue here is the .bashrc / .bash_profile

BASHRC:
```

PS1='\[\e[0;32m\]\u\[\e[1;34m\]@\h\[\e[m\] \[\e[1;34m\]\w\[\e[m\] \[\e[1;32m\]\$\[\e[m\] \[\e[1;37m\]'
# Source global definitions
if [ -f /etc/bashrc ]; then
    . /etc/bashrc
fi
# Looks best on a terminal with black background.....
#echo -e "Welcome Ev][L... We've been expecting you\n"
#date
#if [ -x /usr/games/fortune ]; then
#    /usr/games/fortune -s     # Makes our day a bit more fun.... :-)
#fi



# message too long fix
if [ ${TERM} != "dumb" ]; then
 test -s ~/.bashrc-local && . ~/.bashrc-local
fi


############# giving credit where credit is due ###############
# (02:21:46 PM) Rob: so, that message too long happens anytime you print something out when the bash_rc is processed
# (02:21:53 PM) Rob: you have to check to see it its an interactive sehl;l
# (02:21:54 PM) klikevil@seotechi.net: yeah
# (02:22:56 PM) Rob: do this
# (02:23:01 PM) Rob: put your printing code into
# (02:23:04 PM) Rob: .bash_profile
# (02:23:07 PM) Rob: instead of bashrc
# (02:23:16 PM) Rob: remove from bash_rc and put in bash_profile
# (02:25:38 PM) klikevil@seotechi.net: well I already put the code in .bash_profile, like I just cp'd .bashrc to .bash_profile
# (02:25:56 PM) Rob: then remove from bashrc
# (02:25:59 PM) klikevil@seotechi.net: kk
# (02:27:10 PM) klikevil@seotechi.net: omg you're a genius worked lol
# (02:27:12 PM) klikevil@seotechi.net: ty sir
# (02:27:25 PM) klikevil@seotechi.net: seotechd@EdenII ~/Music $ ssh klikevil@******
# klikevil@********'s password: 
# Last login: Thu Dec 30 14:19:42 2010 from *
# Welcome Ev][L... We've been expecting you
# 
# Thu Dec 30 14:24:57 CST 2010
# Lay on, MacDuff, and curs'd be him who first cries, "Hold, enough!".
#         -- Shakespeare
# klikevil@klikevil-desktop ~ $ exit
# logout
# Connection to *********** closed.
# seotechd@EdenII ~/Music $ sftp klikevil@*******
# Connecting to ****...
# klikevil@*****'s password: 
# sftp> 
# 
# (02:28:01 PM) Rob: http://shreevatsa.wordpress.com/2008/03/30/zshbash-startup-files-loading-order-bashrc-zshrc-etc/
# (02:28:06 PM) Rob: i was looking at the loading order
# (02:28:15 PM) Rob: and bash_profile isnt loaded for non-interactive
# (02:28:21 PM) Rob: but it is for interactive
# (02:28:26 PM) klikevil@seotechi.net: ohhhhhhhhhhh
# (02:28:48 PM) klikevil@seotechi.net: well now I need to go reply to every single forum on the internet
# (02:29:00 PM) Rob: lol

```

BASH_PROFILE
```

PS1='\[\e[0;32m\]\u\[\e[1;34m\]@\h\[\e[m\] \[\e[1;34m\]\w\[\e[m\] \[\e[1;32m\]\$\[\e[m\] \[\e[1;37m\]'
# Source global definitions
if [ -f /etc/bashrc ]; then
    . /etc/bashrc
fi
# Looks best on a terminal with black background.....
echo -e "Welcome Ev][L... We've been expecting you\n"
date
if [ -x /usr/games/fortune ]; then
    /usr/games/fortune -s     # Makes our day a bit more fun.... :-)
fi

```

And for any of you that are curious to see how this looks :)
[img]http://img830.imageshack.us/img830/703/purdy.png[/img]

Unfortunately I forgot to mention to get it to launch the terminal with the greeting / fortune you have to have the echos uncommented in the .bashrc locally, or know more about shell scripting than I [wouldn't surprise me at all if someone is able to expand upon my bashrc and fix my minor problem] and have it not echo or execute fortune on sftp only somehow.  So if you have fortune uncommented be prepared to be unable to sftp IN to the box that it is uncommented on.

---

### Post by howefield on 2011-01-02
Thread closed.

Duplicate here : [http://ubuntuforums.org/showthread.php?t=1656869](http://ubuntuforums.org/showthread.php?t=1656869)

---

