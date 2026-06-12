---
title: "How do you remember the terminal commands?"
date: 2010-01-24
forum: General Help
---

### Post by fterh on 2010-01-24
Is there like a reference page somewhere?

For example the tar command, what is the -xvvf for when extracting tar files? I read [http://www.computerhope.com/unix/utar.htm](http://www.computerhope.com/unix/utar.htm) but still don't get it.

---

### Post by stinkeye on 2010-01-24
In terminal
```
man tar
```
man - an interface to the on-line reference manuals

---

### Post by llawwehttam on 2010-01-24
Personally I set up an alias file with all my most commonly used commands.

Have a look in the alias section of your ~/.bashrc . I always have a separate ~/.bash_aliases file with all my aliases in.

---

### Post by jasneet on 2010-01-24
Tar is a GNU archiving program

Many options can be used with tar depending on your requirement. The options are written after "-". For Example:-  "tar -xvf"

Here "x" means Extract i.e you want to extract the archive, "v" means Verbose i.e. verbosely list files processed during extraction and "f" means File i.e use archive file or device ARCHIVE.

I would suggest you use such commands in your day to day life and then you would be able to remember them :)

---

### Post by cbraxton on 2010-01-24
> **fterh said:**
> Is there like a reference page somewhere?

For example the tar command, what is the -xvvf for when extracting tar files? I read [http://www.computerhope.com/unix/utar.htm](http://www.computerhope.com/unix/utar.htm) but still don't get it.

Work with Unix systems for about 30 years and you'll remember many of the commands and basic options, a surprising number of which are still the same. :-)

If you want a synopsis of a command's usage and options, look at the relevant man page. For tar, you would type the command "man tar" to see this. This would tell you that "x" extracts from an archive, "v" is verbose ("vv" is more verbose), and "f" precedes the filename of the tar archive. 

You can also search the man pages for content via the "apropos" command. For example "apropos mail" would display a list of man pages in which the word "mail" appears.

---

### Post by garvinrick4 on 2010-01-24
> **fterh said:**
> Is there like a reference page somewhere?

For example the tar command, what is the -xvvf for when extracting tar files? I read [http://www.computerhope.com/unix/utar.htm](http://www.computerhope.com/unix/utar.htm) but still don't get it.

Tom boy notes for all and print out cheat sheets in open office of all I am learning until
I got them down pat because I have 3 OS'S going on. Tom boy notes is where I start.
I can think I will never forget but give me 2 1/2 minutes and I have forgotten. Sooner or
later it becomes second nature.

---

### Post by jmszr on 2010-01-24
fterh,

These may be of help:[http://fosswire.com/post/2007/8/unixlinux-command-cheat-sheet/](http://fosswire.com/post/2007/8/unixlinux-command-cheat-sheet/) and:[http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/)

---

### Post by blueshiftoverwatch on 2010-01-24
You can try [setting this]("http://img521.imageshack.us/img521/3738/linuxcliwallpaper.jpg") as your wallpaper.

---

### Post by mkvnmtr on 2010-01-24
I used Tomboy notes for a year or two but normally it is just cut and paste so I do not even try to remember.

---

### Post by fjf314 on 2010-01-24
> **fterh said:**
> Is there like a reference page somewhere?

For example the tar command, what is the -xvvf for when extracting tar files? I read [http://www.computerhope.com/unix/utar.htm](http://www.computerhope.com/unix/utar.htm) but still don't get it.

You become surprisingly familiar with them after you use them for awhile. When I first started with Unix-like operating systems, I mainly just relied on the man pages and Google for whatever I needed. After a few months, though, you tend to remember the commands you use with at least occasional frequency.

---

### Post by mcduck on 2010-01-24
Mostly you learn the commands simply by using them. :)

But if you need to find what command to use for some task, use "**apropos**". It will tell you.

For example:
```
$ apropos zip
bunzip2 (1)    - a block-sorting file compressor, v1.0.4
bzcmp (1)      - xompare bzip2-compressed files
gunzip (1)     -  compress or expand files
unzip (1)      - list, test and extract compressed files in ZIP archives
.
.
.
```
After that you can check the tools that seem suitable for your purposes with the "**man**" and "**info**" commands.

---

### Post by houseworkshy on 2010-01-24
When in the terminal doing something I don't know by heart I often open another by its side so I can use the various helps at the same time.  Entering "info info" and "man man" is a good start when learning the terminal.  As mentioned above by blueshiftoverwatch, makeing wallpapers out of cheatsheets is very handy.  Once made one can simply set whichever is relevant to whatever one is using.  At the end of this page are links to several useful sources of cheatsheets;  [http://www.debian.org/doc/](http://www.debian.org/doc/)
As this is so useful I wonder if anyone knows how to make a click through-able over laid tranceparancy.  It'd be a nice help feature as one could then use the program below while a ghostly cheat sheet hovered above.

---

### Post by bluelamp999 on 2010-01-24
> **blueshiftoverwatch said:**
> You can try [[COLOR="Red"]setting this[/COLOR]]("http://img521.imageshack.us/img521/3738/linuxcliwallpaper.jpg") as your wallpaper.

Brilliant!

---

### Post by fterh on 2010-01-25
> **jasneet said:**
> Tar is a GNU archiving program

Many options can be used with tar depending on your requirement. The options are written after "-". For Example:-  "tar -xvf"

Here "x" means Extract i.e you want to extract the archive, "v" means Verbose i.e. verbosely list files processed during extraction and "f" means File i.e use archive file or device ARCHIVE.

I would suggest you use such commands in your day to day life and then you would be able to remember them :)
I know what v does... but what about "f"? Don't really understand... and why is there sometimes "-xvvf"... why the double v?

---

### Post by D3V11 on 2010-01-25
```

# 1: Uncompress tarball

To uncompress them, execute the following command(s) depending on the extension:
$ tar zxf file.tar.gz
$ tar zxf file.tgz
$ tar jxf file.tar.bz2
$ tar jxf file.tbz2

Now change directory
$ ls
$ cd path-to-software/
# 2: Build and install software

Generally you need to type 3 commands as follows for building and compiling software:
# ./configure
# make
# make install

Where,

    * ./configure will configure the software to ensure your system has the necessary functionality and libraries to successfully compile the package
    * make will compile all the source files into executable binaries.
    * Finally, make install will install the binaries and any supporting files into the appropriate locations.

```Most tar balls will come with an instruction/install.txt file. This may also come with a list of needed dependencies.

---

### Post by scouser73 on 2010-01-25
> **garvinrick4 said:**
> Tom boy notes for all and print out cheat sheets in open office of all I am learning until
I got them down pat because I have 3 OS'S going on. Tom boy notes is where I start.
I can think I will never forget but give me 2 1/2 minutes and I have forgotten. Sooner or
later it becomes second nature.

+1 for using Tomboy Notes

---

### Post by lotharmat on 2010-01-25
> **fterh said:**
> I know what v does... but what about "f"? Don't really understand... and why is there sometimes "-xvvf"... why the double v?


"f" is to tell it which "f"ile to extract from

---

### Post by D3V11 on 2010-01-25
V = verbose

---

### Post by ankspo71 on 2010-01-25
> **blueshiftoverwatch said:**
> You can try [setting this]("http://img521.imageshack.us/img521/3738/linuxcliwallpaper.jpg") as your wallpaper.

Hi, thanks for the link. 
I just requested something like this in another thread.  It's freaky how that happens :shock: (lol)

---

### Post by fterh on 2010-01-25
> **lotharmat said:**
> "f" is to tell it which "f"ile to extract from

for example:

```
tar -xvf something.tar
```

I'm not sure if it's correct syntax, but say it is, I've already specified the tar file to extract from, so why is the "f" needed?

---

### Post by lisati on 2010-01-25
Some commands have a "help" option. For example, ```
tar --help
``` gives:
```
Usage: tar [OPTION...] [FILE]...
GNU `tar' saves many files together into a single tape or disk archive, and can
restore individual files from the archive.

Examples:
  tar -cf archive.tar foo bar  # Create archive.tar from files foo and bar.
  tar -tvf archive.tar         # List all files in archive.tar verbosely.
  tar -xf archive.tar          # Extract all files from archive.tar.

 Main operation mode:

  -A, --catenate, --concatenate   append tar files to an archive
  -c, --create               create a new archive
  -d, --diff, --compare      find differences between archive and file system
      --delete               delete from the archive (not on mag tapes!)
  -r, --append               append files to the end of an archive
  -t, --list                 list the contents of an archive
      --test-label           test the archive volume label and exit
  -u, --update               only append files newer than copy in archive
  -x, --extract, --get       extract files from an archive

 Operation modifiers:

      --check-device         check device numbers when creating incremental
                             archives (default)
  -g, --listed-incremental=FILE   handle new GNU-format incremental backup
  -G, --incremental          handle old GNU-format incremental backup
      --ignore-failed-read   do not exit with nonzero on unreadable files
  -n, --seek                 archive is seekable
      --no-check-device      do not check device numbers when creating
                             incremental archives
      --occurrence[=NUMBER]  process only the NUMBERth occurrence of each file
                             in the archive; this option is valid only in
                             conjunction with one of the subcommands --delete,
                             --diff, --extract or --list and when a list of
                             files is given either on the command line or via
                             the -T option; NUMBER defaults to 1
      --sparse-version=MAJOR[.MINOR]
                             set version of the sparse format to use (implies
                             --sparse)
  -S, --sparse               handle sparse files efficiently

 Overwrite control:

  -k, --keep-old-files       don't replace existing files when extracting
      --keep-newer-files     don't replace existing files that are newer than
                             their archive copies
      --no-overwrite-dir     preserve metadata of existing directories
      --overwrite            overwrite existing files when extracting
      --overwrite-dir        overwrite metadata of existing directories when
                             extracting (default)
      --recursive-unlink     empty hierarchies prior to extracting directory
      --remove-files         remove files after adding them to the archive
  -U, --unlink-first         remove each file prior to extracting over it
  -W, --verify               attempt to verify the archive after writing it

 Select output stream:

      --ignore-command-error ignore exit codes of children
      --no-ignore-command-error   treat non-zero exit codes of children as
                             error
  -O, --to-stdout            extract files to standard output
      --to-command=COMMAND   pipe extracted files to another program

 Handling of file attributes:

      --atime-preserve[=METHOD]   preserve access times on dumped files, either
                             by restoring the times after reading
                             (METHOD='replace'; default) or by not setting the
                             times in the first place (METHOD='system')
      --delay-directory-restore   delay setting modification times and
                             permissions of extracted directories until the end
                             of extraction
      --group=NAME           force NAME as group for added files
      --mode=CHANGES         force (symbolic) mode CHANGES for added files
      --mtime=DATE-OR-FILE   set mtime for added files from DATE-OR-FILE
  -m, --touch                don't extract file modified time
      --no-delay-directory-restore
                             cancel the effect of --delay-directory-restore
                             option
      --no-same-owner        extract files as yourself
      --no-same-permissions  apply the user's umask when extracting permissions
                             from the archive (default for ordinary users)
      --numeric-owner        always use numbers for user/group names
      --owner=NAME           force NAME as owner for added files
  -p, --preserve-permissions, --same-permissions
                             extract information about file permissions
                             (default for superuser)
      --preserve             same as both -p and -s
      --same-owner           try extracting files with the same ownership
  -s, --preserve-order, --same-order
                             sort names to extract to match archive

 Device selection and switching:

  -f, --file=ARCHIVE         use archive file or device ARCHIVE
      --force-local          archive file is local even if it has a colon
  -F, --info-script=NAME, --new-volume-script=NAME
                             run script at end of each tape (implies -M)
  -L, --tape-length=NUMBER   change tape after writing NUMBER x 1024 bytes
  -M, --multi-volume         create/list/extract multi-volume archive
      --rmt-command=COMMAND  use given rmt COMMAND instead of rmt
      --rsh-command=COMMAND  use remote COMMAND instead of rsh
      --volno-file=FILE      use/update the volume number in FILE

 Device blocking:

  -b, --blocking-factor=BLOCKS   BLOCKS x 512 bytes per record
  -B, --read-full-records    reblock as we read (for 4.2BSD pipes)
  -i, --ignore-zeros         ignore zeroed blocks in archive (means EOF)
      --record-size=NUMBER   NUMBER of bytes per record, multiple of 512

 Archive format selection:

  -H, --format=FORMAT        create archive of the given format

 FORMAT is one of the following:

    gnu                      GNU tar 1.13.x format
    oldgnu                   GNU format as per tar <= 1.12
    pax                      POSIX 1003.1-2001 (pax) format
    posix                    same as pax
    ustar                    POSIX 1003.1-1988 (ustar) format
    v7                       old V7 tar format

      --old-archive, --portability
                             same as --format=v7
      --pax-option=keyword[[:]=value][,keyword[[:]=value]]...
                             control pax keywords
      --posix                same as --format=posix
  -V, --label=TEXT           create archive with volume name TEXT; at
                             list/extract time, use TEXT as a globbing pattern
                             for volume name

 Compression options:

  -a, --auto-compress        use archive suffix to determine the compression
                             program
  -j, --bzip2                filter the archive through bzip2
      --lzma                 filter the archive through lzma
      --use-compress-program=PROG
                             filter through PROG (must accept -d)
  -z, --gzip, --gunzip, --ungzip   filter the archive through gzip
  -Z, --compress, --uncompress   filter the archive through compress

 Local file selection:

      --add-file=FILE        add given FILE to the archive (useful if its name
                             starts with a dash)
      --backup[=CONTROL]     backup before removal, choose version CONTROL
  -C, --directory=DIR        change to directory DIR
      --exclude=PATTERN      exclude files, given as a PATTERN
      --exclude-caches       exclude contents of directories containing
                             CACHEDIR.TAG, except for the tag file itself
      --exclude-caches-all   exclude directories containing CACHEDIR.TAG
      --exclude-caches-under exclude everything under directories containing
                             CACHEDIR.TAG
      --exclude-tag=FILE     exclude contents of directories containing FILE,
                             except for FILE itself
      --exclude-tag-all=FILE exclude directories containing FILE
      --exclude-tag-under=FILE   exclude everything under directories
                             containing FILE
      --exclude-vcs          exclude version control system directories
  -h, --dereference          follow symlinks; archive and dump the files they
                             point to
      --hard-dereference     follow hard links; archive and dump the files they
                             refer to
  -K, --starting-file=MEMBER-NAME
                             begin at member MEMBER-NAME in the archive
      --newer-mtime=DATE     compare date and time when data changed only
      --no-recursion         avoid descending automatically in directories
      --no-unquote           do not unquote filenames read with -T
      --null                 -T reads null-terminated names, disable -C
  -N, --newer=DATE-OR-FILE, --after-date=DATE-OR-FILE
                             only store files newer than DATE-OR-FILE
      --one-file-system      stay in local file system when creating archive
  -P, --absolute-names       don't strip leading `/'s from file names
      --recursion            recurse into directories (default)
      --suffix=STRING        backup before removal, override usual suffix ('~'
                             unless overridden by environment variable
                             SIMPLE_BACKUP_SUFFIX)
  -T, --files-from=FILE      get names to extract or create from FILE
      --unquote              unquote filenames read with -T (default)
  -X, --exclude-from=FILE    exclude patterns listed in FILE

 File name transformations:

      --strip-components=NUMBER   strip NUMBER leading components from file
                             names on extraction
      --transform=EXPRESSION use sed replace EXPRESSION to transform file
                             names

 File name matching options (affect both exclude and include patterns):

      --anchored             patterns match file name start
      --ignore-case          ignore case
      --no-anchored          patterns match after any `/' (default for
                             exclusion)
      --no-ignore-case       case sensitive matching (default)
      --no-wildcards         verbatim string matching
      --no-wildcards-match-slash   wildcards do not match `/'
      --wildcards            use wildcards (default for exclusion)
      --wildcards-match-slash   wildcards match `/' (default for exclusion)

 Informative output:

      --checkpoint[=NUMBER]  display progress messages every NUMBERth record
                             (default 10)
      --checkpoint-action=ACTION   execute ACTION on each checkpoint
      --index-file=FILE      send verbose output to FILE
  -l, --check-links          print a message if not all links are dumped
      --no-quote-chars=STRING   disable quoting for characters from STRING
      --quote-chars=STRING   additionally quote characters from STRING
      --quoting-style=STYLE  set name quoting style; see below for valid STYLE
                             values
  -R, --block-number         show block number within archive with each
                             message
      --show-defaults        show tar defaults
      --show-omitted-dirs    when listing or extracting, list each directory
                             that does not match search criteria
      --show-transformed-names, --show-stored-names
                             show file or archive names after transformation
      --totals[=SIGNAL]      print total bytes after processing the archive;
                             with an argument - print total bytes when this
                             SIGNAL is delivered; Allowed signals are: SIGHUP,
                             SIGQUIT, SIGINT, SIGUSR1 and SIGUSR2; the names
                             without SIG prefix are also accepted
      --utc                  print file modification dates in UTC
  -v, --verbose              verbosely list files processed
  -w, --interactive, --confirmation
                             ask for confirmation for every action

 Compatibility options:

  -o                         when creating, same as --old-archive; when
                             extracting, same as --no-same-owner

 Other options:

  -?, --help                 give this help list
      --restrict             disable use of some potentially harmful options
      --usage                give a short usage message
      --version              print program version

Mandatory or optional arguments to long options are also mandatory or optional
for any corresponding short options.

The backup suffix is `~', unless set with --suffix or SIMPLE_BACKUP_SUFFIX.
The version control may be set with --backup or VERSION_CONTROL, values are:

  none, off       never make backups
  t, numbered     make numbered backups
  nil, existing   numbered if numbered backups exist, simple otherwise
  never, simple   always make simple backups

Valid arguments for --quoting-style options are:

  literal
  shell
  shell-always
  c
  c-maybe
  escape
  locale
  clocale

*This* tar defaults to:
--format=gnu -f- -b20 --quoting-style=escape --rmt-command=/usr/sbin/rmt
--rsh-command=/usr/bin/rsh

Report bugs to <bug-tar@gnu.org>.

```

---

### Post by fterh on 2010-01-25
I tried extracting a tar.bz2 file using

```
tar xf file.tar.bz2
```

instead of "xjf" and it works. Is that supposed to work?

---

### Post by Lars Noodén on 2010-01-25
> **fterh said:**
>  How do you remember the terminal commands?  

Two tips:

Think of it as programming, shell script programing to be specific.

Learn to use the reference material available, especially the man pages, as you would any other programming or scripting language.

---

### Post by stinkeye on 2010-01-25
> **fterh said:**
> I tried extracting a tar.bz2 file using

```
tar xf file.tar.bz2
```

instead of "xjf" and it works. Is that supposed to work?


Unless you really need to use the command line, why not just use the right click "extract here" option?

---

### Post by chewearn on 2010-01-25
> **fterh said:**
> for example:

```
tar -xvf something.tar
```I'm not sure if it's correct syntax, but say it is, I've already specified the tar file to extract from, so why is the "f" needed?

Because "tar" command goes back a few decades, when it was used for tape back-up (you know, those reels you see in building-sized mainframes). So, if you don't specify "f" option, it will look for a tape drive.

---

### Post by pricetech on 2010-01-25
> **lisati said:**
> Some commands have a "help" option.

I wondered how long it would take before someone mentioned the --help option.

By the way;  use q to close man when you're through reading.

---

### Post by hemimaniac on 2010-01-25
> **blueshiftoverwatch said:**
> You can try [setting this]("http://img521.imageshack.us/img521/3738/linuxcliwallpaper.jpg") as your wallpaper.


That is neat, maybe a future addition to stock system wallpaper for new linux users?

---

### Post by bodhi.zazen on 2010-01-25
> **fterh said:**
> Is there like a reference page somewhere?

For example the tar command, what is the -xvvf for when extracting tar files? I read [http://www.computerhope.com/unix/utar.htm](http://www.computerhope.com/unix/utar.htm) but still don't get it.

Most people learn by repetition. So the more you use bash, the easier it becomes.

Start with at tutorial of some kind, such as 

[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

and use the command line.

The suggestion to learn to read the man pages is key. It is intimidating at first, but once you can read the man pages it becomes much easier.

---

