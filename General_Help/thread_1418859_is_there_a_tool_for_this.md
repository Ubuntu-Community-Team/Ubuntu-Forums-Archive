---
title: "is there a tool for this?"
date: 2010-03-01
forum: General Help
---

### Post by Jive Turkey on 2010-03-01
I need to validate the integrity of a large number of files copied over network.  I could make a list of md5sums of the source directory and check the destination against the same list but there is probably a tool that does this or something comparable, possibly taking the two paths as arguments (I hope).

---

### Post by hemimaniac on 2010-03-01
I use cksfv for stuff like that, you can get it from [here]("http://ubuntuforums.org/wget%20http://freshmeat.net/urls/713e5297c438894930376f90420370af") ,

once installed simply cd into the source directory and cksfv * > nameofsfv.sfv  (* = everything in the directory)

then just send the .sfv to the new directory, cd into the new directory and simply cksfv -f nameofsfv.sfv

there is also a gui client called Parano but it fails over networks, with cksfv it needs to be installed in both source and destination machines

---

### Post by undecim on 2010-03-01
```
find ./ -type f -exec md5sum {} \; > md5sums
```Will list the md5sum of every file in the current directory and its sub directories. and put them in the file "md5sums"

Do that on both ends, then just take the md5sum of both md5sums and compare them```
md5sum md5sums
```

If you get two different results, you can check the files linewise with diff:```
diff md5sums1 md5sums2
``` to see what files you need to re-download

---

### Post by Jive Turkey on 2010-03-02
Thanks guys, both very good suggestions.

---

### Post by asmoore82 on 2010-03-02
rsync!

... but you need to have SSH server on one of the machines.

something like...

```
rsync --dry-run -avz --checksum asmoore@192.168.1.101:/home/asmoore/Music/ /home/asmoore/Music/
```

The beauty of this is, if you take out the `--dry-run` it will fix any bad files for you,
just make sure you have the source and destination in the right order!!

rsync tip: always end folder names with a final ``/'' -
the following 2 commands will behave exactly the same,
but the 2nd one is much easier for humans to read:
```
rsync -av /home/user /backup/home/
rsync -av /home/user/ /backup/home/user/
```
^^it's more obvious in the 2nd command that you want to sync 2 folders named "user".

the common mistake you want to avoid is this:
```
[COLOR="Red"]### avoid this
rsync -av /home/user /backup/home/user/[/COLOR]
```
^^this will create a nested folder "/backup/home/user/user"

---

