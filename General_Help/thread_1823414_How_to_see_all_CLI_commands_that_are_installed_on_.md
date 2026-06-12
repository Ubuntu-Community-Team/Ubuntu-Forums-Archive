---
title: "How to see all CLI commands that are installed on my OS?"
date: 2011-08-12
forum: General Help
---

### Post by SidebySide on 2011-08-12
Hi Free-Users
--------------
Is this part of forum the correct where I'm asking about terminal?
Why is not any tunnel specified for terminal/console in this forum?

1. How can I find tutorials for below special characters, which use into terminal:
```
~ ^ * _ - + ; : ? ' " ! @ # $ % &  {} []  () <> / \ | ./ Space-bar Tab-Key Return
```on web or through the man pages into terminal?

2.  1. How can I copy/print my CLI commands list (default+installed) that comes with "man <Tab> <Tab>" or other man pages that are shown in several pages within  terminal/console?

---

### Post by ~!geek!~ on 2011-08-12
There are a lot of linux cli tutorials available. You may like to visit [www.linuxcommand.org](www.linuxcommand.org) to get a feel of the way linux command line work. To know about the specific symbols you can learn some commands like grep etc. from there which uses a number of symbols you mentioned. 

To print the cli commands your terminal can understand (default+installed), Just press tab once or twice just after opening terminal. It will ask you to show some three thousand odd commands, type y or yes as required. After printing all the commands copy and paste in some file. 
Other way is: Just visit the directiories /bin, /usr/bin etc. using ls command in the directories. These consists of  binary files for all commands. Now copy the command names in files.

---

### Post by Habitual on 2011-08-12
> **SidebySide said:**
> ...How can I copy/print my CLI commands list (default+installed) that comes with "man <Tab> <Tab>" or other man pages that are shown in several pages within  terminal/console?

What are they? ("Display all 4567 possibilities?")
```
compgen -c | sort -u > commands && less commands
```

for man pages:
```
man --regex text
```
enjoy.

---

### Post by SidebySide on 2011-08-13
> 2. How can I copy/print my CLI commands list (default+installed) that comes with "man <Tab> <Tab>" or other man pages that are shown in several pages within  terminal/console?...means, for example:
```
$ man cmus
```The OUTPUT in firs page of my terminal screen:
```
CMUS(1)                                                                CMUS(1)
NAME
       cmus - C* Music Player
SYNOPSIS
       cmus [options]
DESCRIPTION
       cmus is a small ncurses based music player.  It supports various output
       methods by output-plugins. It has got completely configurable
       keybindings and it can be controlled from the outside via
       cmus-remote(1).
OPTIONS
       --listen ADDR
              Listen to ADDR (UNIX socket) instead of ~/.cmus/socket. ADDR is
              either a UNIX socket or host[:port].

              WARNING: Using host[:port] is insecure even with password! It
              might be useful though in LAN if you want multiple local users
              to able to control cmus.  Never make cmus listen to the
              internet.
 [SIZE=2][COLOR=Red]**Manual page cmus(1) line 1**[/COLOR][/SIZE]
```manual page cmus(1) line [COLOR=SeaGreen]26[/COLOR]  **[COLOR=RoyalBlue]=>[/COLOR]** 26? becaus of my terminal screen: 400*600
manual page cmus(1) line 40
manual page cmus(1) line 49
...

Now I should copy each page contents separately in 47 times(=try) and paste them into a text file 47 times, too!
so I wanna copy them just once = copy all contents of  [COLOR=DarkOrange]man cmus[/COLOR] (e.g.) in one try.
How?
this command line:
```
compgen -c | sort -u > commands && less commands
```just list command = <Tab><Tab> in staring terminal.
AND this one:
```
man --regex text
```navigate me in to [COLOR=Magenta]man gettext[/COLOR] page!!!
[COLOR=Red]_---------------------------------------------------------------------------------_[/COLOR]

```
1. How can I find tutorials for below special characters, which use into  terminal:
[CODE]~ ^ * _ - + ; : ? ' " ! @ # $ % &  {} []  () <> / \ | ./  Space-bar Tab-Key Return
```on web or through the man pages into  terminal?[/CODE]I wanna a guide just for mentioned character. I've enough guide to CLI!
[COLOR=Red]_~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~_[/COLOR]

tnx to [~!geek!~]("http://ubuntuforums.org/member.php?u=1202974") & [Habitual]("http://ubuntuforums.org/member.php?u=504341") for their answers.

---

### Post by AlphaLexman on 2011-08-13
If you are interested in converting man pages see '**manconv**'

And from the bash man page...
```
  Special Parameters
       The  shell  treats several parameters specially.  These parameters may only be referenced;
       assignment to them is not allowed.
       *      Expands to the positional parameters, starting from one.  When the expansion occurs
              within  double quotes, it expands to a single word with the value of each parameter
              separated by the first character of the IFS special variable.   That  is,  "$*"  is
              equivalent  to  "$1c$2c...", where c is the first character of the value of the IFS
              variable.  If IFS is unset, the parameters are separated  by  spaces.   If  IFS  is
              null, the parameters are joined without intervening separators.
       @      Expands to the positional parameters, starting from one.  When the expansion occurs
              within double quotes, each parameter expands to a separate word.  That is, "$@"  is
              equivalent  to  "$1" "$2" ...  If the double-quoted expansion occurs within a word,
              the expansion of the first parameter is joined with the beginning part of the orig&#8208;
              inal  word, and the expansion of the last parameter is joined with the last part of
              the original word.  When there are no positional parameters, "$@" and $@ expand  to
              nothing (i.e., they are removed).
       #      Expands to the number of positional parameters in decimal.
       ?      Expands to the exit status of the most recently executed foreground pipeline.
       -      Expands  to  the  current  option  flags  as  specified upon invocation, by the set
              builtin command, or those set by the shell itself (such as the -i option).
       $      Expands to the process ID of the shell.  In  a  ()  subshell,  it  expands  to  the
              process ID of the current shell, not the subshell.
       !      Expands  to  the process ID of the most recently executed background (asynchronous)
              command.
       0      Expands to the name of the shell or shell script.  This is set at shell initializa&#8208;
              tion.   If  bash  is invoked with a file of commands, $0 is set to the name of that
              file.  If bash is started with the -c option, then $0 is set to the first  argument
              after  the  string  to be executed, if one is present.  Otherwise, it is set to the
              file name used to invoke bash, as given by argument zero.
       _      At shell startup, set to the absolute pathname used to invoke the  shell  or  shell
              script being executed as passed in the environment or argument list.  Subsequently,
              expands to the last argument to the previous command, after expansion.  Also set to
              the  full  pathname used to invoke each command executed and placed in the environ&#8208;
              ment exported to that command.  When checking mail, this parameter holds  the  name
              of the mail file currently being checked.


```

---

### Post by SidebySide on 2011-09-30
> **AlphaLexman said:**
> If you are interested in converting man pages see '**manconv**'
[/CODE]
"see **[COLOR=Black]manconv[/COLOR]**" => ???


> **SidebySide said:**
> Hi Free-Users
How can I copy/print my CLI  commands list (default+installed) that comes with "man <Tab>  <Tab>" or other man pages that are shown in several pages within   terminal/console?
Answer; Ex:
man nano > man-nano.txt

---

