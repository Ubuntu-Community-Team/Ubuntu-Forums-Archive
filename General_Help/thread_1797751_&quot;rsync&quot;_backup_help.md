---
title: "&quot;rsync&quot; backup help"
date: 2011-07-05
forum: General Help
---

### Post by qsczse25 on 2011-07-05
Hello,

I'm setting up a home file/backup server and would like to use the "rsync" tool from clients to back them up.

My goals:
[LIST]
[*]I want each client to define in its local configuration file very specific directories to sync.
[*]Each directory specified in the file should sync recursively.
[*]The directories may be located anywhere on the computer.
[/LIST]

I read rsync's man page and tried different combinations of the --include-from= and of course searched the internet, but without any success.

These are the rsync options I'm using (minus the ones related to filters and paths which I was unsuccessful with):
```
rsync -vaur
```
The remote backup part is covered quite well and is unrelated, so any examples provided could use local directories for the destination.

Thank you!

---

### Post by seawolf167 on 2011-07-05
If you use the

```
--list-from=FILE
```

option you have to specify the exact files you want to be rsync'd. So you'll have to create your list first each time, maybe from an

```
ls -r
```

or

```
ls -rd
```

Else, your command should work

```
rsync -ruva --delete-before /source /destination
```

You can read more from

```
[man rsync]("http://linux.die.net/man/1/rsync")
```

and the Ubuntu [rsync page]("https://help.ubuntu.com/community/rsync").

---

### Post by qsczse25 on 2011-07-05
Thank you for your replay,

About the "--list-from=FILE", I would not like to sync individual files, but individual directories (recursively). Should that work with "--list-from=FILE"? Because I was unsuccessful.

I suppose that I could issue a separate `rsync` command for each directory, but a configuration file would make much more sense...
I would appreciate it if someone elaborated on how to do this, because (re)reading the rsync man page and trying myself didn't work so far.

Thanks in advance.

---

### Post by seawolf167 on 2011-07-05
When you create your list file, include trailing slashes on the directories you want to transfer, else it will be treated as a file

example list

```
#transfer-list
/path/to/file1
/path/to/file2
/path/to/directory1/
/path/to/directory2/
```example command

```
rsync -ruva --delete-before --files-from=/path/to/transfer-list /destination
```see if that works

---

