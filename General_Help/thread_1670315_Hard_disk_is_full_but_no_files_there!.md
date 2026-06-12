---
title: "Hard disk is full but no files there!"
date: 2011-01-18
forum: General Help
---

### Post by khurtsiya on 2011-01-18
I am having trouble with my HDD.

Here is how Disk Usage Analyzer looks like:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=181472&stc=1&d=1295397219[/IMG]

But I can not find any files there to delete.

Trash is also clean.

Any idea what is wrong?

TIA

PS
Ubuntu 11.04

---

### Post by khurtsiya on 2011-01-19
anyone?

---

### Post by khurtsiya on 2011-01-19
anyone?

---

### Post by ndefontenay on 2011-01-19
Hi.

The folder /media is a folder where external devices are plugged.

What's interesting in your case, it's that you got a file called .ecryptfs

the . (dot) preceding the folder name means it's hidding. You won't see it in the file manager

but from the command line you can do this:

```
cd /media/.ecryptfs; ls -l
```

Do yo have a large 145GB device connected to your computer?
If so, try removing it.

Also the disk space value from / (root) is relative. It will vary depending of the devices you plug.

If you look at the home folder for instance, you will see that it uses only 18% of its 36GB so your disk is not exactly full :)

Nico

---

### Post by khurtsiya on 2011-01-19
Thanks for the raply.

I have one 250GB HDD in my notebook.

26GB I leave for Windows and other is for Ubuntu. This part which I mount is I believe was created for /home folders but something went wrong...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=181495&stc=1&d=1295435463[/IMG]

PS
Sorry for my English, I am from Ukraine

---

### Post by khurtsiya on 2011-01-22
any ideas?
very annoing problem.......

---

### Post by khurtsiya on 2011-02-02
help please!

---

### Post by mikewhatever on 2011-02-02
What exactly is the problem?

---

### Post by khurtsiya on 2011-02-02
that / is full
but I have 250 Gb free on the disk

---

### Post by mikewhatever on 2011-02-02
What about the encrypted filesystem of 145GB?

---

### Post by khurtsiya on 2011-02-02
why is it encrypted and how can I decrypt i?

---

### Post by mikewhatever on 2011-02-02
You tell me, it's your system, is it not?

---

### Post by khurtsiya on 2011-02-02
actually I do not know.... any chances to decrypt it? or I need to format it to use then?

---

### Post by mikewhatever on 2011-02-02
If you don't have the password, then no, you can't decrypt it. Should probably ask the owner of that volume.
Do you mind posting the ouput of the **df -h | grep ^/** command.

---

### Post by khurtsiya on 2011-02-02
I believe I have all passwords

> khurtsiya@khurtsiya-laptop:~$ df -h | grep ^/
/dev/sda6              23G   20G  2.0G  91% /
/home/khurtsiya/.Private


---

### Post by mikewhatever on 2011-02-02
Did you install Ubuntu on that computer? Did you select to encrypt your home partition or something like that? If you did, and yet know nothing about the encrypted volume, I really don't know what to say.

---

### Post by khurtsiya on 2011-02-02
Previously there was Ubuntu 9.04
Then I deleted / and swap, created new one and installed 10.10
/home folder was untouched
but I believe I did not encrypt anything

---

### Post by mikewhatever on 2011-02-02
Let's check the size of your home partition with **du -hs /home/khurtsiya**

---

### Post by khurtsiya on 2011-02-02
executing this command took a lot of time.

here is output

> khurtsiya@khurtsiya-laptop:~$ du -hs /home/khurtsiya
16G	/home/khurtsiya


---

### Post by mikewhatever on 2011-02-02
It's odd, the sizes you post now don't match those in the screenshots, and the mysterious encryptfs volume you know nothing about. Do there other people use that computer?

---

### Post by khurtsiya on 2011-02-02
nope
can I give some more information to figure out what is happening?

---

### Post by mikewhatever on 2011-02-02
Well, what's going on is, you seem to have a 145GB encrypted volume taking up the space.

---

### Post by khurtsiya on 2011-02-02
so can I decypt it? or need to format?

---

### Post by mikewhatever on 2011-02-02
I would format.

---

### Post by khurtsiya on 2011-02-02
thank you!

---

