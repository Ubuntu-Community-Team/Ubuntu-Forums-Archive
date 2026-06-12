---
title: "Opening and Importing PST files in Ubuntu"
date: 2010-05-10
forum: General Help
---

### Post by pramathesh on 2010-05-10
Guys,
     Just formatted my office notebook with Ubu 9.04. Problem is I don't find any app/plug-in that will help me import PST files in Thunderbird. All help is appreciated! :)

---

### Post by todak on 2010-05-10
See [here]("http://kb.mozillazine.org/Import_.pst_files") for possible solutions.

---

### Post by sedawk on 2010-05-10
The tool is called "readpst" and is a frontend to the library
libpst.

"sudo apt-get install readpst" should do the trick.

I have used it a few times and it worked fine.

---

### Post by pramathesh on 2010-05-10
I've heard readpst is not being developed any futher will still give it a try and see if that helps!

---

### Post by pramathesh on 2010-05-10
readpst cannot open file here's the log.

pravinc@pravinc-laptop:~$ READPST
bash: READPST: command not found
pravinc@pravinc-laptop:~$ readspst
bash: readspst: command not found
pravinc@pravinc-laptop:~$ readpst
ReadPST / LibPST v0.6.27
Little Endian implementation being used.
GCC 4.3 : Mar 27 2009 22:51:25
Usage: readpst [OPTIONS] {PST FILENAME}
OPTIONS:
	-V	- Version. Display program version
	-C	- Decrypt (compressible encryption) the entire file and output on stdout (not typically useful)
	-D	- Include deleted items in output
	-M	- MH. Write emails in the MH format
	-S	- Separate. Write emails in the separate format
	-b	- Don't save RTF-Body attachments
	-c[v|l]	- Set the Contact output mode. -cv = VCard, -cl = EMail list
	-d <filename> 	- Debug to file. This is a binary log. Use readpstlog to print it
	-h	- Help. This screen
	-k	- KMail. Output in kmail format
	-o <dirname>	- Output directory to write files to. CWD is changed *after* opening pst file
	-q	- Quiet. Only print error messages
	-r	- Recursive. Output in a recursive format
	-w	- Overwrite any output mbox files
pravinc@pravinc-laptop:~$ cd desktop
bash: cd: desktop: No such file or directory
pravinc@pravinc-laptop:~$ Desktop
bash: Desktop: command not found
pravinc@pravinc-laptop:~$ cd Desktop
pravinc@pravinc-laptop:~/Desktop$ readpst -m Personal Foleders_05.10.10.pst
readpst: invalid option -- 'm'
ReadPST / LibPST v0.6.27
Little Endian implementation being used.
GCC 4.3 : Mar 27 2009 22:51:25
Usage: readpst [OPTIONS] {PST FILENAME}
OPTIONS:
	-V	- Version. Display program version
	-C	- Decrypt (compressible encryption) the entire file and output on stdout (not typically useful)
	-D	- Include deleted items in output
	-M	- MH. Write emails in the MH format
	-S	- Separate. Write emails in the separate format
	-b	- Don't save RTF-Body attachments
	-c[v|l]	- Set the Contact output mode. -cv = VCard, -cl = EMail list
	-d <filename> 	- Debug to file. This is a binary log. Use readpstlog to print it
	-h	- Help. This screen
	-k	- KMail. Output in kmail format
	-o <dirname>	- Output directory to write files to. CWD is changed *after* opening pst file
	-q	- Quiet. Only print error messages
	-r	- Recursive. Output in a recursive format
	-w	- Overwrite any output mbox files
pravinc@pravinc-laptop:~/Desktop$ readpst -M Personal Foleders_05.10.10.pst
Opening PST file and indexes...
cannot open PST file. Error
Error opening File
pravinc@pravinc-laptop:~/Desktop$ readpst -k Personal Foleders_05.10.10.pst
Opening PST file and indexes...
cannot open PST file. Error
Error opening File
pravinc@pravinc-laptop:~/Desktop$ readpst -o <Desktop> Personal Foleders_05.10.10.pst
bash: Desktop: No such file or directory
pravinc@pravinc-laptop:~/Desktop$ readpst -o <Desktop> Personal Foleders_05.10.10.pst
bash: Desktop: No such file or directory
pravinc@pravinc-laptop:~/Desktop$ readpst -o Personal Foleders_05.10.10.pstOpening PST file and indexes...
cannot open PST file. Error
Error opening File
pravinc@pravinc-laptop:~/Desktop$

---

### Post by nomnex on 2010-06-25
I did a test opening some f****** Mikeysoft .pst files.
worked as expected as commented by sedawk.
you don't give any information about the .pst version, and are you sure you pass the correct command? Try it without switch to see if that works.

step-by-step
> 1. $ cd ~/mypst_directory (i.e. type the path of your dir.)
2. $ ls (list your .pst files)
3. $ readpst (in small letter) mypst(your_file_name).pst
4. Enter (push enter)


---

### Post by StuartN on 2010-06-25
> **nomnex said:**
> , and are you sure you pass the correct command?

Pramathesh, you are not accurately typing the folder and filenames. Linux is case-sensitive, so desktop and Desktop are two different folders that may both exist. The option M is uppercase, there is no option m. The filename **Personal Foleders_05.10.10.pst** contains a space, so the space must be escaped ("\ ") or the whole filename enclosed in quotes: 

```
readpst -M "Personal Foleders_05.10.10.pst"
readpst -M Personal\ Foleders_05.10.10.pst
```

Try using tab-completion by typing "readpst -M Per" and pressing tab (and either type more characters or press tab again if there is more than one match).

**WARNING:** Do you really want to create all the mbox files on your Desktop? If not, then change directory to or specify an output location.

---

### Post by xav!or on 2012-11-08
Is there a way to find or specify multiple PST's and search them all together for specific keywords and such?

---

### Post by oldos2er on 2012-11-08
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

