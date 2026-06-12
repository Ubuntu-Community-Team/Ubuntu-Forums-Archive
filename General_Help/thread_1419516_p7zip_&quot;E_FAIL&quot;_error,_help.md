---
title: "p7zip &quot;E_FAIL&quot; error, help?"
date: 2010-03-01
forum: General Help
---

### Post by kenji_03 on 2010-03-01
So the back story is that when I first got onto Ubuntu I used Archive Manager to 7zip a bunch of my files (what I now know is p7zip) I put a password on them as I wanted to keep these files safe.  They were my back-up files.  The time has come to where I need my backups but I keep getting this E_FAIL error.

I am told it is because p7zip cannot open the password prompt, so can anyone tell me how to open it?  I really need to access these files again...

```

7-Zip 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,4 CPUs)

Error: /media/2067-C4DB/fresh/~Emergency Drive~.7z.001: E_FAIL                

Errors: 1
```

Edit: I already installed the "p7zip-full package" package

---

### Post by byStanderone on 2010-03-02
...as per this thread, e_fail error means short of space to do decompression:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=397763](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=397763)

---

### Post by kenji_03 on 2010-03-03
I have over 16 gigs of free space for 3 5mb 7zip files.  I cannot be "out of space"...

---

### Post by psusi on 2010-03-03
What was the command you gave to invoke 7zip?  Are you trying to extract the files to the same directory, which is on read only media?

---

### Post by Yannick Le Saint kyncani on 2010-03-03
> **kenji_03 said:**
> I am told it is because p7zip cannot open the password prompt

Then why don't you try the -pSuperSecretPassword option ?

---

### Post by kenji_03 on 2010-03-04
> **Yannick Le Saint kyncani said:**
> Then why don't you try the -pSuperSecretPassword option ?

Ya know... I'm not sure if you are joking or not...

Edit: I'm not "zipping" (compressing) a file I am unzipping (decompressing) a file and it gives me that E_Fail error.  I have over 16 gigs of free space.  I got it to ask me for the password but upon entering it I am returned with the same "e_fail" error...
[http://en.wikipedia.org/wiki/File:P7zip-terminal_output.png](http://en.wikipedia.org/wiki/File:P7zip-terminal_output.png)

Edit 2: I just tried the -p(pass) switch, no good.  To test what's happening I made a new 7zip archive, split it into 2 volumes, and set a password like before.  This time I get the prompt so something else is happening here... it might be that it's not reading I have the space but how can I fix that when I DO have the space?

---

### Post by psusi on 2010-03-04
No, -p is for entering the password rather than waiting to be prompted for it and typing it in then.  And again, WHERE are you trying to extract?  It does not matter how much free space you have on the hard disk if you are trying to extract to some other disk that is full, like a read only cdrom.

---

### Post by kenji_03 on 2010-03-04
> **psusi said:**
> What was the command you gave to invoke 7zip?  Are you trying to extract the files to the same directory, which is on read only media?

I have the files in my home/user folder and have tried accessing them with "sudo natilus" along with "sudo 7za -p (file)" I am now able to get the password up but it doesn't seem to be helping.

I have been using the "extract here" command with natiuls.

Edit: thank you for trying to help me on this, sorry for taking so long to reply as I'm frustrated from not simply being able to unzip this.

---

### Post by psusi on 2010-03-04
Ahh... ok, from what you originally posted it looked like you were trying to extract it right there on the cdrom.  What is the exact command and results when you try running 7z on the command line?

---

### Post by kenji_03 on 2010-03-04
> **psusi said:**
> Ahh... ok, from what you originally posted it looked like you were trying to extract it right there on the cdrom.  What is the exact command and results when you try running 7z on the command line?The file name is "~Emergency\ Drive~.7z.001" in terminal's "dir". [INDENT]**no Sudo**
[/INDENT]```
kenji03@K:~$ 7za e -p ~Emergency\ Drive~.7z.001

7-Zip (A) 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,4 CPUs)

Processing archive: ~Emergency Drive~.7z.001

Error: E_FAIL
```[INDENT]**Sudo**
[/INDENT]```
kenji03@K:~$ sudo 7za e -p ~Emergency\ Drive~.7z.001
[sudo] password for kenji03: 

7-Zip (A) 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,4 CPUs)

Processing archive: ~Emergency Drive~.7z.001

Error: E_FAIL
```

I just realized I may of been mistaking the Sudo password prompt for a 7zip password prompt

---

### Post by kyncani on 2010-03-04
I doubt it will work, however I don't think you're using the -p option correctly.

-pSuperSecretPassword means "SuperSecretPassword" is the password.

-p means "" (the empty string) is the password

not giving -p, if the archive requires a password, you will be prompted for one

So it you have a password with special characters, use -p'SuperSecretPa$$word with spacesAndStuff'

Please note that there is no space between -p and the password.
However, like I said, I doubt it will work, the error message I have is not E_FAIL.

---

### Post by macleapa on 2011-04-07
I realize this is an old post, but just incae anyone else is having this issue, I'll share another cause of this error.
 
If you are trying to extract a multi-part archive (1Gb files total over 8Gb).  The backup is on a 32bit filesystem (FAT32), and you are trying to extract the archive to the same 32bit filesystem.  This will not work as the max file size supported by the 32bit filesystem is 4Gb /file. 
 
Hope this helps someone.

---

### Post by MikeDK on 2011-04-26
I have the exact same problem, unzipping a file without password thou, get the very same results, and its pissing me off, pardon my french, but this is serious getting me thinking of rolling back from Maverick, or worse things :-S

7-Zip 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=da_DK.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)

Processing archive: /home/michael/Skrivebord/Billeder2.7z

---

### Post by justinjedlawton on 2011-06-11
7-Zip 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,1 CPU)

Error: /home/justin/Documents/Downloads/bible_web_old_testament_0901_librivox2_64kb_mp3.zip: Can not open file as archive

Errors: 1



ig et this after tryong to un zip is suposed o b a audio file only 252mb not even archive mpunter will work could the file b too big ? or b courpted?

---

### Post by Francewhoa on 2013-03-21
> **macleapa said:**
> I realize this is an old post, but just incae anyone else is having this issue, I'll share another cause of this error.
 
If you are trying to extract a multi-part archive (1Gb files total over 8Gb).  The backup is on a 32bit filesystem (FAT32), and you are trying to extract the archive to the same 32bit filesystem.  This will not work as the max file size supported by the 32bit filesystem is 4Gb /file. 
 
Hope this helps someone.

Thanks macleapa :) Confirming this is the source of the issue.

---

### Post by Francewhoa on 2013-03-21
**Here is a workaround.** Uncompress only part of the file at once. Less than 4GB per try. To do so with Ubuntu 12.04:

[LIST=1]
[*]Right click the compress file 
[*]Select "Open with Archieve Manager" 
[*]Select files up to 4GB 
[*]Extract 
[*]Repeat above for remaining files, bingo :razz: 
[/LIST]

---

