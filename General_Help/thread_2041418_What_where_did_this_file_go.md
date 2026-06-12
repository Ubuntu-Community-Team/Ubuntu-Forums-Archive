---
title: "What? where did this file go?"
date: 2012-08-12
forum: General Help
---

### Post by LLCoolJeff on 2012-08-12
I was trying to install adobe air and I had the .bin file on my desktop, so i thought I would put in some practice on the terminal moving things around and making a new directory for it.

I navigated to my desktop and did this:

```
sudo mv AdobeAIRInstaller.bin /xubuntu
```and the file disappeared so I thought, cool it went into my zubuntu directory on my desktop...Wrong

its not there, and when I search for it using catfish, it brings back 

[IMG]http://i47.tinypic.com/fb2qb.png[/IMG]

What the hell is wrong with me, where could it have gone?


```
find / AdobeAIRInstaller.bin
```

also just tried this ^^^^^ and it didn't find it anywhere

---

### Post by vasa1 on 2012-08-12
I suggest you use a nice tutorial that explains just what **mv** does. I can't think of one right now but there are a lot of them around.

---

### Post by papibe on 2012-08-12
Hi LLCoolJeff.

The command you executed did this: it moved the file to the root directory and it renamed the file as xubuntu.

To get it back to your home directory rin this:
```
sudo mv /xubuntu ~/AdobeAIRInstaller.bin
```
Tell us how it goes.
Regards.

---

### Post by LLCoolJeff on 2012-08-12
> **papibe said:**
> Hi LLCoolJeff.

The command you executed did this: it moved the file to the root directory and it renamed the file as xubuntu.

To get it back to your home directory rin this:
```
sudo mv /xubuntu ~/AdobeAIRInstaller.bin
```Tell us how it goes.
Regards.

and then by the same logic, what you just told me moved it and renamed it desktop right? cuz thats what hapenned when I did this:

```
$ sudo mv /xubuntu /home/Desktop
```

---

### Post by papibe on 2012-08-12
Almost.

If the destination is a directory, the file is not renamed but only moved to the destination directory.

Regards.

---

### Post by ads52 on 2012-08-12
> **LLCoolJeff said:**
> What the hell is wrong with me, where could it have gone?
```
find / AdobeAIRInstaller.bin
```also just tried this ^^^^^ and it didn't find it anywhere

What is wrong with you is that like all of us you at one stage you have made a mistake :). Perhaps for your find syntax you could try:

```

sudo find / -name AdobeAIRInstaller.bin

```Of course this will not find the file if it has been renamed :(.

---

### Post by GeneralCody on 2012-08-12
If you did:
sudo mv AdobeAIRInstaller.bin /xubuntu

You basically moved the AdobeAIRInstaller.bin from your current directory to the root directory /
You should be able to mv it back using:

sudo mv /xubuntu ~/Desktop/AdobeAIRInstaller.bin

This would move the file back to the folder called Desktop in your home directory...

Good luck.

---

### Post by LLCoolJeff on 2012-08-12
> **GeneralCody said:**
> If you did:
sudo mv AdobeAIRInstaller.bin /xubuntu

You basically moved the AdobeAIRInstaller.bin from your current directory to the root directory /
You should be able to mv it back using:

sudo mv /xubuntu ~/Desktop/AdobeAIRInstaller.bin

This would move the file back to the folder called Desktop in your home directory...

Good luck.

ok I think I get it a little bit, quick question about moving up directories though:

If I wanted to move from desktop to /home would I just do:
```
$ mv file1 /home/filename
```

---

### Post by papibe on 2012-08-12
I think you mean "your" home. If so, your home directory is /home/youruser (or ~/)

Then you would have to do:
```
mv ~/Desktop/AdobeAIRInstaller.bin  ~/
```
or
```
mv ~/Desktop/AdobeAIRInstaller.bin  /home/youruser
```
or
```
mv /home/youruser/Desktop/AdobeAIRInstaller.bin  /home/youruser
```
(replace youruser with your actual username).

Regards.

---

### Post by GWBouge on 2012-08-12
If you're moving to a directory that already exists, you don't need to specify a filename, but you can if you want.  If the destination you specify doesn't exist, mv assumes you want to rename the file you're moving, it won't automatically make a folder.  And remember, '/home' isn't *your* home directory, that's the folder where users' home directories go.  So you're home dir, for example, would be something like /home/LLCoolJeff

You may have overlooked/misunderstood the tilda (~) earlier as well.  It's just shorthand for your home directory.  'cd ~/' would be the same as 'cd /home/LLCoolJeff/'

Starting over from the beginning, to move that file to a 'xubuntu' folder on your desktop, it should have went like this:

```
mkdir ~/Desktop/xubuntu
mv ~/Desktop/AdobeAIRInstaller.bin ~/Desktop/xubuntu
```

*Edit*
D'oh, ninja'd.

---

### Post by LLCoolJeff on 2012-08-12
> **GWBouge said:**
> If you're moving to a directory that already exists, you don't need to specify a filename, but you can if you want.  If the destination you specify doesn't exist, mv assumes you want to rename the file you're moving, it won't automatically make a folder.  And remember, '/home' isn't *your* home directory, that's the folder where users' home directories go.  So you're home dir, for example, would be something like /home/LLCoolJeff

You may have overlooked/misunderstood the tilda (~) earlier as well.  It's just shorthand for your home directory.  'cd ~/' would be the same as 'cd /home/LLCoolJeff/'

Starting over from the beginning, to move that file to a 'xubuntu' folder on your desktop, it should have went like this:

```
mkdir ~/Desktop/xubuntu
mv ~/Desktop/AdobeAIRInstaller.bin ~/Desktop/xubuntu
```*Edit*
D'oh, ninja'd.

ok playing around with it a little more I think I get it:

in the second part where you specify where it is being moved to, it will move it to directories until it comes across a directory which doesn't exist, and then it will rename it to that which does not exist.

So if my ./Desktop does not contain a dir called xubuntu, it will simply rename the file xubuntu.  

Am I correct?
If so, this is what makes the whole thing make sense, without that piece of info it appears to just do whatever it wants...

---

### Post by marlow59 on 2012-08-12
yes exactly. for further information, the manual page for the mv command is really well documented. run
```
 man mv 
```
and you will find everything you want concerning this command.

---

### Post by marlow59 on 2012-08-12
if your problem is solved, please mark the thread as [Solved]

---

