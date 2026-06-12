---
title: "how to open recovered files ?"
date: 2010-02-28
forum: General Help
---

### Post by chitragurung on 2010-02-28
I had lost my emails and contact after using Evolution. some of forum user recommended to use photorec to recover all the files. I used and have stored all the files in a folder. Now my problem is there are over 1500 folders and in there over thousand and thousand of text files. How should I recognize which folder contains email and contacts and how to import to Evolution ?

---

### Post by SPr on 2010-02-28
cd into the top directory of the recovered files
```

cd /to/top/level/directory
find . -true>find.txt 
file -f find.txt

```
That will show what each file is along with /path/basename. You will then have to grep the output to match the filetypes you need. Evolution uses the following file types:
> 
8086 relocatable (Microsoft)
ASCII English text, with very long lines
ASCII mail text
ASCII mail text, with very long lines
ASCII text
ASCII text, with no line terminators
Berkeley DB 1.85 (Hash, version 2, native byte-order)
Berkeley DB (Hash, version 8, native byte-order)
data
empty
HTML document text
ISO-8859 mail text, with very long lines
Non-ISO extended-ASCII text
Non-ISO extended-ASCII text, with no line terminators
SQLite 3.x database
UTF-8 Unicode English text
vCalendar calendar file
XML  document text

found by running the following on my home dir
```

find ~/.evolution/ -true>find.txt
file -bf find.txt |grep -v directory>file.txt
sort file.txt|uniq

```

Edit: I'd assume grepping for "mail text" would find the relevent files but who knows?
```

file -f find.txt|grep "mail text"

```

Copy any "suspect" files to ~/.evolution/mail/local and open Evolution to see what Evolution makes of them.
I can't think of an easy way to recover any attachments though.

Edit2:
Looking for something completely different I found this:
```

find . -type f -exec file '{}' \;|grep "mail text"

```
which does the same thing without the need for all those text files.

---

### Post by chitragurung on 2010-02-28
Hello,

thank you for your advice. But I do not know how to run commands you mentioned. For example my files are located at home/Directory. In this case which command I need to type. When I type cd /to/top/level/Directory it says there is no such file or directory etc.

There is 1500 directories recovered and in each directory over 1000 files. Is that possible to find easily ?

---

### Post by SPr on 2010-03-01
```

cd /home/Directory

```
I didn't know where the files/directories were on your HDD so I couldn't give explicit instructions. If they are in /home/chitragurung/DIRECTORIES then type
```

cd /home/chitragurung/DIRECTORIES

```
if they are in /home/chitragurung/recovered_files/ type
```

cd /home/chitragurung/recovered_files

```
cd = change directory so it wont harm the computer.

The command (find . -type f -exec file '{}' \;|grep "mail text") will take a long time to dig through all the files and directories. I don't know how much time it will take for your PC to do that.

It will be easy for the PC to find those files but very, very time consuming, boring and laborious for you to check each file by hand.

Linux is excellent at this kind of job and will plough through each and every file and directory and give the names of the files that may contain emails.

Edit
```
find . -type f -exec file '{}' \;|grep "mail text">files.txt
```
will save the output to a file called (for want of a better name) files.txt

---

### Post by chitragurung on 2010-03-01
After doing those commands, it will save collected file in different directory or file name or we have to copy manually one by one. I have 1140 directories and 500 items in each folder so it may take very long time I assume. Also this command collects contacts or address books ?

---

### Post by SPr on 2010-03-02
It will only give you the name and path of the file. You will have to do the copying and check that you copied the correct files. Contact lists etc will probably be stored in the database files I gave earlier.

I have given you a start by showing you how to pick out possible candidates for the deleted emails; you still have work to do. Have you actually tried searching for the files yet?

change 
grep "mail text"
to
grep "Berkeley DB"
for example to find possible candidates for contact lists (I assume they are stored in a database). Those commands wont do any harm so you can experiment with them. I don't know how evolution works or how it stores or searches for data.

If you had kept backups of the emails etc you wouldn't have to do any of this. I learnt the hard way and it seems that you are learning the hard way too.

---

### Post by chitragurung on 2010-03-03
Yes, I was using windows till  October 2009. When I bought new Dell Mini Inspiron it came with UBUNTU. It looks nice  O system. Evolution also was nice,  but when I try to import or extract some mails from text file or some file, it deleted all my mails and contacts. I had no back up as well so I am also trying hard way you are doing.

Well I tried some of command you mentioned and it found lots of file and it could complete even in 4-5 hours so I stopped. May be I should run again but which one can be shorter time ?

Thanks

---

### Post by Pritamsng on 2010-03-03
ya... no need to use find command... as i think..
beacause due to shutdown or any othere issue you can not save your file the it i will store as .<filename>.swp in same dir where you tried to create it or need to check home dir only.

---

### Post by SPr on 2010-03-03
Four or five hours? I'm glad I don't have to do this with my old PC :)
If it has already found some files have you tried moving them to the .evolution directory yet?
```

cp /path/to/file/name_of_file ~.evolution/local/Inbox.sbd

```
You will have to change /path/to/file/name_of_file to an entry in files.txt. Don't rename the file just let evolution sort it out.

I too have trouble with Evolution at times. I have heard that Thunderbird is a better mail client.

---

### Post by chitragurung on 2010-03-04
I tried and pasted some text file to .evolution directory and when I reopen evolution, I got a folder which contain one email. So, it mean each mail has one text file or something like that.

---

### Post by SPr on 2010-03-04
Emails aren't stored one per file. Keep going and see what appears.

---

