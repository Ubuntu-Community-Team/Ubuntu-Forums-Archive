---
title: "How do you delete folders?"
date: 2009-07-07
forum: General Help
---

### Post by Nubi505 on 2009-07-07
This is probably a super noob question. Earlier I asked how to get permission to extract into certain folders. Now I need to know how to delete certain folders. When I try to right click -> Move to Trash the option is greyed out. Cut is greyed out as well. I know there is a command that will let you delete anything you desire (as far as I know) but I don't know what that command is (rm?) or how to use it. How do I specify what I want to delete? Or is there a way to activate the Move to Trash option?

I'm trying to delete within the file system. But I'm not trying to delete anything critical to the system. I swear. 

As always,
Thank you!

---

### Post by K.Y.A on 2009-07-07
> **Nubi505 said:**
> This is probably a super noob question. Earlier I asked how to get permission to extract into certain folders. Now I need to know how to delete certain folders. When I try to right click -> Move to Trash the option is greyed out. Cut is greyed out as well. I know there is a command that will let you delete anything you desire (as far as I know) but I don't know what that command is (rm?) or how to use it. How do I specify what I want to delete? Or is there a way to activate the Move to Trash option?

I'm trying to delete within the file system. But I'm not trying to delete anything critical to the system. I swear. 

As always,
Thank you!

I know I will get an infraction for this...

If you wish to delete a file with the CLI, use this command:
```

sudo rm /home/username/FILE/FILE.txt
```

replace the last argument with the appropriate directory, USE AT OWN RISK!


To delete graphically, just launch the filebrowser as root. Press alt+F2, and type in:


```
gksudo nautilus
```


And no options will longer be greyed out, unless you chowned ~/God to 000, I did that once :)

---

### Post by wojox on 2009-07-07
Read about the terminal and sudo

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by anystupidname on 2009-07-07
man is your friend.

man rm:
> RM(1)                                                                  User Commands                                                                  RM(1)



NAME
       rm - remove files or directories

SYNOPSIS
       rm [OPTION]... FILE...

DESCRIPTION
       This manual page documents the GNU version of rm.  rm removes each specified file.  By default, it does not remove directories.

       If  the  -I  or --interactive=once option is given, and there are more than three files or the -r, -R, or --recursive are given, then rm prompts the
       user for whether to proceed with the entire operation.  If the response is not affirmative, the entire command is aborted.

       Otherwise, if a file is unwritable, standard input is a terminal, and the -f or --force option is not  given,  or  the  -i  or  --interactive=always
       option is given, rm prompts the user for whether to remove the file.  If the response is not affirmative, the file is skipped.

OPTIONS
       Remove (unlink) the FILE(s).

       -f, --force
              ignore nonexistent files, never prompt

       -i     prompt before every removal

       -I     prompt  once  before  removing  more  than  three files, or when removing recursively.  Less intrusive than -i, while still giving protection
              against most mistakes

       --interactive[=WHEN]
              prompt according to WHEN: never, once (-I), or always (-i).  Without WHEN, prompt always

       --one-file-system
              when removing a hierarchy recursively, skip any directory that is on a file system different from that  of  the  corresponding  command  line
              argument

       --no-preserve-root
              do not treat ‘/’ specially

       --preserve-root
              do not remove ‘/’ (default)

       -r, -R, --recursive
              remove directories and their contents recursively

       -v, --verbose
              explain what is being done

       --help display this help and exit

       --version
              output version information and exit

       By  default, rm does not remove directories.  Use the --recursive (-r or -R) option to remove each listed directory, too, along with all of its con&#8208;
       tents.

       To remove a file whose name starts with a ‘-’, for example ‘-foo’, use one of these commands:

              rm -- -foo

              rm ./-foo

       Note that if you use rm to remove a file, it is usually possible to recover the contents of that file.  If you want more assurance that the contents
       are truly unrecoverable, consider using shred.

AUTHOR
       Written by Paul Rubin, David MacKenzie, Richard Stallman, and Jim Meyering.

REPORTING BUGS
       Report bugs to <bug-coreutils@gnu.org>.

COPYRIGHT
       Copyright © 2008 Free Software Foundation, Inc.  License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
       This is free software: you are free to change and redistribute it.  There is NO WARRANTY, to the extent permitted by law.

SEE ALSO
       unlink(1), unlink(2), chattr(1), shred(1)

       The full documentation for rm is maintained as a Texinfo manual.  If the info and rm programs are properly installed at your site, the command

              info rm

       should give you access to the complete manual.



GNU coreutils 6.9.92.4-f088d-dirty                                      January 2008                                                                  RM(1)

man rmdir:
> RMDIR(1)                                                               User Commands                                                               RMDIR(1)



NAME
       rmdir - remove empty directories

SYNOPSIS
       rmdir [OPTION]... DIRECTORY...

DESCRIPTION
       Remove the DIRECTORY(ies), if they are empty.

       --ignore-fail-on-non-empty

              ignore each failure that is solely because a directory is non-empty

       -p, --parents
              Remove DIRECTORY and its ancestors.  E.g., ‘rmdir -p a/b/c’ is similar to ‘rmdir a/b/c a/b a’.

       -v, --verbose
              output a diagnostic for every directory processed

       --help display this help and exit

       --version
              output version information and exit

AUTHOR
       Written by David MacKenzie.

REPORTING BUGS
       Report bugs to <bug-coreutils@gnu.org>.

COPYRIGHT
       Copyright © 2008 Free Software Foundation, Inc.  License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
       This is free software: you are free to change and redistribute it.  There is NO WARRANTY, to the extent permitted by law.

SEE ALSO
       rmdir(2)

       The full documentation for rmdir is maintained as a Texinfo manual.  If the info and rmdir programs are properly installed at your site, the command

              info rmdir

       should give you access to the complete manual.



GNU coreutils 6.9.92.4-f088d-dirty                                      January 2008                                                               RMDIR(1)

---

### Post by Nubi505 on 2009-07-07
> I know I will get an infraction for this...

I hope not. That helped me out a bunch. I'll try not to abuse it. Thanks K.Y.A.

And I'll certainly read up on the sources provided to better understand what I'm doing. Thank you everyone.

---

