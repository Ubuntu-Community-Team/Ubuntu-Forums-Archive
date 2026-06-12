---
title: "Debian Package Install Problem"
date: 2009-10-21
forum: General Help
---

### Post by carolina on 2009-10-21
I just installed Ubuntu 9.04 and received the following message when trying to install a debian pkg from Synaptic .

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

However , when i try to run manually in terminal i get this message :

alan@alan-desktop:~$  'sudo dpkg --configure -a' 
bash: sudo dpkg --configure -a: command not found

Any help appreciated

---

### Post by scragar on 2009-10-21
Don't use the quotes around it.

---

### Post by DeMus on 2009-10-21
> **carolina said:**
> I just installed Ubuntu 9.04 and received the following message when trying to install a debian pkg from Synaptic .

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

However , when i try to run manually in terminal i get this message :

alan@alan-desktop:~$  'sudo dpkg --configure -a' 
bash: sudo dpkg --configure -a: command not found

Any help appreciated

Did you type the command using the quotes? You should not do that.
Try it again, this time without them.

---

### Post by carolina on 2009-10-21
Thanks for the tip ... that did move the terminal forward , but now i am even more confused  following this message:

dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
alan@alan-desktop:~$ dpkg --help for help about installing and deinstalling packages 
[*];
Usage: dpkg [<option> ...] <command>

Commands:
  -i|--install       <.deb file name> ... | -R|--recursive <directory> ...
  --unpack           <.deb file name> ... | -R|--recursive <directory> ...
  -A|--record-avail  <.deb file name> ... | -R|--recursive <directory> ...
  --configure        <package> ... | -a|--pending
  --triggers-only    <package> ... | -a|--pending
  -r|--remove        <package> ... | -a|--pending
  -P|--purge         <package> ... | -a|--pending
  --get-selections [<pattern> ...] Get list of selections to stdout.
  --set-selections                 Set package selections from stdin.
  --clear-selections               Deselect every non-essential package.
  --update-avail <Packages-file>   Replace available packages info.
  --merge-avail <Packages-file>    Merge with info from file.
  --clear-avail                    Erase existing available info.
  --forget-old-unavail             Forget uninstalled unavailable pkgs.
  -s|--status <package> ...        Display package status details.
  -p|--print-avail <package> ...   Display available version details.
  -L|--listfiles <package> ...     List files `owned' by package(s).
  -l|--list [<pattern> ...]        List packages concisely.
  -S|--search <pattern> ...        Find package(s) owning file(s).
  -C|--audit                       Check for broken package(s).
  --print-architecture             Print dpkg architecture.
  --compare-versions <a> <op> <b>  Compare version numbers - see below.
  --force-help                     Show help on forcing.
  -Dh|--debug=help                 Show help on debugging.

  -h|--help                        Show this help message.
  --version                        Show the version.
  --license|--licence              Show the copyright licensing terms.

Use dpkg -b|--build|-c|--contents|-e|--control|-I|--info|-f|--field|
 -x|--extract|-X|--vextract|--fsys-tarfile  on archives (type dpkg-deb --help).

For internal use: dpkg --assert-support-predepends | --predep-package |
  --assert-working-epoch | --assert-long-filenames | --assert-multi-conrep.

Options:
  --admindir=<directory>     Use <directory> instead of /var/lib/dpkg.
  --root=<directory>         Install on a different root directory.
  --instdir=<directory>      Change installation dir without changing admin dir.
  -O|--selected-only         Skip packages not selected for install/upgrade.
  -E|--skip-same-version     Skip packages whose same version is installed.
  -G|--refuse-downgrade      Skip packages with earlier version than installed.
  -B|--auto-deconfigure      Install even if it would break some other package.
  --[no-]triggers            Skip or force consequential trigger processing.
  --no-debsig                Do not try to verify package signatures.
  --no-act|--dry-run|--simulate
                             Just say what we would do - don't do it.
  -D|--debug=<octal>         Enable debugging (see -Dhelp or --debug=help).
  --status-fd <n>            Send status change updates to file descriptor <n>.
  --log=<filename>           Log status changes and actions to <filename>.
  --ignore-depends=<package>,...
                             Ignore dependencies involving <package>.
  --force-...                Override problems (see --force-help).
  --no-force-...|--refuse-...
                             Stop when problems encountered.
  --abort-after <n>          Abort after encountering <n> errors.

Comparison operators for --compare-versions are:
  lt le eq ne ge gt       (treat empty version as earlier than any version);
  lt-nl le-nl ge-nl gt-nl (treat empty version as later than any version);
  < << <= = >= >> >       (only for compatibility with control file syntax).

Use `dselect' or `aptitude' for user-friendly package management.

At this point i would just like to get rid of the aborted install as i can't use Synaptic ..

---

### Post by MelDJ on 2009-10-21
just type: sudo dpkg --configure -a

---

### Post by carolina on 2009-10-21
MelDJ

ok , i did that and get :

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

I have no idea which of the above commands i should initiate . At this point i would be happy to just free up the Synaptic app so i ran dselect ... and was told it was "not currently installed"... so i ran the command to install dselect... and go right back to the initial message ... dpkg was interrupted , you must manually run sudo dpkg--configure a  , to correct the problem .

After running this last command i am given this message :

dpkg: error processing a (--configure):
 no package named `a' is installed, cannot configure
Errors were encountered while processing:
 a
alan@alan-desktop:~$ sudo dpkg--configure-a
sudo: dpkg--configure-a: command not found

I will say that i have never encountered this kind of issue previously running 8.10 and am starting to wonder if 9.04 is not appropriate for us more "challenged" computer users .  :-)

Any further advice appreciated as i am thinking "just go back back to what worked previously"..  :-)

---

### Post by carolina on 2009-10-21
> **carolina said:**
> MelDJ

ok , i did that and get :

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

I have no idea which of the above commands i should initiate . At this point i would be happy to just free up the Synaptic app so i ran dselect ... and was told it was "not currently installed"... so i ran the command to install dselect... and go right back to the initial message ... dpkg was interrupted , you must manually run sudo dpkg--configure a  , to correct the problem .

After running this last command i am given this message :

dpkg: error processing a (--configure):
 no package named `a' is installed, cannot configure
Errors were encountered while processing:
 a
alan@alan-desktop:~$ sudo dpkg--configure-a
sudo: dpkg--configure-a: command not found

I will say that i have never encountered this kind of issue previously running 8.10 and am starting to wonder if 9.04 is not appropriate for us more "challenged" computer users .  :-)

Any further advice appreciated as i am thinking "just go back back to what worked previously"..  :-)


**Problem Solved**

Have no idea how or why but will move on to the next set of problems   :P

---

### Post by itsjareds on 2009-10-21
You just forgot to put a space:
```
sudo dpkg --configure -a
```

The space between --configure and -a is important.

---

