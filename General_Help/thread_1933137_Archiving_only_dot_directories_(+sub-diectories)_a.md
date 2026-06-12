---
title: "Archiving only dot directories (+sub-diectories) and files in home directory"
date: 2012-02-28
forum: General Help
---

### Post by casbahdk on 2012-02-28
How do I backup dot directories, dot sub-directories and dot files residing in /home/user/ to an archive? Normally I would run something like the following, but that doesn't seem to work on hidden folders and files:```
tar -czvf pictures.tar.gz ~/Pictures
```I am using Xubuntu 11.04

---

### Post by papibe on 2012-02-28
Hi casbahdk.

Yes, if you use .* as an argument for tar, it will include . (that means all).

Try this:
```
find  -maxdepth 1 -type d -regex './\..*' -print0 | xargs -0 tar -czvf myhidden.tar.bz

```
Explanation:
- Use 'find' to get the list of the .* directories.
- the option -maxdepth 1 means just the directories directly located at home.
- option -type d looks for directory names only.
- regex is used to skip ./ and ../
- the option -print0 is just in case there are tricky characters in the directory names (like spaces).
- xargs take the list created by 'find' and it passes it to the command tar.

Hope it helps, and tell us how it goes.
Regards.

---

### Post by TeoBigusGeekus on 2012-02-28
If you only want to tar dot files, you could use something like this:
```
tar -cvzf archive.tar.gz ./.[^.]*
```

---

### Post by casbahdk on 2012-02-28
Thanks for the quick reply. Well this bit partially works:```
$ find  -maxdepth 1 -type d -regex './\..*' > test.txt
```I can create a test file with a list of the hidden directories, but it doesn't include the hidden files at the top level, like .bashrc and .pinerc The entire command, when used together gives me the following:```
$ find  -maxdepth 1 -type d -regex './\..*' -print0 | xargs -0 tar -czvf hidden_bits.tar.gz
tar: Cowardly refusing to create an empty archive
Try `tar --help' or `tar --usage' for more information.
```

---

### Post by casbahdk on 2012-02-28
> **TeoBigusGeekus said:**
> If you only want to tar dot files, you could use something like this:
```
tar -cvzf archive.tar.gz ./.[^.]*
```
I get the following errors:```
$ tar -cvzf hidden_files.tar.gz ./.[^.]*
tar: ./.[^.]*: Cannot stat: No such file or directory
tar: Exiting with failure status due to previous errors
```Could this be due to my working from the destination directory?

---

### Post by TeoBigusGeekus on 2012-02-28
Are you sure sure there are hidden files and/or folders where you run the command?

---

### Post by casbahdk on 2012-02-28
> **TeoBigusGeekus said:**
> Are you sure sure there are hidden files and/or folders where you run the command?
Kalispera, I am running this from the destination folder. Should I try running it from home like this:```
$ tar -cvzf archive.tar.gz ./.[^.]* /media/cbb/newest_backup_files/home_folders_files
```?

---

### Post by TeoBigusGeekus on 2012-02-28
cd to the folder where the dot files are and run the command.
It works for me...

---

### Post by papibe on 2012-02-28
> **casbahdk said:**
> it doesn't include the hidden files at the top level
Yes, the option '-type d' do exactly that (my mistake from reading just the beginning from your post title).

Just remove it and 'find' will add the files to the list.

> **casbahdk said:**
> ```
$ find  -maxdepth 1 -type d -regex './\..*' -print0 | xargs -0 tar -czvf hidden_bits.tar.gz
tar: Cowardly refusing to create an empty archive
Try `tar --help' or `tar --usage' for more information.
```
In this instance it looks like the second time you are running the command in a place with no hidden directories.

Hope it helps.
Regards.

---

### Post by casbahdk on 2012-02-28
> **TeoBigusGeekus said:**
> cd to the folder where the dot files are and run the command.
It works for me...
Yes, it worked here as well. I had to restart when I discovered I hadn't emptied the trash. No point in backing up things I don't want :) Efharistó.

---

### Post by Khayyam on 2012-02-28
I would generally want all the files contained in the tarball to be in a directory, and for that reason would use tar from /home ...

```
% cd /home
% tar cjf /path/to/backup/archive-$(date +%F).tar.bz2 username
```[FONT=sans-serif]
The point to keep in mind with tar is that it is an archive of the target path, so /home/username will contain a 'deeper' directory structure than "." .. this can have repercusions if/when you untar the archive.

There are many way to read the content of the archive, 'tar ztvf archive.tar.gz', or using less (with lesspipe.sh) but people often overwrite files and/or end up with files strewn in unwated places (hence the '-w' switch).

Also useful ... send the data directly to another machine (tar over ssh)

```
tar cjf - username | ssh user@host.tld "cat > /path/to/archive-$(date +%F).tar.bz2"
```I find rsync much more flexable for this sort of thing and so rarely make backups of this sort.

HTH ... khay




[/FONT]

---

