---
title: "Installing Sunbird"
date: 2012-10-13
forum: General Help
---

### Post by jediknight36 on 2012-10-13
Referencing [http://ubuntuforums.org/showthread.php?t=278206](http://ubuntuforums.org/showthread.php?t=278206)

I downloaded Sunbird via the website, but I cant get access to /opt. Can someone help me figure this out?

---

### Post by jediknight36 on 2012-10-13
I am trying to install an iCal like calender and found Sunbird. I want to install it but so far nothing is working. 

For reference, I found:
[http://ubuntuforums.org/showthread.php?t=278206](http://ubuntuforums.org/showthread.php?t=278206)

and then after that failed, I found:
[https://wiki.mozilla.org/Calendar:Installing_Sunbird](https://wiki.mozilla.org/Calendar:Installing_Sunbird)

So far, terminal is being difficult. 

jediknight36@Ubuntu-MacBookPro:~$ sudo bash
[sudo] password for jediknight36: 
Sorry, try again.
[sudo] password for jediknight36: 
^[[DSorry, try again.
[sudo] password for jediknight36: 
Sorry, try again.
sudo: 3 incorrect password attempts
jediknight36@Ubuntu-MacBookPro:~$ sudo bash
[sudo] password for jediknight36: 
Sorry, try again.
[sudo] password for jediknight36: 
root@Ubuntu-MacBookPro:~# cp /home/jediknight36/Desktop/sunbird-0.7.en-US.linux-i686.tar.gz /usr/lib
cp: cannot stat `/home/jediknight36/Desktop/sunbird-0.7.en-US.linux-i686.tar.gz': No such file or directory
root@Ubuntu-MacBookPro:~# cp /home/jediknight36/Desktop/sunbird-0.7.en-US.linux-i686.tar.gz /usr/lib
cp: cannot stat `/home/jediknight36/Desktop/sunbird-0.7.en-US.linux-i686.tar.gz': No such file or directory
root@Ubuntu-MacBookPro:~# cp /home/jediknight36/Desktop/sunbird-0.7.en-US.linux-i686.tar.gz /usr/lib
cp: cannot stat `/home/jediknight36/Desktop/sunbird-0.7.en-US.linux-i686.tar.gz': No such file or directory
root@Ubuntu-MacBookPro:~# cp /home/Desktop/sunbird-0.7.en-US.linux-i686.tar.gz /usr/lib
cp: cannot stat `/home/Desktop/sunbird-0.7.en-US.linux-i686.tar.gz': No such file or directory
root@Ubuntu-MacBookPro:~# cd /usr/lib
root@Ubuntu-MacBookPro:/usr/lib# tar -xvf sunbird-0.7.en-US.linux-i686.tar.gz
tar: sunbird-0.7.en-US.linux-i686.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
root@Ubuntu-MacBookPro:/usr/lib# sudo bash
root@Ubuntu-MacBookPro:/usr/lib# cp/home/jediknight36/Desktop
bash: cp/home/jediknight36/Desktop: No such file or directory
root@Ubuntu-MacBookPro:/usr/lib# cp /home/desktop
cp: missing destination file operand after `/home/desktop'
Try `cp --help' for more information.
root@Ubuntu-MacBookPro:/usr/lib# cp help
cp: missing destination file operand after `help'
Try `cp --help' for more information.
root@Ubuntu-MacBookPro:/usr/lib# cp --help
Usage: cp [OPTION]... [-T] SOURCE DEST
  or:  cp [OPTION]... SOURCE... DIRECTORY
  or:  cp [OPTION]... -t DIRECTORY SOURCE...
Copy SOURCE to DEST, or multiple SOURCE(s) to DIRECTORY.

Mandatory arguments to long options are mandatory for short options too.
  -a, --archive                same as -dR --preserve=all
      --attributes-only        don't copy the file data, just the attributes
      --backup[=CONTROL]       make a backup of each existing destination file
  -b                           like --backup but does not accept an argument
      --copy-contents          copy contents of special files when recursive
  -d                           same as --no-dereference --preserve=links
  -f, --force                  if an existing destination file cannot be
                                 opened, remove it and try again (redundant if
                                 the -n option is used)
  -i, --interactive            prompt before overwrite (overrides a previous -n
                                  option)
  -H                           follow command-line symbolic links in SOURCE
  -l, --link                   hard link files instead of copying
  -L, --dereference            always follow symbolic links in SOURCE
  -n, --no-clobber             do not overwrite an existing file (overrides
                                 a previous -i option)
  -P, --no-dereference         never follow symbolic links in SOURCE
  -p                           same as --preserve=mode,ownership,timestamps
      --preserve[=ATTR_LIST]   preserve the specified attributes (default:
                                 mode,ownership,timestamps), if possible
                                 additional attributes: context, links, xattr,
                                 all
      --no-preserve=ATTR_LIST  don't preserve the specified attributes
      --parents                use full source file name under DIRECTORY
  -R, -r, --recursive          copy directories recursively
      --reflink[=WHEN]         control clone/CoW copies. See below
      --remove-destination     remove each existing destination file before
                                 attempting to open it (contrast with --force)
      --sparse=WHEN            control creation of sparse files. See below
      --strip-trailing-slashes  remove any trailing slashes from each SOURCE
                                 argument
  -s, --symbolic-link          make symbolic links instead of copying
  -S, --suffix=SUFFIX          override the usual backup suffix
  -t, --target-directory=DIRECTORY  copy all SOURCE arguments into DIRECTORY
  -T, --no-target-directory    treat DEST as a normal file
  -u, --update                 copy only when the SOURCE file is newer
                                 than the destination file or when the
                                 destination file is missing
  -v, --verbose                explain what is being done
  -x, --one-file-system        stay on this file system
      --help     display this help and exit
      --version  output version information and exit

By default, sparse SOURCE files are detected by a crude heuristic and the
corresponding DEST file is made sparse as well.  That is the behavior
selected by --sparse=auto.  Specify --sparse=always to create a sparse DEST
file whenever the SOURCE file contains a long enough sequence of zero bytes.
Use --sparse=never to inhibit creation of sparse files.

When --reflink[=always] is specified, perform a lightweight copy, where the
data blocks are copied only when modified.  If this is not possible the copy
fails, or if --reflink=auto is specified, fall back to a standard copy.

The backup suffix is `~', unless set with --suffix or SIMPLE_BACKUP_SUFFIX.
The version control method may be selected via the --backup option or through
the VERSION_CONTROL environment variable.  Here are the values:

  none, off       never make backups (even if --backup is given)
  numbered, t     make numbered backups
  existing, nil   numbered if numbered backups exist, simple otherwise
  simple, never   always make simple backups

As a special case, cp makes a backup of SOURCE when the force and backup
options are given and SOURCE and DEST are the same name for an existing,
regular file.

Report cp bugs to [email]bug-coreutils@gnu.org[/email]
GNU coreutils home page: <http://www.gnu.org/software/coreutils/>
General help using GNU software: <http://www.gnu.org/gethelp/>
For complete documentation, run: info coreutils 'cp invocation'
root@Ubuntu-MacBookPro:/usr/lib# cp /home/jediknight36/Desktop/sunbird-0.7.en-US.linux-i686.tar.gz /usr/lib
cp: cannot stat `/home/jediknight36/Desktop/sunbird-0.7.en-US.linux-i686.tar.gz': No such file or directory
root@Ubuntu-MacBookPro:/usr/lib# cd /usr/libcp /home/jediknight36/Desktop/sunbird-1.0b1.tar.bz2 
bash: cd: /usr/libcp: No such file or directory
root@Ubuntu-MacBookPro:/usr/lib# cd /home/jediknight36
root@Ubuntu-MacBookPro:~# cp /home/jediknight36/Desktop/sunbird-1.0b1.tar.bz2
cp: missing destination file operand after `/home/jediknight36/Desktop/sunbird-1.0b1.tar.bz2'
Try `cp --help' for more information.
root@Ubuntu-MacBookPro:~# 

The file is sitting on the desktop and terminal cant find it. 
Location: /home/jediknight36/Desktop

Any help is appreciated.

---

### Post by Cheesemill on 2012-10-13
AKAIK Mozilla have stopped developing the standalone Sunbird application.

You can, however, get exactly the same functionality by using Thunderbird with the [Lightning]("https://addons.mozilla.org/en-US/thunderbird/addon/lightning/") plugin (it's also easier to install).

---

### Post by Frogs Hair on 2012-10-13
Sunbird is an old project and Mozilla recommends using Thunderbird Mail + Lightning which can be installed from Tools > Addons > Get Addons from within Thunderbird.   [https://addons.mozilla.org/en-US/thunderbird/addon/lightning/](https://addons.mozilla.org/en-US/thunderbird/addon/lightning/)

---

### Post by jediknight36 on 2012-10-13
> **Cheesemill said:**
> AKAIK Mozilla have stopped developing the standalone Sunbird application.

You can, however, get exactly the same functionality by using Thunderbird with the [Lightning]("https://addons.mozilla.org/en-US/thunderbird/addon/lightning/") plugin (it's also easier to install).

> **Frogs Hair said:**
> Sunbird is an old project and Mozilla recommends using Thunderbird Mail + Lightning which can be installed from Tools > Addons > Get Addons from within Thunderbird.   [https://addons.mozilla.org/en-US/thunderbird/addon/lightning/](https://addons.mozilla.org/en-US/thunderbird/addon/lightning/)

Hmm... I did install that plug-in, but Thunderbird isnt really wanting to work. I want to sync my iCloud and gmail calenders and I can barely browse my mail. The brightness of Thunderbird goes in and out and when I try to access the add-on, it locks up.

---

### Post by Frogs Hair on 2012-10-14
That doesn't read like a calendar problem. Post some information regarding Ubuntu, Thunderbird, and lightning version . Computer specs may also help. Evolution Mail & Calendar is also in the software center which will sync with Google.

---

