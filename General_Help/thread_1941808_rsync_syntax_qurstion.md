---
title: "rsync syntax qurstion"
date: 2012-03-16
forum: General Help
---

### Post by dheerajkabra on 2012-03-16
Hi.

I have a text file which contains the list of files and directories that I want to copy (one on a line). Now I want rsync to take this input from  my text file and sync it to the destination that I provide.

I've tried playing around with "--include-from=FILE" and "--from-file=FILE" options of rsync but it gives me syntax error no matter what I try.

Could someone provide me correct syntax for this use case.

Many thanks.
-Dheeraj.

---

### Post by sudodus on 2012-03-16
Reading from the man page, I think you should use
```
--files-from=FILE
``` instead of --from-file=FILE, when you have the files explicitly listed

>           --files-from=FILE       read list of source-file names from FILEI hope this helps :-)

Edit: more help added from [FONT=Courier New]man rsync[/FONT] to help showing the syntax
```

       --files-from=FILE
              Using this option allows you to specify the exact list of  files
              to  transfer  (as read from the specified FILE or - for standard
              input).  It also tweaks the default behavior of  rsync  to  make
              transferring just the specified files and directories easier:

              o      The  --relative  (-R)  option is implied, which preserves
                     the path information that is specified for each  item  in
                     the file (use --no-relative or --no-R if you want to turn
                     that off).

              o      The --dirs (-d) option  is  implied,  which  will  create
                     directories  specified  in  the  list  on the destination
                     rather than  noisily  skipping  them  (use  --no-dirs  or
                     --no-d if you want to turn that off).

              o      The  --archive  (-a)  option’s  behavior  does  not imply
                     --recursive (-r), so specify it explicitly, if  you  want
                     it.

              o      These  side-effects change the default state of rsync, so
                     the position of the --files-from option on  the  command-
                     line has no bearing on how other options are parsed (e.g.
                     -a works the same before or after --files-from,  as  does
                     --no-R and all other options).

              The  filenames  that  are read from the FILE are all relative to
              the source dir — any leading slashes are  removed  and  no  ".."
              references  are  allowed  to go higher than the source dir.  For
              example, take this command:

                [COLOR=Red] rsync -a --files-from=/tmp/foo /usr remote:/backup[/COLOR]

              If /tmp/foo contains the string  "bin"  (or  even  "/bin"),  the
              /usr/bin  directory will be created as /backup/bin on the remote
              host.  If it contains "bin/"  (note  the  trailing  slash),  the
              immediate  contents of the directory would also be sent (without
              needing to be explicitly mentioned in the file — this  began  in
              version  2.6.4).   In  both cases, if the -r option was enabled,
              that dir’s entire hierarchy would also be transferred  (keep  in
              mind that -r needs to be specified explicitly with --files-from,
              since it is not implied by -a).  Also note that  the  effect  of
              the  (enabled by default) --relative option is to duplicate only
              the path info that is read from the file — it does not force the
              duplication of the source-spec path (/usr in this case).

              In  addition,  the --files-from file can be read from the remote
              host instead of the local host if you specify a "host:" in front
              of the file (the host must match one end of the transfer).  As a
              short-cut, you can specify just a prefix of ":" to mean "use the
              remote end of the transfer".  For example:

                 rsync -a --files-from=:/path/file-list src:/ /tmp/copy

              This  would  copy all the files specified in the /path/file-list
              file that was located on the remote "src" host.

              If the --iconv and --protect-args options are specified and  the
              --files-from  filenames are being sent from one host to another,
              the filenames will be translated from the sending host’s charset
              to the receiving host’s charset.
```Maybe something like this would work:
```
rsync -a --files-from=/tmp/foo /usr remote:/backup
```

---

