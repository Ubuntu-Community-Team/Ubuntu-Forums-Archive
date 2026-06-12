---
title: "Help! Accidently deleted my ENTIRE mp3 collection"
date: 2010-02-06
forum: General Help
---

### Post by CSHANKY on 2010-02-06
Can anyone PLEASE tell me where I can find a tool / utility that can help me recover my precious mp3 files? 

I deleted and cleared my trash.

Running 9.10 on my desktop

---

### Post by msrinath80 on 2010-02-06
Stop writing any more data to it. For that matter, remount the partition read only to be safe. Search for a program called ext3undel and see how far you can get. Good Luck!

---

### Post by ranatanveer on 2010-02-06
yes only good luck :)

---

### Post by SeanHodges on 2010-02-06
Consult the data recovery documentation:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I've found the "foremost" utility very useful for this kind of thing.

---

### Post by bug67 on 2010-02-06
Oh NO!  :(

I am so sorry to hear that.  Unfortunately, I can offer no *recovery* advice.  However, it is *exactly* for reasons like this I have my "precious mp3 collection" backed up to 6 different locations (7 if you include the actual CDs I originally ripped from).  Same thing has happened to me.  It will ***_NEVER_*** happen again.

Might I suggest, if you do recover your data, buying an external hard drive and doing the same...just in case!

---

### Post by jflaker on 2010-02-06
Reminds me of a conversation I overheard about backing up data

"if you don't back up your data, you will be sorry"

"Are you sorry?"

Ubuntu One is one option as well as keeping copies on different media....and external drive is a good choice.

Back up your data, not your applications or OS as both of those can be reinstalled.....Backup often and if possible, automate the task so that you don't have to think about it.

---

### Post by gamerchick02 on 2010-02-06
If you need a backup program, I recommend Back In Time.  It's available in the repos and you can set it to run daily backups.  I'd recommend this for the future.

Sorry your music collection is wiped.  :(

Amy

---

### Post by CSHANKY on 2010-02-06
> **SeanHodges said:**
> Consult the data recovery documentation:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I've found the "foremost" utility very useful for this kind of thing.
[B]Installed Foremost
[/B]
[B]Did:

[/B]~$ sudo foremost -t mp3 -i /dev/hda -o /recovery/foremost

[B]Got:
[/B]
[COLOR=Purple]foremost version 1.5.6 by Jesse Kornblum, Kris Kendall, and Nick Mikus.
$ foremost [-v|-V|-h|-T|-Q|-q|-a|-w-d] [-t <type>] [-s <blocks>] [-k <size>] 
    [-b <size>] [-c <file>] [-o <dir>] [-i <file] 

-V  - display copyright information and exit
-t  - specify file type.  (-t jpeg,pdf ...) 
-d  - turn on indirect block detection (for UNIX file-systems) 
-i  - specify input file (default is stdin) 
-a  - Write all headers, perform no error detection (corrupted files) 
-w  - Only write the audit file, do not write any detected files to the disk 
-o  - set output directory (defaults to output)
-c  - set configuration file to use (defaults to foremost.conf)
-q  - enables quick mode. Search are performed on 512 byte boundaries.
-Q  - enables quiet mode. Suppress output messages. 
-v  - verbose mode. Logs all messages to screen[/COLOR]

[B]What am I supposed to do next? 
[/B]

---

### Post by tgalati4 on 2010-02-06
Testdisk and photorec work well:

sudo apt-get install testdisk
man testdisk
man photorec
sudo photorec -d /home/user/recovermypreciousmp3collectionthatispentyearscollecting /dev/sda

---

### Post by CSHANKY on 2010-02-06
> **tgalati4 said:**
> Testdisk and photorec work well:

sudo apt-get install testdisk
man testdisk
man photorec
sudo photorec -d /home/user/recovermypreciousmp3collectionthatispentyearscollecting /dev/sda
Thanks ! Installed and ready to go....

Is there a command that only recovers the MP3 files?

---

### Post by tgalati4 on 2010-02-07
Photorec tries to recover everything.  There is no way that I know of to limit it to a specific file type.  You could always look at the source code and modify it to work only on one file type.  The types of files it recognizes is huge, so it will automatically try to recover every type of file that has a known header type.

---

