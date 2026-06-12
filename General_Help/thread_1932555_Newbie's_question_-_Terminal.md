---
title: "Newbie's question - Terminal"
date: 2012-02-27
forum: General Help
---

### Post by chenxinghao on 2012-02-27
New to Ubuntu, installed recently with its new 11.10 release.

I have three questions:

(1) How to change the name of the computer name which, as I recall, was typed in during the Ubuntu installation?

(2) In the Terminal, each command line starts with:

my_login_ID@computer_name:~$

How can I remove @computer_name and the ~$ sign?

(3) How can I change my_login_ID?

NOTE: During Ubuntu installation I gave long my_login_ID and computer_name because the installer kept deny my shorter choices. The results is that the command line header takes too much space. The System Settings -> User Accounts doesn't seem to give me an option to modify my login ID.

---

### Post by cortman on 2012-02-27
Hi, and welcome to Ubuntu!

1) [How to change computer name]("http://www.google.com/#hl=en&sclient=psy-ab&q=how+to+change+computer+name+in+ubuntu&pbx=1&oq=how+to+change+computer+name+in+ubuntu&aq=f&aqi=g3&aql=&gs_sm=3&gs_upl=391l4298l0l4509l37l19l0l0l0l0l662l4954l2-1.0.5.4l10l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=5d90671964ba4230&biw=1366&bih=627")
2) Although I would recommend sticking with the standard prompt, you can do it by opening the terminal and typing

```
PS1="my_custom_prompt "
```

But first run

```
echo $PS1
```

and save the resulting line of gibberish in a text file, so you can quickly revert to standard if you want.

3) [How to change username]("http://www.google.com/#hl=en&biw=1366&bih=627&sclient=psy-ab&q=how+to+change+username+in+ubuntu&pbx=1&oq=how+to+change+username+in+ubuntu&aq=f&aqi=g4&aql=&gs_sm=3&gs_upl=494l3716l0l3933l32l15l0l0l0l0l764l4617l4-2.4.2l8l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=5d90671964ba4230")

---

### Post by Disabled20240622 on 2012-02-27
Regarding the prompt, it sounds like you want to do this once:

```
echo "export PS1=\"\u \"" >> ~/.bashrc
```

I don't think that's a very useful prompt though. I use a coluored one where It's normally:

**[COLOR="Lime"]user@hostname[/COLOR] [COLOR="RoyalBlue"]/some/directory[/COLOR] $** some command

Unless a command fails (returns non-zero status, like "2"), then it's:

**[COLOR="Red"][2][/COLOR] [COLOR="Lime"]user@hostname[/COLOR] [COLOR="RoyalBlue"]/some/directory[/COLOR] $** some command

And when I sudo -s it becomes:

**[COLOR="Red"]root@hostname[/COLOR] [COLOR="RoyalBlue"]/some/directory[/COLOR] # **some command

It's striking enouh to tell we just got a prompt, it shows my return codes, it reminds me when I'm root and it supports double click copying for just the bit I want to copy the most. On my test boxes I have it post the time, so I can see what time I ran commands when raising defects.

---

### Post by chenxinghao on 2012-02-28
Thanks for the reply.

The link to "How to change computer name" doesn't seem to provide correct information. On my Ubuntu 11.10 installation, there is no System -> Administrative -> .... From the tools symbol on the top-right corner I get System Settings and in the pan there is this System Info that is closest to the subject and no changes can be made in it.

What does "~$" mean in a Terminal command line header and why it is there?

Where (or in which set-up file) the "~$" is defined/specified to appear in the Terminal command line header?

Excuse my rudimentary ignorance of Linux traditions - I am learning the basic structures of Ubuntu. 

Many thanks.

---

### Post by howefield on 2012-02-28
To change the hostname try editing /etc/hostname and /etc/hosts eg, using the terminal...

```
gksudo gedit /etc/hostname
```
and

```
gksudo gedit /etc/hosts
```

Probably need a logout and log back in or reboot to take effect.

---

### Post by nothingspecial on 2012-02-28
Like stated before, I would just change your prompt rather than your computers hostname.

Your prompt can be anything you like. In ubuntu the default is for it to be ```
username@host:path_to_working_directory$
```

It is set in the file ~/.bashrc to this

```
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
```

\u = user
\h = hostname
\w = where you are in the file system

There are many many options such as the date and time etc

Here is a tutorial

[http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html)

---

### Post by matt_symes on 2012-02-28
> **chenxinghao said:**
> Thanks for the reply.

The link to "How to change computer name" doesn't seem to provide correct information. On my Ubuntu 11.10 installation, there is no System -> Administrative -> .... From the tools symbol on the top-right corner I get System Settings and in the pan there is this System Info that is closest to the subject and no changes can be made in it.

Try this link.

[http://www.tech-recipes.com/rx/2732/ubuntu_how_to_change_computer_name/](http://www.tech-recipes.com/rx/2732/ubuntu_how_to_change_computer_name/)

> 
What does "~$" mean in a Terminal command line header and why it is there?

That means you are in your home directory. ~ is shorthand for your home directory

> 
Where (or in which set-up file) the "~$" is defined/specified to appear in the Terminal command line header?

It's in the file ~/.bashrc in your home directory.

> 
Excuse my rudimentary ignorance of Linux traditions - I am learning the basic structures of Ubuntu. 

Many thanks.

No problem. 

EDIT: Blimey you guys type fast  ;)

Kind regards

---

### Post by drmrgd on 2012-02-28
> **BigglesPiP said:**
> Regarding the prompt, it sounds like you want to do this once:

```
echo "export PS1=\"\u \"" >> ~/.bashrc
```

I don't think that's a very useful prompt though. I use a coluored one where It's normally:

**[COLOR="Lime"]user@hostname[/COLOR] [COLOR="RoyalBlue"]/some/directory[/COLOR] $** some command

Unless a command fails (returns non-zero status, like "2"), then it's:

**[COLOR="Red"][2][/COLOR] [COLOR="Lime"]user@hostname[/COLOR] [COLOR="RoyalBlue"]/some/directory[/COLOR] $** some command

And when I sudo -s it becomes:

**[COLOR="Red"]root@hostname[/COLOR] [COLOR="RoyalBlue"]/some/directory[/COLOR] # **some command

It's striking enouh to tell we just got a prompt, it shows my return codes, it reminds me when I'm root and it supports double click copying for just the bit I want to copy the most. On my test boxes I have it post the time, so I can see what time I ran commands when raising defects.

That's a nice idea.  For the lazy and uninitiated amongst us *cough* would you mind sharing the code for that?  I'm constantly deep in directories and working with really long filenames and have a hard time finding my prompt from time to time :oops:

---

### Post by Disabled20240622 on 2012-02-28
> **drmrgd said:**
> That's a nice idea.  For the lazy and uninitiated amongst us *cough* would you mind sharing the code for that?  I'm constantly deep in directories and working with really long filenames and have a hard time finding my prompt from time to time :oops:

no problem

uncomment "force_color_prompt=yes" (you might want to stop here), then put this in place of the current coloured prompt definition (search for this line: 'if [ "$color_prompt" = yes ]; then'):

```

function statstring {
RC=$?
  if [ "0" != $RC ]; then
    printf "[$RC] "
  fi
}

if [ "$color_prompt" = yes ]; then
    if [ "$USER" = root ]; then
        PS1='\[\033[01;31m\]$(statstring)\[\033[00m\]${debian_chroot:+($debian_chroot)}\[\033[01;31m\]\u@\h\[\033[00m\] \[\033[01;34m\]\w\[\033[00m\] \$ '
    else
        PS1='\[\033[01;31m\]$(statstring)\[\033[00m\]${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\] \[\033[01;34m\]\w\[\033[00m\] \$ '
    fi
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

```

---

### Post by chenxinghao on 2012-02-28
Thanks for all inputs.

For now, I just remove user_ID@hose_name in the .bashrc file from the Terminal command line prompt.

---

### Post by drmrgd on 2012-02-29
> **BigglesPiP said:**
> no problem

uncomment "force_color_prompt=yes" (you might want to stop here), then put this in place of the current coloured prompt definition (search for this line: 'if [ "$color_prompt" = yes ]; then'):

```

function statstring {
RC=$?
  if [ "0" != $RC ]; then
    printf "[$RC] "
  fi
}

if [ "$color_prompt" = yes ]; then
    if [ "$USER" = root ]; then
        PS1='\[\033[01;31m\]$(statstring)\[\033[00m\]${debian_chroot:+($debian_chroot)}\[\033[01;31m\]\u@\h\[\033[00m\] \[\033[01;34m\]\w\[\033[00m\] \$ '
    else
        PS1='\[\033[01;31m\]$(statstring)\[\033[00m\]${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\] \[\033[01;34m\]\w\[\033[00m\] \$ '
    fi
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

```


Very nice!  I love the new prompt.  Thanks so much!

---

### Post by matt_symes on 2012-02-29
Hi

If you like coloured prompts, how about coloured man pages. If you want these then install most.

You will need to enable the universe repository. Then install most. Open a terminal and type

```
sudo apt-get install most
```

Run this command to add export PAGER="most" to your .bashrc file.

```
echo 'export PAGER="most"' >> .bashrc
```

After doing that re-source your .bashrc.

```
source .bashrc
```

Then check out the man pages for say apt.

See that attached screen shot. I find it much easier to read.

Kind regards

---

### Post by sudodus on 2012-02-29
> **BigglesPiP said:**
> no problem

uncomment "force_color_prompt=yes" (you might want to stop here), then put this in place of the current coloured prompt definition (search for this line: 'if [ "$color_prompt" = yes ]; then'):

```

function statstring {
RC=$?
  if [ "0" != $RC ]; then
    printf "[$RC] "
  fi
}

if [ "$color_prompt" = yes ]; then
    if [ "$USER" = root ]; then
        PS1='\[\033[01;31m\]$(statstring)\[\033[00m\]${debian_chroot:+($debian_chroot)}\[\033[01;31m\]\u@\h\[\033[00m\] \[\033[01;34m\]\w\[\033[00m\] \$ '
    else
        PS1='\[\033[01;31m\]$(statstring)\[\033[00m\]${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\] \[\033[01;34m\]\w\[\033[00m\] \$ '
    fi
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

```
I have installed your colour prompt and it is very nice. Thank you for sharing :KS

---

### Post by Khayyam on 2012-02-29
> **sudodus said:**
> I have installed your colour prompt and it is very nice. Thank you for sharing

I have something similar (for zsh) though I also check local and remote connections and change the user@host (seperately) based on user (yellow/red for user and root respectively) and location (local and ssh). It also chomps the path if it gets too long (but this may be a zshprompt only feature, I'm not sure). I could post a bashified example if anyone is interested.

Matt ... [lesspipe.sh]("http://www-zeuthen.desy.de/%7Efriebel/unix/lesspipe.html") (using the LESSOPEN variable) will also colourise manpages, allow you to 'page' 'tar:/path', 'bz2:/path', 'zip:/path', 'rar:/path', pdf, MS Word, Openoffice/LibreOffice docs, .ps, .debs, gpg encrypted files .. and many, many ... ummm ... 'less'.

Less is more only better!

best ... khay

---

### Post by matt_symes on 2012-02-29
> Matt ... lesspipe.sh (using the LESSOPEN variable) will also colourise manpages, allow you to 'page' 'tar:/path', 'bz2:/path', 'zip:/path', 'rar:/path', pdf, MS Word, Openoffice/LibreOffice docs, .ps, .debs, gpg encrypted files .. and many, many ... ummm ... 'less'.

Less is more only better!

Thanks Khayyam. I will check that out.

---

### Post by sudodus on 2012-03-01
> **Khayyam said:**
> I have something similar (for zsh) though I also check local and remote connections and change the user@host (seperately) based on user (yellow/red for user and root respectively) and location (local and ssh). It also chomps the path if it gets too long (but this may be a zshprompt only feature, I'm not sure). [COLOR=Red]I could post a bashified example if anyone is interested.[/COLOR]

Matt ... [lesspipe.sh]("http://www-zeuthen.desy.de/%7Efriebel/unix/lesspipe.html") (using the LESSOPEN variable) will also colourise manpages, allow you to 'page' 'tar:/path', 'bz2:/path', 'zip:/path', 'rar:/path', pdf, MS Word, Openoffice/LibreOffice docs, .ps, .debs, gpg encrypted files .. and many, many ... ummm ... 'less'.

Less is more only better!

best ... khay
Yes please :-)

---

### Post by Khayyam on 2012-03-01
> **sudodus said:**
> Yes please

This should give you some idea how to proceed, I provided only two PS1's as I'm not sure what colors and/or prompt escapes you might want. It fairly simple just set the PS1 with the prompt and change the colors for "\u" and "\h" for each (I use a yellow=nopriv, red=priv, yellow=local, blue=ssh .. but with a different set of colours escape codes that bash doesn't like ... I assume as PS1 is in double not single quotes as with zsh).

Note \[$color\] is protected within \[  ....... \] and that I've only uncommented the basic colors and 'IBlue'.

I did test it ... briefly ... and so it should work as expected, but you'll definitely want to tinker with it to get the right combinations of colors and prompt escapes.

```
if [[ -n ${SSH_CLIENT} ]]; then
    CONN="ssh"
else
    CONN="local"
fi

if [[ ${UID} == "0" ]]; then
    USR="priv"
else
    USR="nopriv"
fi

# Colour Definitons:

# Reset
Color_Off='\e[0m'       # Text Reset

# Regular Colors
Black='\e[0;30m'        # Black
Red='\e[0;31m'          # Red
Green='\e[0;32m'        # Green
Yellow='\e[0;33m'       # Yellow
Blue='\e[0;34m'         # Blue
Purple='\e[0;35m'       # Purple
Cyan='\e[0;36m'         # Cyan
White='\e[0;37m'        # White

## Bold
#BBlack='\e[1;30m'       # Black
#BRed='\e[1;31m'         # Red
#BGreen='\e[1;32m'       # Green
#BYellow='\e[1;33m'      # Yellow
#BBlue='\e[1;34m'        # Blue
#BPurple='\e[1;35m'      # Purple
#BCyan='\e[1;36m'        # Cyan
#BWhite='\e[1;37m'       # White

## Underline
#UBlack='\e[4;30m'       # Black
#URed='\e[4;31m'         # Red
#UGreen='\e[4;32m'       # Green
#UYellow='\e[4;33m'      # Yellow
#UBlue='\e[4;34m'        # Blue
#UPurple='\e[4;35m'      # Purple
#UCyan='\e[4;36m'        # Cyan
#UWhite='\e[4;37m'       # White

## Background
#On_Black='\e[40m'       # Black
#On_Red='\e[41m'         # Red
#On_Green='\e[42m'       # Green
#On_Yellow='\e[43m'      # Yellow
#On_Blue='\e[44m'        # Blue
#On_Purple='\e[45m'      # Purple
#On_Cyan='\e[46m'        # Cyan
#On_White='\e[47m'       # White

## High Intensty
#IBlack='\e[0;90m'       # Black
#IRed='\e[0;91m'         # Red
#IGreen='\e[0;92m'       # Green
#IYellow='\e[0;93m'      # Yellow
IBlue='\e[0;94m'        # Blue
#IPurple='\e[0;95m'      # Purple
#ICyan='\e[0;96m'        # Cyan
#IWhite='\e[0;97m'       # White

## Bold High Intensty
#BIBlack='\e[1;90m'      # Black
#BIRed='\e[1;91m'        # Red
#BIGreen='\e[1;92m'      # Green
#BIYellow='\e[1;93m'     # Yellow
#BIBlue='\e[1;94m'       # Blue
#BIPurple='\e[1;95m'     # Purple
#BICyan='\e[1;96m'       # Cyan
#BIWhite='\e[1;97m'      # White

## High Intensty backgrounds
#On_IBlack='\e[0;100m'   # Black
#On_IRed='\e[0;101m'     # Red
#On_IGreen='\e[0;102m'   # Green
#On_IYellow='\e[0;103m'  # Yellow
#On_IBlue='\e[0;104m'    # Blue
#On_IPurple='\e[10;95m'  # Purple
#On_ICyan='\e[0;106m'    # Cyan
#On_IWhite='\e[0;107m'   # White

# colour selection test: echo -e "${blue}BLUE"

# SET PROMPT

if [ ${CONN} == local -a ${USR} == nopriv ] ; then
    PS1="[\[$Yellow\]\u\[$Black\]@\[$IBlue\]\h\[$Green\] \W\[$Black\]]$ "
elif [ ${CONN} == local -a ${USR} == priv ] ; then
    PS1="[\[$Red\]\u\[$Black\]@\[$IBlue\]\h\[$Green\] \W\[$Black\]]$ "
elif [ ${CONN} == ssh -a ${USR} == nopriv ] ; then
    PS1=""
elif [ ${CONN} == ssh -a ${USR} == priv ] ; then
    PS1=""
else
    PS1=""
fi
```best ... khay

---

### Post by drmrgd on 2012-03-01
> **matt_symes said:**
> Hi

If you like coloured prompts, how about coloured man pages. If you want these then install most.

You will need to enable the universe repository. Then install most. Open a terminal and type

```
sudo apt-get install most
```

Run this command to add export PAGER="most" to your .bashrc file.

```
echo 'export PAGER="most"' >> .bashrc
```

After doing that re-source your .bashrc.

```
source .bashrc
```

Then check out the man pages for say apt.

See that attached screen shot. I find it much easier to read.

Kind regards

Thanks for sharing that Matt!  I totally forgot about most, and now that you've reminded me how nice man pages are when they're in color, I installed it right away.

Nothing like a nice looking terminal to help commandline work along :D

Nice color chart Kayyam!  I'm going to hang on to that one; it's a lot more thorough than the one I've been using.

---

### Post by WasMeHere on 2012-03-01
Thanks Khayyam,

It works with your colours. Now there is a choice. Since I have light-yellow background in the terminal windows, I will change the colours a little to get good contrast.

---

### Post by ubuntu27 on 2012-03-02
[How to easily change your username in Ubuntu 11.10 ]("http://iloveubuntu.net/how-easily-change-your-username-ubuntu-1110")

---

### Post by Khayyam on 2012-03-02
> **Olle Wiklund said:**
> Thanks Khayyam, It works with your colours. Now there is a choice. Since I have light-yellow background in the terminal windows, I will change the colours a little to get good contrast.

Your welcome ... that the idea, the above it just a template for tinkering. My own zshprompt (which the basic test conditions are adapted from) has additional prompt escapes (I have the current history number to the right of the prompt in red (like so [[COLOR=DarkOrange]user[/COLOR]@[COLOR=RoyalBlue]host[/COLOR] ~]% .... [[COLOR=DarkRed]231[/COLOR]]"), and as I'm not a bash user I'm not too familiar with what the bash prompt capabilities are, so I kept it fairly basic.

Anyhow, I'm sure that with a little bit of tinkering with colours, bash prompt escape codes, and setting priv/nopriv and local/ssh to different colours it'll work as advertised. BTW, it needs distributing it to the various machines you have shell access to it.

Incidentally I've written another script to do just that, its designed to make keeping all dotfiles sync'ed between a 'skel' and all the hosts you might want these kept in sync.

best ... khay

---

### Post by sudodus on 2012-03-04
Thank you Khayyam :KS

---

### Post by Khayyam on 2012-03-04
> **sudodus said:**
> Thank you Khayyam

your welome ... btw, I'd made some changes to my .zshrc as I realised that some of my  previous tests were either un-necessary or returned an empty string, it  was written some time back prior to sshd providing shell variables and  so needed to be brought up-to-date. Previously I use to have to check on tty, and that 0:0 wasn't set (for ssh -X) but I'm pretty sure that this is nologer necessary with the env variable provided by sshd. It seems to be working as expected but if you discover any problem with it let me know.

best ... khay

---

