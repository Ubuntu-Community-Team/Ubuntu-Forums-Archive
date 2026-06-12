---
title: "Installing TrueCrypt in ubuntu 11.04, help?"
date: 2011-09-21
forum: General Help
---

### Post by tfbielawski on 2011-09-21
I have the same problem and nothing seems to work.

I am running Natty 11.04 x64. And I downloaded: truecrypt-7.1-linux-x64.tar.gz  this was the "Standard 64 bit" option. I also tried the "Standard 32 bit" option with precisely the same results each time.

1st- I right clicked on the file and chose Open with Archive Manager. The Manager attempts to extract and gives the following [I]error:
gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now[/I]

2nd- As suggested above, I tried the code in terminal: tar -xvf truecrypt-7.1-linux-x64.tar.gz. This is what happened: [I]Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
[/I]

3rd- I downloaded the file again and repeated above steps with both the 32 and 64 bit with the same results.

Any suggestions?

Thanks!

Tom B.

---

### Post by oldos2er on 2011-09-21
I've moved your post to its own thread to better your chances of getting help.

---

### Post by patryk77 on 2011-09-21
> **oldos2er said:**
> I've moved your post to its own thread to better your chances of getting help.

Thanks for that :P

On to the issue at hand: You need to be in the correct directory in the terminal for this to work, and if it tells you the file doesn't exist you probably aren't.

Are the .tar.gz file in ~/Downloads?

If so, do:
cd ~/Downloads
ls 
# ls will list the files so you can be sure it is indeed there
# Optionally, move it to /tmp and extract it there to keep out the clutter
mv truecrypt-7.1-linux-x64.tar.gz /tmp
cd /tmp
tar -zxvf truecrypt-7.1-linux-x64.tar.gz
# The z option in "tar -**z**xvf" is important, as it's a GZipped file (.gz)

You will then (hopefully) see a list of all the files being extracted.

---

### Post by tfbielawski on 2011-09-21
@ Olddos2er- Thanks!!!

@ Patryk77- You were correct that I was in the downloads folder, so I followed your instructions. Here is the error I recieved: 

[I]tar (child): trucrypt-7.1-linux-x64.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now[/I]

Seems to be the same error, only slightly modified. 

Tom

---

### Post by patryk77 on 2011-09-21
> **tfbielawski said:**
> [I]tar (child): trucrypt-7.1-linux-x64.tar.gz

It's modified in 2 ways... First, it says (child) because now the error is returned by gunzip and not by tar (that's good and not really important).

Second, it says trucrypt without an e.

Did you copy that output from the terminal? If so, you probably mistyped the name.

Best way to avoid that is by using Bash Completion.

Simply type:
tar -zxvf tru
and press the TAB key, this should complete it to the file it matches.

If more than one file matches, pressing tab again will give you a list of all matching files.

If the file is still not there, use these 2 commands:
pwd
ls

and copy/paste the output. pwd = print working directory (tells you where you are, which should be /tmp)

ls lists the files in the current directory, which will tell you if the truecrypt file is indeed in the current directory.

---

### Post by tfbielawski on 2011-09-21
Thanks. I definitely left out the "e".

Here is the output I received when I corrected the typo:

[I]
gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
[/I]

LOL, I'm almost ready to give up!

Tom

---

### Post by patryk77 on 2011-09-21
Sorry, I should have tackled the EOF from the get-go :P

EOF means that you have an incomplete file.

Remove it:
rm truecrypt-7.1-linux-x64.tar.gz

Download it anew:
```
wget http://www.truecrypt.org/download/truecrypt-7.1-linux-x64.tar.gz
ls -l truecrypt-7.1-linux-x64.tar.gz
#should say it's 2670835 bytes long
sha512sum truecrypt-7.1-linux-x64.tar.gz
#check integrity, should say:
# fe6caf5f5bb9c26db02a99dec2e40c67f48ea4aaee55263e243c9d5792407307970cdb20cca7fd3534a586e47b01592133ae0f04e99fd66aadc2e472fab80050 truecrypt-7.1-linux-x64.tar.gz
# now extract it
tar -zxvf truecrypt-7.1-linux-x64.tar.gz

```

That should do it ;)

If you get no errors, do the following to install
chmod +x truecrypt-7.1-setup-x64 
./truecrypt-7.1-setup-x64

---

### Post by tfbielawski on 2011-09-21
Woohooooo!!!! Thank you!!! Thank you!!! Thank you!!!):p :d

---

### Post by oldos2er on 2011-09-21
If your problem has been solved, please mark it 'Solved', under Thread Tools. Thanks!

---

