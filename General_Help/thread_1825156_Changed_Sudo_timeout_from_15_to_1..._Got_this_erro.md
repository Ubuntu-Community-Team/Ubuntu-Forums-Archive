---
title: "Changed Sudo timeout from 15 to 1... Got this error... is this Bad?"
date: 2011-08-14
forum: General Help
---

### Post by M!SF!TS on 2011-08-14
@linux:~$ sudo visudo
>>> /etc/sudoers: syntax error near line 28 <<<
sudo: parse error in /etc/sudoers near line 28
sudo: no valid sudoers sources found, quitting

---

### Post by WyleECoyote on 2011-08-14
```
sudo cat /etc/sudoers
```

paste output in next reply

---

### Post by trozamon on 2011-08-14
Did you use that initially use "sudo visudo" to edit /etc/sudoers ? Cuz if you didn't, that may cause an error.

---

### Post by M!SF!TS on 2011-08-14
```
@linux:~$ sudo cat /etc/sudoers
```

output was:

```
@linux:~$ sudo cat /etc/sudoers
>>> /etc/sudoers: syntax error near line 28 <<<
sudo: parse error in /etc/sudoers near line 28
sudo: no valid sudoers sources found, quitting

```

---

### Post by M!SF!TS on 2011-08-14
> **trozamon said:**
> Did you use that initially use "sudo visudo" to edit /etc/sudoers ? Cuz if you didn't, that may cause an error.

```
@linux:~$ sudo visudo
```

^^^ that was my original input

---

### Post by WyleECoyote on 2011-08-14
wow, I think you may have kicked yourself out of your system, I hope someone else can help you. Sorry I have never seen this before

---

### Post by WyleECoyote on 2011-08-14
please humor me on this one kind of a shot in the dark but hope to hit something

```
ls /etc/sudoers.d
```

---

### Post by M!SF!TS on 2011-08-14
Yeah the only way I discovered it was after I closed vi
I just for some reason wanted to just look at the sodoers file again...
and BAM got this

```
@linux:~$ sudo visudo
>>> /etc/sudoers: syntax error near line 28 <<<
sudo: parse error in /etc/sudoers near line 28
sudo: no valid sudoers sources found, quitting

```

---

### Post by M!SF!TS on 2011-08-14
```
@linux:~$ ls /etc/sudoers.d
README

```

---

### Post by WyleECoyote on 2011-08-14
yep thought so, sorry I was hoping that was your problem and the last chance for me to help sorry I will still keep an eye open for similar issues and hope to find your fix unless you have better luck soon

---

### Post by WyleECoyote on 2011-08-14
ok nother last ditch effort:

[http://www.intelligrape.com/blog/2011/02/27/linux-trick-to-get-your-user-back-to-sudo-access-while-you-lost-your-admin-password-and-you-are-with-no-sudo-prevailages/](http://www.intelligrape.com/blog/2011/02/27/linux-trick-to-get-your-user-back-to-sudo-access-while-you-lost-your-admin-password-and-you-are-with-no-sudo-prevailages/)

---

### Post by M!SF!TS on 2011-08-14
::looking for a screwed the pooch smiley::

---

### Post by M!SF!TS on 2011-08-14
Ugggh this is annoying. LOL I just installed this OS to start with a fresh one. not even an hour ago.

](*,)

---

### Post by M!SF!TS on 2011-08-14
I just did it re-installed it fresh again, Didn't have not important on this box anyways.

LOL so there is the fix! re-installed Ubuntu from scratch!

[SOLVED] :P

---

### Post by JKyleOKC on 2011-08-14
Since it was a fresh install, your solution was probably the easiest and best. However for future reference, if you can get to a GRUB menu at boot time, select the "Recovery Mode" option. This will automatically log you in as the root user so that you do not need "sudo" and from there you can view /etc/sudoers and can use "visudo" to edit the file.

This also works if you forget your login password -- but it's a potential security risk too, if anyone else has physical access to your machine!

---

### Post by WyleECoyote on 2011-08-15
Thank You for that info JKyleOKC

I never realized that safe mode was ran in root till now I will definitely remember this if it ever happens to me

---

### Post by M!SF!TS on 2011-08-15
> **JKyleOKC said:**
> get to a GRUB menu at boot time, select the "Recovery Mode" option. This will automatically log you in as the root user from there you can view /etc/sudoers -- but it's a potential security risk too, if anyone else has physical access to your machine!


That's good information to know.

Here is a question, You mentioned potential security risk for person(s) having physical access to my box.

Would the best solution to safe gaurd this risk be a BIOS boot passwd?

---

### Post by JKyleOKC on 2011-08-15
> **M!SF!TS said:**
> Here is a question, You mentioned potential security risk for person(s) having physical access to my box.

Would the best solution to safe gaurd this risk be a BIOS boot passwd?If anyone else has physical access, there's not much you can do to keep the box safe. Even with a boot password, it would be possible to open the box, physically remove the drive, take it to another machine, and do whatever. You could protect against that by making it difficult to get inside the box, but then any needed repair becomes a problem.

Bottom line is that security and repair-ability are mutually exclusive and must be balanced against each other.

You can remove the "recovery mode" option from the GRUB menu, but then you might not be able to make repairs such as the original problem of this thread. It's all a matter of balance!

---

### Post by M!SF!TS on 2011-08-15
Well yeah I mean if I had data that deemed the government, foreign government operative, or a search and seizure warrant for god knows what. 

I was being more specific for the typical drunk friend, pissed off girl friend, or curious cousin and in-laws type deal... Not the SWAT Team kick in the door and hold shot guns and automatic rifles to your face tearing your place apart just to seize a information system from a scrawny 6 foot tall 150lbs who never shot or owned a gun, lifehacker computer geek 

BIOS Password... I was just wondering if there was another option or better way.

Security is really one of those balancing acts like you mentioned I agree totally. LOL like look at my original post in what I was trying to do.

sudo visudo

to edit the timeout for sudo
,timestamp_timeout=0 
yeah sure you can enter you admin password 12 times to install a stupid printer driver. ot just do this to save the headache of a 30 second install and modify the sodoers file to this ,timestamp_timeout=1

---

### Post by M!SF!TS on 2011-08-15
> **JKyleOKC said:**
> future reference, if you can get to a GRUB menu at boot time, select the "Recovery Mode" option. This will automatically log you in as the root user so that you do not need "sudo" and from there you can view /etc/sudoers and can use "visudo" to edit the file.

Thanks for solving the question JKyleOKC. If I had some beans I would give them to you :)

---

### Post by M!SF!TS on 2011-08-15
If this happens to anyone else: 

hold the "Shift" key before boot up to enter Grub2

[SOLVED]

---

