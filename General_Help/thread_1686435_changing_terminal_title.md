---
title: "changing terminal title"
date: 2011-02-12
forum: General Help
---

### Post by unix-lover-2011 on 2011-02-12
Hallo All,

I wanted to change terminal title via command line.
Here is what I was doing.
gnome-terminal --title="Sample Window"

this works but on new terminal once I get my command prompt it changes to default which is id@domain name home working directory.

I also tried PROMPT_COMMAND method but that too is not working any help would be much appreciated.

PROMPT_COMMAND

export PROMPT_COMMAND='echo -ne "\033]0;"Coo Sample Stuff Title"\007"'

---

### Post by gmargo on 2011-02-12
Look at the value of your **$PS1** shell variable.  That's the main prompt and is where the id@domain is coming from.

---

### Post by unix-lover-2011 on 2011-02-12
Good I tried that as well.

But guess what happens!?
ameya@ubuntu-desktop:~$ PROMPT_COMMAND='echo -ne "\033]0;"Sample-Windows"\007"'
ameya@ubuntu-desktop:~$ echo $?
0
ameya@ubuntu-desktop:~$ PS1='echo -ne "\033]0;"Sample-Windows"\007"'echo -ne ""
echo -ne ""id
uid=1000(ameya) gid=1000(ameya) groups=1000(ameya),4(adm),20(dialout),24(cdrom),46(plugdev),111(lpadmin),119(admin),122(sambashare),1001(vboxsf)
echo -ne ""
echo -ne ""
echo -ne ""su - ameya
Password: 
ameya@ubuntu-desktop:~$ 

SO If change variable from PROMPT_COMMAND to PS1 trick is performed but prompt is compromised.

Any suggestions?

---

### Post by gmargo on 2011-02-12
What I would suggest is:
a. get rid of PROMPT_COMMAND
b. edit your $HOME/.bashrc file and comment out this block, which starts about line 59 if your .bashrc is the standard default one:
```

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

```

---

### Post by unix-lover-2011 on 2011-02-12
naah mate it is still not working.

did exactly the same commented out, saved file.
Performed PS1 but still I can't understand why am I getting.
ameya@ubuntu-desktop:~$ vi /home/ameya/.bashrc
ameya@ubuntu-desktop:~$ PS1='echo -ne "\033]0;"Ameya-Sample-Window"\007"'echo -ne ""
echo -ne ""

nope its not working something weird is happening

see my prompt now!
echo -ne ""clear

look what the status now! I dint do this,

echo -ne ""clearecho $PS1
echo -ne "\033]0;"Ameya-Sample-Window"\007"clear
echo -ne ""clear



yeah we are getting closer...

---

### Post by gmargo on 2011-02-12
After you edit your .bashrc, reread it by typing "source .bashrc".
(Also "unset PROMPT_COMMAND" to get rid of that one.)

```

$ unset PROMPT_COMMAND
$ vi .bashrc
$ source .bashrc

```
And now your $PS1 should be set to the value from the .bashrc.

---

### Post by unix-lover-2011 on 2011-02-12
guess now what! ?

yay issue is resolved.

Commenting and the re-assigning PS1 variable and then re-reading performs the trick!
PS1='echo -ne "\033]0;"Shell-Scripting"\007"'
source ~/.bashrc

I had terminal with Title as Shell-Scripting and you know! if I perform gnome-terminal with title argument it works perfectly fine.

SO I would like to now ask you what exactly we did when commented out section line 59 to 66?

Many Thanks for your Assistance.

---

