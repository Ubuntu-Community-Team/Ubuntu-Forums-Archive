---
title: "Wine not opening programs?"
date: 2010-08-12
forum: General Help
---

### Post by GreezyFreezy on 2010-08-12
Ok so I was a regular windows user for ~10 years now, but my current pc wasnt installing windows for some reason so i switched to linux to try it out. I've been trying to run a few small games here and there to keep me entertained, and wine just isnt agreeing with me ... Any program i try to open with wine, it says "opening _____________" in the taskbar, and then NOTHING HAPPENS! This is really irritating me, becuase if i got an error message i could try to figure out whats wrong, but when NOTHING AT ALL happens, i get frustrated -.- Can anyone help me out? Im a huge linux noob

---

### Post by Vaphell on 2010-08-12
the best way to troubleshoot pretty much anything is to run stuff from command line, because apps spit out a lot of debug info there. Drop into terminal and run **wine <file.exe>**

---

### Post by GreezyFreezy on 2010-08-12
> **Vaphell said:**
> the best way to troubleshoot pretty much anything is to run stuff from command line, because apps spit out a lot of debug info there. Drop into terminal and run **wine <file.exe>**

When i want to go to a specific folder, i type cd /blahblahblah right?
my user is zazzy, so i try cd /home/zazzy/Downloads but nothing happens, it says no such file or directory, it doesnt even go to /home/zazzy for some reason

EDIT: i managed to get to /home/zazzy/Downloads but lets say theres a folder called Recent Downloads, and theres a space in the middle, how would i enter that in terminal? Same with the program

EDIT2: I did some googling, and found out that putting " " around the spaced parts makes it work
i entered the folder, entered: wine "________.exe" and this is the message that came up:

err:seh:setup_exception_record stack overflow 2340 bytes in thread 001e eip 7bc3f3be esp 00240a0c stack 0x240000-0x241000-0x340000

What does that mean?

---

### Post by JBAlaska on 2010-08-12
Are you running the install programs for these games?

For example:
```
wine install.exe
```

---

### Post by Vaphell on 2010-08-12
when dealing with spaces you can do 2 things: use "" or escape spaces - and you do that using '\'
that sign means 'next character is a part of string no matter what'
so you need to use
**cd Recent\ Downloads** (space is treated as a part of the name, not as a separator between the words)

also you can use an incredibly useful autocompletion with tab key
sometimes you need only one char or 2 to get what you need
for example:
**cd Re[tab]** will automagically put whole Recent Downloads without any need to type that manually. In case of similar names (**Rec**ent Downloads, **Rec**overy) when you type R and press tab, it will autocomplete to Rec because this is the common part that fits, now you must decide if the next char is 'e' or 'o', once you do that, tab will type the rest. That way you can produce very long paths with 5 actual keypresses tops. Also double tab shows list of possibilities. Once you learn that, gui feels clunky and wasteful to navigate :)


about error - no idea. Does wine do that with every exe?

---

### Post by GreezyFreezy on 2010-08-12
> **JBAlaska said:**
> Are you running the install programs for these games?

For example:
```
wine install.exe
```

I already installed the games, and also i got an emulator (no install nessessary) and even that wouldnt run.

---

### Post by Vaphell on 2010-08-12
[http://appdb.winehq.org/](http://appdb.winehq.org/)

look if your apps are mentioned there and if they work

---

### Post by GreezyFreezy on 2010-08-12
> **Vaphell said:**
> when dealing with spaces you can do 2 things: use "" or escape spaces - and you do that using '\'
that sign means 'next character is a part of string no matter what'
so you need to use
**cd Recent\ Downloads** (space is treated as a part of the name, not as a separator between the words)

also you can use an incredibly useful autocompletion with tab key
sometimes you need only one char or 2 to get what you need
for example:
**cd Re[tab]** will automagically put whole Recent Downloads without any need to type that manually. In case of similar names (**Rec**ent Downloads, **Rec**overy) when you type R and press tab, it will autocomplete to Rec because this is the common part that fits, now you must decide if the next char is 'e' or 'o', once you do that, tab will type the rest. That way you can produce very long paths with 5 actual keypresses tops. Also double tab shows list of possibilities. Once you learn that, gui feels clunky and wasteful to navigate :)


about error - no idea. Does wine do that with every exe?

Thanks for the info!
Tried the same procedure with a different .exe, here are the results:

zazzy@Zooz-Top:~/Downloads$ cd /home/zazzy/Downloads/"Metal Slug 1,2,3,4,5 & X  PC"
zazzy@Zooz-Top:~/Downloads/Metal Slug 1,2,3,4,5 & X  PC$ wine WinKawaks.exe
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cfdc
fixme:iphlpapi:NotifyAddrChange (Handle 0x61de8d8, overlapped 0x61de8e0): stub
wine: configuration in '/home/zazzy/.wine' has been updated.

What does that mean lol, no window opened up btw

---

### Post by GreezyFreezy on 2010-08-12
> **Vaphell said:**
> [http://appdb.winehq.org/](http://appdb.winehq.org/)

look if your apps are mentioned there and if they work

Well what im really tryna run, if nothing else works, was the emulator so i can play some old school retro games, and its not on the list obviously becuase the list is all like commercial games

---

### Post by Vaphell on 2010-08-12
emulator of which platform? dos? some oldschool consoles?

---

### Post by Vaphell on 2010-08-12
try to find native linux emulators first because running a windows binary to emulate a console is pretty hardcore :)

maybe this will help
[http://ubuntuforums.org/showthread.php?t=595124](http://ubuntuforums.org/showthread.php?t=595124)
people mention mednafen which is in the repo, you can check it out

---

### Post by GreezyFreezy on 2010-08-12
> **Vaphell said:**
> emulator of which platform? dos? some oldschool consoles?

yep, neogeo :P

---

### Post by GreezyFreezy on 2010-08-12
> **Vaphell said:**
> try to find native linux emulators first because running a windows binary to emulate a console is pretty hardcore :)

maybe this will help
[http://ubuntuforums.org/showthread.php?t=595124](http://ubuntuforums.org/showthread.php?t=595124)
people mention mednafen which is in the repo, you can check it out

I saw that thread earlier, and didnt even understand which emulator to use and how to use it =/ im used to the good ol neoragex

---

### Post by GreezyFreezy on 2010-08-12
> **Vaphell said:**
> try to find native linux emulators first because running a windows binary to emulate a console is pretty hardcore :)

maybe this will help
[http://ubuntuforums.org/showthread.php?t=595124](http://ubuntuforums.org/showthread.php?t=595124)
people mention mednafen which is in the repo, you can check it out

Ok im on [http://mednafen.sourceforge.net/releases/](http://mednafen.sourceforge.net/releases/)
how exactly do i get it? the apt-get command didnt do anything
and when i clicked "here" in the download here, there were a billion links but iunno which one to pick

EDIT: tried putting sudo apt-get instead of apt-get, i think it installed but i dont know how to access it

---

### Post by Vaphell on 2010-08-12
well, you always need to sudo to install stuff from an ordinary user account because you need to be allowed to write in system directories (unless you know how to disable it ;-)).
either way i think you run it from terminal, most probably **mednafen**

i guess it will be handy
[http://mednafen.sourceforge.net/documentation/#intro](http://mednafen.sourceforge.net/documentation/#intro)

---

### Post by GreezyFreezy on 2010-08-12
> **Vaphell said:**
> well, you always need to sudo to install stuff from an ordinary user account because you need to be allowed to write in system directories (unless you know how to disable it ;-)).
either way i think you run it from terminal, most probably **mednafen**

i guess it will be handy
[http://mednafen.sourceforge.net/documentation/#intro](http://mednafen.sourceforge.net/documentation/#intro)

zazzy@Zooz-Top:~$ mednafen
Starting Mednafen 0.8.C
 Loading settings from "/home/zazzy/.mednafen/mednafen.cfg"...
 Compiled against SDL 1.2.14, running with SDL 1.2.14

No command-line arguments specified.

Usage: mednafen [OPTION]... [FILE]
	Please refer to the documentation for option parameters and usage.

What do i do to go into the actual emulator, which is a GUI (i hope)

---

### Post by Zorgoth on 2010-08-12
Whenever your stuck with a command and it gives you a message like that, try "<command> --help" for a quick list of switches or man <command> for a detailed help file.

So for example, if you wanted to know how to list all the files, hidden or non-hidden, in a directory, except . and .., and you knew "ls" was the command for listing a directory (which by default does not list hidden files/folders), you could type "ls --help" and obtain the following:

```

someone@someonescomputer:~$ ls --help
Usage: ls [OPTION]... [FILE]...
List information about the FILEs (the current directory by default).
Sort entries alphabetically if none of -cftuvSUX nor --sort.

Mandatory arguments to long options are mandatory for short options too.
  -a, --all                  do not ignore entries starting with .
  -A, --almost-all           do not list implied . and ..
      --author               with -l, print the author of each file
  -b, --escape               print octal escapes for nongraphic characters
      --block-size=SIZE      use SIZE-byte blocks
  -B, --ignore-backups       do not list implied entries ending with ~
  -c                         with -lt: sort by, and show, ctime (time of last
                               modification of file status information)
                               with -l: show ctime and sort by name
                               otherwise: sort by ctime
  -C                         list entries by columns
      --color[=WHEN]         control whether color is used to distinguish file
                               types.  WHEN may be `never', `always', or `auto'
  -d, --directory            list directory entries instead of contents,
                               and do not dereference symbolic links
  -D, --dired                generate output designed for Emacs' dired mode
  -f                         do not sort, enable -aU, disable -ls --color
  -F, --classify             append indicator (one of */=>@|) to entries
      --file-type            likewise, except do not append `*'
      --format=WORD          across -x, commas -m, horizontal -x, long -l,
                               single-column -1, verbose -l, vertical -C
      --full-time            like -l --time-style=full-iso
  -g                         like -l, but do not list owner
      --group-directories-first
                             group directories before files.
                               augment with a --sort option, but any
                               use of --sort=none (-U) disables grouping
  -G, --no-group             in a long listing, don't print group names
  -h, --human-readable       with -l, print sizes in human readable format
                               (e.g., 1K 234M 2G)
      --si                   likewise, but use powers of 1000 not 1024
  -H, --dereference-command-line
                             follow symbolic links listed on the command line
      --dereference-command-line-symlink-to-dir
                             follow each command line symbolic link
                             that points to a directory
      --hide=PATTERN         do not list implied entries matching shell PATTERN
                               (overridden by -a or -A)
      --indicator-style=WORD  append indicator with style WORD to entry names:
                               none (default), slash (-p),
                               file-type (--file-type), classify (-F)
  -i, --inode                print the index number of each file
  -I, --ignore=PATTERN       do not list implied entries matching shell PATTERN
  -k                         like --block-size=1K
  -l                         use a long listing format
  -L, --dereference          when showing file information for a symbolic
                               link, show information for the file the link
                               references rather than for the link itself
  -m                         fill width with a comma separated list of entries
  -n, --numeric-uid-gid      like -l, but list numeric user and group IDs
  -N, --literal              print raw entry names (don't treat e.g. control
                               characters specially)
  -o                         like -l, but do not list group information
  -p, --indicator-style=slash
                             append / indicator to directories
  -q, --hide-control-chars   print ? instead of non graphic characters
      --show-control-chars   show non graphic characters as-is (default
                             unless program is `ls' and output is a terminal)
  -Q, --quote-name           enclose entry names in double quotes
      --quoting-style=WORD   use quoting style WORD for entry names:
                               literal, locale, shell, shell-always, c, escape
  -r, --reverse              reverse order while sorting
  -R, --recursive            list subdirectories recursively
  -s, --size                 print the allocated size of each file, in blocks
  -S                         sort by file size
      --sort=WORD            sort by WORD instead of name: none -U,
                             extension -X, size -S, time -t, version -v
      --time=WORD            with -l, show time as WORD instead of modification
                             time: atime -u, access -u, use -u, ctime -c,
                             or status -c; use specified time as sort key
                             if --sort=time
      --time-style=STYLE     with -l, show times using style STYLE:
                             full-iso, long-iso, iso, locale, +FORMAT.
                             FORMAT is interpreted like `date'; if FORMAT is
                             FORMAT1<newline>FORMAT2, FORMAT1 applies to
                             non-recent files and FORMAT2 to recent files;
                             if STYLE is prefixed with `posix-', STYLE
                             takes effect only outside the POSIX locale
  -t                         sort by modification time
  -T, --tabsize=COLS         assume tab stops at each COLS instead of 8
  -u                         with -lt: sort by, and show, access time
                               with -l: show access time and sort by name
                               otherwise: sort by access time
  -U                         do not sort; list entries in directory order
  -v                         natural sort of (version) numbers within text
  -w, --width=COLS           assume screen width instead of current value
  -x                         list entries by lines instead of by columns
  -X                         sort alphabetically by entry extension
  -Z, --context              print any SELinux security context of each file
  -1                         list one file per line
      --help     display this help and exit
      --version  output version information and exit

SIZE may be (or may be an integer optionally followed by) one of following:
kB 1000, K 1024, MB 1000*1000, M 1024*1024, and so on for G, T, P, E, Z, Y.

By default, color is not used to distinguish types of files.  That is
equivalent to using --color=none.  Using the --color option without the
optional WHEN argument is equivalent to using --color=always.  With
--color=auto, color codes are output only if standard output is connected
to a terminal (tty).  The environment variable LS_COLORS can influence the
colors, and can be set easily by the dircolors command.

Exit status:
 0  if OK,
 1  if minor problems (e.g., cannot access subdirectory),
 2  if serious trouble (e.g., cannot access command-line argument).

Report ls bugs to bug-coreutils@gnu.org
GNU coreutils home page: <http://www.gnu.org/software/coreutils/>
General help using GNU software: <http://www.gnu.org/gethelp/>
Report ls translation bugs to <http://translationproject.org/team/>

```

The second item on the list is "ls -A," which does what we want.

If you wanted more detail on how each switch works (switches are things like -a, -A, -t, --help, etc.), you could refer to man ls.

---

### Post by GreezyFreezy on 2010-08-16
How exactly would i run this neo geo emulator tho? When i put the command in nothing happens =/

---

