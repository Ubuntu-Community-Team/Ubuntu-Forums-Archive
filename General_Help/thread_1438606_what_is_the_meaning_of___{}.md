---
title: "what is the meaning of   {} \ ?"
date: 2010-03-25
forum: General Help
---

### Post by luofeiyu on 2010-03-25
there is a command:
find / -name "*~" -exec rm -rfv {} \
can you tell me the meaning of {} \  ?

---

### Post by nothingspecial on 2010-03-25
{} means what find has found

\ escapes the ; that should go immediately after it to end the command.

Are you sure you want to do that?

---

### Post by gmargo on 2010-03-25
All the juicy details can be found in the **find(1)** man page.

For each matched file that **find** finds, the command after the -exec is run, with the file's pathname substituted for {}.  The command string is terminated by a semicolon.  Since a semicolon would normally be interpreted by the shell as a command separator, the backslash is added to prevent the shell's interpretation and to pass it along as an argument to **find**.

---

### Post by luofeiyu on 2010-03-25
the command can delete files  which ended with character~ .
when the file contain  a space-bar , such as 
/home/pt/test/vcd make.txt~
/home/pt/test/movie translate.txt~
the command can delete them
find / -name "*~" -exec rm -r {} \&#65307;

i have written other two command to delete them,
command 1:
 rm -rf ` find / -name '*~'`
command 2:
find / -name '*~' >list.txt
rm -f $(cat ./list.txt)

both command 1 and command 2  can not delete (but find / -name "*~" -exec rm -r {} \&#65307; can delete )
my file which contain a space-bar

/home/pt/test/vcd make.txt~
/home/pt/test/movie translate.txt~

if i delete a space-bar ,
/home/pt/test/vcdmake.txt~
/home/pt/test/movietranslate.txt~
command1 and command2 can delte them ,
now ,my problem is :
how to revise cammand1 and command2 to make them can delte my files (filenames contain  a space-bar)??

---

### Post by renkinjutsu on 2010-03-25
it's a command used by people who just don't like clutter. Basically it deletes everything with a ~ character appended to the name. Gedit saves a backup file 'filename~' everytime you save a file (if the option is enabled [it's enabled by default] ), so there will be duplicates of tons of textfiles that aren't necessarily needed.
that find command finds them, then deletes them

---

### Post by satish_j on 2010-03-26
As said by renkinjutsu,the command is for removing clutter...I use it periodically to remove the backup files,as i do not feel the need of keeping the same..

---

### Post by gmargo on 2010-03-26
> **luofeiyu said:**
> 
i have written other two command to delete them,
command 1:
 rm -rf ` find / -name '*~'`
command 2:
find / -name '*~' >list.txt
rm -f $(cat ./list.txt)

how to revise cammand1 and command2 to make them can delte my files (filenames contain  a space-bar)??

```

# command 1:
find / -name '*~' -print0 | xargs -0 rm -f            # (removed -r option)

# command 2:
find / -name '*~' >list.txt
tr '\n' '\0' < list.txt | xargs -0 rm -f

```(If you're going to  search from the root directory, using the find command's -xdev option is a good idea to avoid searching  the special directories like /proc and /sys.  You'll need another search  for each valid filesystem, for instance /home.)

---

### Post by satish_j on 2010-03-26
Thanks gmargo..learnt a new thing today..I assume we can use xargs as follows to delete the files from a directory??
```

ls /var/log | xargs rm -f

```

---

