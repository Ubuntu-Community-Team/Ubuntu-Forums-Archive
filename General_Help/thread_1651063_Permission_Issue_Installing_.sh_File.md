---
title: "Permission Issue Installing .sh File"
date: 2010-12-22
forum: General Help
---

### Post by sleapz on 2010-12-22
So the issue that I'm having is this (please bear with me, linux noob):  I'm trying to install an application for Ubuntu that is in the form of .sh -- I have full read/write privileges to the file (box to run as executable is checked) and full read/write privileges to the /opt directory.  When I try and proceed with the install into /opt, I get told that I have no write privileges to the directory.

Any help would be appreciated.
Thanks

---

### Post by ean5533 on 2010-12-22
Unless you're logged in as the root user, it's unlikely that you have write permissions to /opt. What you most likely want to do is run the script by using sudo. For example:

```
sudo sh ./MY_AWESOME_SCRIPT.sh
```

That will run the script as root, which definitely has write permissions to /opt and all sub directories.

**Note: Make very, very sure that you trust the script you're running, because running it with sudo gives it the power to destroy everything (everything on your computer, not everything in the world)**

---

### Post by sleapz on 2010-12-22
Ok, I'll give that a shot.  I should add that my account is set up as an admin account and that I've installed other applications without issue, but this is the first .sh I've tried.  Also, would you mind explaining the sudo command and syntax.
Thanks

---

### Post by ean5533 on 2010-12-22
> **sleapz said:**
> Ok, I'll give that a shot.  I should add that my account is set up as an admin account and that I've installed other applications without issue, but this is the first .sh I've tried.
Shell scripts (that's what a .sh is) can be fussy because it depends on what exactly the script writer decided to do. Sometimes script writers are lazy and don't make their scripts as robust as they should be, and strange things can happen when running them as anyone except root.

> **sleapz said:**
> Also, would you mind explaining the sudo command and syntax.

sudo stands for **S**uper **U**ser **Do**, and all it does it run whatever command you send to it as the root user. It's pretty easy to use, just type:

```
sudo SOME_COMMAND
```

SOME_COMMAND can be anything that you want to do as the root user. If you chain multiple commands together by using &&, you'll have to put a sudo before each command that needs to be run as a super user. (If you don't know what I mean by chaining commands, don't worry about it)

If you want to use sudo to run a graphical program, such as gedit, then use **gksudo** instead. Example:

```
gksudo SOME_GRAPHICAL_PROGRAM
```

---

### Post by sleapz on 2010-12-22
Sweet, thanks.  Knew it was a script but I'm literally starting from the bottom when it comes to 'nix so I wasn't even sure on the relation of the script to Ubuntu and how it would install the actual app (no other file/directory was downloaded with it) and I didn't bother to read through it.  Thanks for the quick 101, I'll update my post when I get home and give it a try.

---

### Post by efflandt on 2010-12-22
Man pages in a terminal can be helpful for getting more information about commands.  So if you wanted to learn more about sudo, in a terminal do: **man sudo** (cursor keys or page up/down move through it, **q** to quit).

One useful command if you are not quite sure what a command is would be **apropos** to search for man pages for a word.  For example **apropos cron** would find man pages that refer to cron.  If there is more than one manpage with the same name, there would be a number after it, for example:

crontab (1) - maintain crontab files for individual users (Vixie Cron)
crontab (5) - tables for driving cron

**man crontab** would default to the 1st one, and **man 5 crontab** would open the 2nd.

Many install scripts that are not just scripts might contain binary code within them as DATA and will create the binaries from that data.

---

### Post by sleapz on 2010-12-22
So I gave it a shot and was able to install it after some trial and error (was typing the path to the .sh instead of using your statement).  Out of curiosity, why didn't I need to specify the path to the .sh file?
Thanks again.

@efflandt - thanks for the quick tutorial.

---

### Post by Girya on 2010-12-22
haven't followed the whole thread but where you installed the shell script is in your path env. thats where the shell looks for scripts to run that are called on the cl

try typing in a terminal

> echo $PATH

that will display all the paths that that the shell searches for scripts.

---

### Post by sleapz on 2010-12-23
Thanks again guys.

---

