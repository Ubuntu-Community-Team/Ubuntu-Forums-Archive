---
title: "How can i compress files or create split archives and etc?"
date: 2010-04-25
forum: General Help
---

### Post by aviramof on 2010-04-25
i have noticed that if right click on many files types for instance iso  files i don't have the option to store them in 
compress files at all i  have one iso file now that i want to compress and split to three parts  so i could upload it but as i said right click on the file don't help
because i don't have the option there so what can i do?

thanks in advance.

---

### Post by HermanAB on 2010-04-25
Hmm, never tar files.  Only tar directories.

(It is very annoying when you untar something and end up with a gazillion files dumped all over your home directory)

Either read the 'tar' man page or read the 'split' man page.

---

### Post by byStanderone on 2010-04-25
...found this, hope it helps:[http://ubuntuforums.org/showthread.php?t=977060](http://ubuntuforums.org/showthread.php?t=977060)

---

### Post by john newbuntu on 2010-04-25
There are several utilitie.  'rar' being one of them.  The first line below compresses and splits the my.iso file into several rar chunks with each chunk=40mb.  It puts it all in one directory.  The second command looks at the first rar chunk and uncompresses and combines them all.

```
   rar a -v40m myArchive my.iso
   rar e myArchive.part1.rar

```
'man rar' from a terminal for more info.

---

### Post by colorlessprism on 2010-04-25
[B][FONT=Verdana][SIZE=1]original can be seen [HERE]("https://help.ubuntu.com/community/BackupYourSystem/TAR")[/SIZE][/FONT]
[/B]

**Archive Splitting**

 If you want to burn the archive to discs, or transfer them to a filesystem with a limited max filesize (say FAT32 with a limit of 4GB per file) then you will have to split the file either during or after archive creation. A simple means is to use the split command. Below are examples of both scenarios. More information than conveyed here can be found in the man pages of split, use man split in a terminal to read. Ensure you keep these archives all together in a directory you label for extraction at a later date. Once the archives are split to a desirable size, they can be burned one at a time to disc. 
**To Split During Creation** 
tar -cvpz <put options here> / | split -d -b 3900m - /name/of/backup.tar.gz. 
[LIST]
[*]The first half until the pipe (|) is identical to our earlier example, except for the omission of the f option. Without this, tar will output the archive to standard output, this is then piped to the split command. 
[*]**-d** - This option means that the archive suffix will be numerical instead of alphabetical, each split will be sequential starting with 01 and increasing with each new split file. 
[*]**-b** - This option designates the size to split at, in this example I've made it 3900mB to fit into a FAT32 partition. 
[*]**-** - The hyphen is a placeholder for the input file (normally an actual file already created) and directs split to use standard input. 
[*]**/name/of/backup.tar.gz.** Is the prefix that will be applied to all generated split files. It should direct to the folder you want the archives to end up. In our example, the first split archive will be in the directory /name/of/ and be named backup.tar.gz.01 . 
[/LIST]
**To Split After Creation** 
split -d -b 3900m /path/to/backup.tar.gz /name/of/backup.tar.gz. 
[LIST]
[*]Here instead of using standard input, we are simply splitting an existing file designated by /path/to/backup.tar.gz . 
[/LIST]
**To Reconstitute the Archive**
 Reconstructing the complete archive is easy, first cd into the directory holding the split archives. Then simply use cat to write all the archives into one and send over standard output to tar to extract to the specified directory. 

cat *tar.gz* | tar -xvpzf - -C /  
[LIST]
[*]The use of * as a wild card before and after tar.gz tells cat to start with first matching file and add every other that matches, a process known as catenation, how the command got its name. 
[*]Afterwards, it simply passes all that through standard output to tar to be extracted into root in this example. 
[*]For a more complete explanation of restoration, see [Restoring]("https://wiki.ubuntu.com/starcraft.man/Sandbox#Restoring"). 
[/LIST]

---

