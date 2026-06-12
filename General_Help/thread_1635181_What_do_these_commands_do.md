---
title: "What do these commands do?"
date: 2010-12-01
forum: General Help
---

### Post by ChaosChris2009 on 2010-12-01
[CENTER]Could someone possible tell me what these commands do?

```
dmesg | grep -i kill
```

```
[CODE]dmesg | grep -i net
```[/CODE]

```
ifconfig -a
```[/CENTER]

---

### Post by tgm4883 on 2010-12-01
> **ChaosChris2009 said:**
> [CENTER]Could someone possible tell me what these commands do?

```
dmesg | grep -i kill
```

```
[CODE]dmesg | grep -i net
```[/CODE]

```
ifconfig -a
```[/CENTER]

You can by doing these in a terminal (man shows you the manual page for the command. You can even man man)

```
man dmesg
man grep
man ifconfig
```

The | is a pipe. Simply put it takes the output of the first command and sends it to the second command

---

### Post by ChaosChris2009 on 2010-12-01
> **tgm4883 said:**
> You can by doing these in a terminal (man shows you the manual page for the command. You can even man man)

```
man dmesg
man grep
man ifconfig
```

The | is a pipe. Simply put it takes the output of the first command and sends it to the second command

I know how to use and run commands via Terminal, but I wish to know what actions the commands do before I actually open Terminal and try them

---

### Post by bowens44 on 2010-12-01
> **ChaosChris2009 said:**
> I know how to use and run commands via Terminal, but I wish to know what actions the commands do before I actually open Terminal and try them

man dmesg
man grep
man ifconfig

these will tell you what the commands do.

---

### Post by Spyderkid on 2010-12-01
This is what dmesg and grep do

```

DMESG(1)                                                              DMESG(1)

NAME
       dmesg - print or control the kernel ring buffer

SYNOPSIS
       dmesg [-c] [-r] [-n level] [-s bufsize]

DESCRIPTION
       dmesg is used to examine or control the kernel ring buffer.

       The program helps users to print out their bootup messages.  Instead of
       copying the messages by hand, the user need only:
              dmesg > boot.messages
       and mail the boot.messages file to whoever can debug their problem.

OPTIONS
       -c     Clear the ring buffer contents after printing.

       -r     Print the raw message buffer, i.e., don't strip  the  log  level
              prefixes.

       -s bufsize

 Use  a  buffer  of size bufsize to query the kernel ring buffer.
              This is 16392 by default.  (The  default  kernel  syslog  buffer
              size was 4096 at first, 8192 since 1.3.54, 16384 since 2.1.113.)
              If you have set the kernel buffer to be larger than the  default
              then this option can be used to view the entire buffer.

       -n level
              Set  the  level at which logging of messages is done to the con&#8208;
              sole.  For example, -n 1 prevents  all  messages,  except  panic
              messages, from appearing on the console.  All levels of messages
              are still written to /proc/kmsg, so syslogd(8) can still be used
              to  control  exactly  where kernel messages appear.  When the -n
              option is used, dmesg will not print or clear  the  kernel  ring
              buffer.

              When  both options are used, only the last option on the command
              line will have an effect.

```

```

NAME
       grep, egrep, fgrep, rgrep - print lines matching a pattern

SYNOPSIS
       grep [OPTIONS] PATTERN [FILE...]
       grep [OPTIONS] [-e PATTERN | -f FILE] [FILE...]

DESCRIPTION
       grep  searches the named input FILEs (or standard input if no files are
       named, or if a single hyphen-minus (-) is given as file name) for lines
       containing  a  match to the given PATTERN.  By default, grep prints the
       matching lines.

       In  addition,  three  variant  programs  egrep,  fgrep  and  rgrep  are
       available.   egrep  is  the  same  as  grep -E.   fgrep  is the same as
       grep -F.  rgrep is the same as grep -r.  Direct  invocation  as  either
       egrep  or  fgrep  is  deprecated,  but  is provided to allow historical
       applications that rely on them to run unmodified.

OPTIONS
   Generic Program Information
 -V, --version
              Print  the version number of grep to the standard output stream.
              This version number should be included in all bug  reports  (see
              below).

   Matcher Selection
       -E, --extended-regexp
              Interpret  PATTERN  as  an extended regular expression (ERE, see
              below).  (-E is specified by POSIX.)

       -F, --fixed-strings
              Interpret PATTERN as a  list  of  fixed  strings,  separated  by
              newlines,  any  of  which is to be matched.  (-F is specified by
              POSIX.)

       -G, --basic-regexp
              Interpret PATTERN  as  a  basic  regular  expression  (BRE,  see
              below).  This is the default.

       -P, --perl-regexp
Matching Control
       -e PATTERN, --regexp=PATTERN
              Use PATTERN as  the  pattern.   This  can  be  used  to  specify
              multiple search patterns, or to protect a pattern beginning with
              a hyphen (-).  (-e is specified by POSIX.)

       -f FILE, --file=FILE
              Obtain patterns  from  FILE,  one  per  line.   The  empty  file
              contains  zero  patterns, and therefore matches nothing.  (-f is
              specified by POSIX.)

       -i, --ignore-case
              Ignore case distinctions in  both  the  PATTERN  and  the  input
              files.  (-i is specified by POSIX.)

       -v, --invert-match
              Invert the sense of matching, to select non-matching lines.  (-v
              is specified by POSIX.)

       -w, --word-regexp
              Select only those  lines  containing  matches  that  form  whole
              words.   The  test is that the matching substring must either beat the  beginning  of  the  line,  or  preceded  by  a  non-word
              constituent  character.  Similarly, it must be either at the end
              of the line or followed by  a  non-word  constituent  character.
              Word-constituent   characters   are  letters,  digits,  and  the
              underscore.

       -x, --line-regexp
              Select only those matches that exactly  match  the  whole  line.
              (-x is specified by POSIX.)

       -y     Obsolete synonym for -i.

   General Output Control
       -c, --count
              Suppress  normal output; instead print a count of matching lines
              for each input file.  With the -v,  --invert-match  option  (see
              below), count non-matching lines.  (-c is specified by POSIX.)

 Manual page grep(1) line 69



```

---

### Post by endotherm on 2010-12-01
the first two don't do much, except search your dmesg.log for the non-cased literals 'kill' and 'net', returning the lines on which they are found.  not terribly useful in an of itself. 

the last command shows you your current Network card IP configuration, for all NICs even the disabled ones (-a is 'all').

---

### Post by matt_symes on 2010-12-01
Hi

Don't worry. These commands, as is, are safe to run. endotherms explanation is correct.

The point about the man pages is correct. If you need to know what something does read the pages. They are your friend :) (if a little dry a times)

Kind regards

---

### Post by Hippytaff on 2010-12-01
When I first was asked in this forum to post the output of a command with kill in the line I thought it was something dodgy :-)

Your fairly safe here...if in doubt as already suggested check the man page :-)

---

### Post by jocko on 2010-12-01
[LEFT]```
dmesg | grep -i kill
```If you didn't get it from the manual and the previous replies:
dmesg prints the kernel ring buffer.
The "|" redirects ("pipes") the output of the previous command to the next command...
grep searches for an expression pattern in a file (or in the output from a previous command).
So altogether the whole line will look for the word "kill" in the kernel ring buffer (the -i switch makes it case-insensitive), and if it finds it it will print the line containing the word.```
dmesg | grep -i net
```Same as above, but looks for the word "net".
[/LEFT]
```
ifconfig -a
```Prints the configuration of your network connections.
```
man ifconfig
```Shows you the manual for the ifconfig program.
```
man dmesg
```Shows you the manual for the dmesg command.
```
man bash
```Shows you the manual of the shell.
```
man man
```Shows you the manual of the program that shows you the manual.

---

