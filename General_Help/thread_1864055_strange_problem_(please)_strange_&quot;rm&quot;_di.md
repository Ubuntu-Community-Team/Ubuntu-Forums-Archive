---
title: "strange problem (please) strange &quot;rm&quot; directory"
date: 2011-10-18
forum: General Help
---

### Post by youWho on 2011-10-18
I have a directory in my home folder called "rm" (without quotes); I have only now realized that it's there but I believe it wasn't always there. I definitely didn't (knowingly) create it. Does anybody else have such a directory?

The strange part is that it contains just copies of, and hard links to, EVERYTHING on the hard drive!! There is a copy even of this "rm" directory---and it contains (you guessed it) further copies; there are at least 13 layers deep of these nested copies! I made a text file listing the contents of the outermost "rm" directory and the text file alone is over 400 MB!! There are over a million items in there.

Does anybody have any idea where this came from, what created it, and whether I can delete it??

Searching the web is frustratingly futile because of course I get millions of results discussing how to use the rm command, etc, etc. So if anybody could help I'd be very grateful!

This is Ubuntu Natty, 64 bit (Ubuntu Studio actually but I doubt that matters).

---

### Post by matt_symes on 2011-10-18
Hi

What's the full path for this directory ? A quick search on my Oneiric install did not find that directory only the rm executable.

```
matthew@matthew-Aspire-7540:~$ locate -bi '\rm'
/bin/rm
matthew@matthew-Aspire-7540:~$ 
```Sounds like it may be a find command gone awol maybe ?

Kind regards

---

### Post by ofnuts on 2011-10-18
> **youWho said:**
> I have a directory in my home folder called "rm" (without quotes); I have only now realized that it's there but I believe it wasn't always there. I definitely didn't (knowingly) create it. Does anybody else have such a directory?

The strange part is that it contains just copies of, and hard links to, EVERYTHING on the hard drive!! There is a copy even of this "rm" directory---and it contains (you guessed it) further copies; there are at least 13 layers deep of these nested copies! I made a text file listing the contents of the outermost "rm" directory and the text file alone is over 400 MB!! There are over a million items in there.

Does anybody have any idea where this came from, what created it, and whether I can delete it??

Searching the web is frustratingly futile because of course I get millions of results discussing how to use the rm command, etc, etc. So if anybody could help I'd be very grateful!

This is Ubuntu Natty, 64 bit (Ubuntu Studio actually but I doubt that matters).
Given the name, I would still place my bets on a user error or a rogue script.

Normally you can: "rm rm/*" to remove all the links it contains (will only remove first-level links), and then "rmdir rm".

---

### Post by youWho on 2011-10-18
> **matt_symes said:**
> Hi

What's the full path for this directory ? A quick search on my Oneiric install did not find that directory only the rm executable.

```
matthew@matthew-Aspire-7540:~$ locate -bi '\rm'
/bin/rm
matthew@matthew-Aspire-7540:~$ 
```Sounds like it may be a find command gone awol maybe ?

Kind regards

Hi. Thanks for your quick comments. The path to that directory is: /home/<my_user_name>/rm
(I have a separate /home partition by the way.)

Especially strange is that even stuff from the / partition is in there!! For example I just checked with "stat" the version of bash (!) that's in there (as a hard link) and it says that there are 14 links to the file, corresponding I guess to the 13 layers deep of nested "rm" folders I counted, plus presumably the original copy of bash. This is too bizarre.

I'm not gonna say I'm a geek gnu/linux expert, but I'm extremely sure I did not somehow, even accidentally, create that directory with all of its contents. Yes I've written and use a few scripts but none would be capable of creating all those hard links recursively in a folder like that, I seriously think not anyway.

***In any case, if you kind folks are saying that you don't have such a directory, and that it's definitely NOT something standard with Ubuntu, then I'll go ahead and delete it.*** But please do let me know if this sounds like a bad idea... (Thanks again.)

---

### Post by Jonathan L on 2011-10-18
> **youWho said:**
> Hi. Thanks for your quick comments. The path to that directory is: /home/<my_user_name>/rm
...
***In any case, if you kind folks are saying that you don't have such a directory, and that it's definitely NOT something standard with Ubuntu, then I'll go ahead and delete it.*** But please do let me know if this sounds like a bad idea... (Thanks again.)

Hi 

It's definitely not a standard thing.  I'd just take a look at the the ownership with ls -l, and I'd fsck your disk to make sure it's not something really wrong.  Then I'd delete them.

Hope that helps

Kind regards,
Jonathan.

---

### Post by youWho on 2011-10-18
> **Jonathan L said:**
> Hi 
It's definitely not a standard thing.  I'd just take a look at the the ownership with ls -l, and I'd fsck your disk to make sure it's not something really wrong.  Then I'd delete them.


Checking ownership with:
# find /home/<me>/rm \! \( -user me -and -group me \) 
I see that everything inside is owned by me, though about 150 of the items have group ownership of "fuse", "audio" or "dip". I don't know what "dip" is but it all seems safe to delete, seems to me. I forced fsck by:
# sudo touch /forcefsck
and rebooted. Now I've temporarily just moved that odd folder into a folder away from where it was, to see if all is otherwise well; if so I'll trash it.

Thanks again everybody for your help.

---

