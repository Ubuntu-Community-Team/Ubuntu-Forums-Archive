---
title: "Which version have I got?"
date: 2012-02-26
forum: General Help
---

### Post by Buster95 on 2012-02-26
A puzzle!
I "thought" I was using 11.10 with the Gnome Classic interface, but System Settings/System/Details says 12.04 LTS (see screen shot)
[IMG]/home/dexter/Pictures/Screenshot at 2012-02-27 10:31:11.png[/IMG].
I have never installed 12.04.

I then checked via a terminal. It assure me that I'm using 11.10 (see screen shot)
[IMG]/home/dexter/Pictures/Screenshot at 2012-02-27 10:37:49.png[/IMG]

Which is right? and why the difference?

---

### Post by howefield on 2012-02-26
Screenshot has gone awry, no one can see it here whilst it is still in your local home folder.

Use the paperclip icon to attach your screenshot to your post.

---

### Post by papibe on 2012-02-26
Could you post the result of this command?
```
lsb_release -a
```
Regards.

---

### Post by grahammechanical on 2012-02-26
I can tell you two things.

1) I have been using 12.04 since the end of November last year and at first System Info said it was 11.10 and it kept saying that for many weeks. After a while System Monitor started reporting 12.04 and it took many, many more weeks before System Info got around to saying it was 12.04. Now, just the other week System Info had its name changed to Details.

2) I have just run my standard 11.10 install. System Info is still called System Info and it is still saying 11.10.

What PPAs do you have in your System Sources?

Some people on 11.10 like to have the very latest bits and pieces. Such as Linux kernel 3.2 instead of 3.0. Or Unity 5 or the latest Gnome shell. These are bits coming in 12.04.

Have you done anything like that? It could be (that means that I am guessing) that these packages have dependencies that are pulling in other packages that are meant for 12.04 and that is how you have got a Details Utility and enough of 12.04 for the Details utility to label the OS as 12.04.

Regards.

---

### Post by Buster95 on 2012-02-26
> **howefield said:**
> Screenshot has gone awry, no one can see it here whilst it is still in your local home folder.

Use the paperclip icon to attach your screenshot to your post.

attached
[ATTACH][ATTACH]213349[/ATTACH][/ATTACH]

---

### Post by Buster95 on 2012-02-26
> **grahammechanical said:**
> I can tell you two things.

1) I have been using 12.04 since the end of November last year and at first System Info said it was 11.10 and it kept saying that for many weeks. After a while System Monitor started reporting 12.04 and it took many, many more weeks before System Info got around to saying it was 12.04. Now, just the other week System Info had its name changed to Details.

2) I have just run my standard 11.10 install.System Info is still called System Info and it is still saying 11.10.

What PPAs do you have in your System Sources?

Some people on 11.10 like to have the very latest bits and pieces. Such as Linux kernel 3.2 instead of 3.0. Or Unity 5 or the latest Gnome shell. These are bits coming in 12.04.

Have you done anything like that? It could be (that means that I am guessing) that these packages have dependencies that are pulling in other packages that are meant for 12.04 and that is how you have got a Details Utility and enough of 12.04 for the Details utility to label the OS as 12.04.

Regards.

You may be right.
Until recently, I used the "vanilla" sources only and a very limited software suite. Then, I lost the menu bar indicators, some keyboard shortcuts, Deja Dup backup and Gimp after a routine update.

I was compelled to use some other repositories to get some of those functionalities back.

---

### Post by Lisiano on 2012-02-26
That's... Weird, to me it seems you have 11.10. Take a look in /etc/apt/sources.list
If almost everything says
```
deb some-address/ubuntu oneiric main multiverse universe extra 
```
Then you have 11.10, if not, then whatever it has instead of oneiric.

EDIT: If you have PPAs, make sure you aren't using 12.04 PPAs as they can mess up (They are in /etc/apt/sources.list.d/)

---

### Post by Buster95 on 2012-02-26
> **Lisiano said:**
> That's... Weird, to me it seems you have 11.10. Take a look in /etc/apt/sources.list
If almost everything says
```
deb some-address/ubuntu oneiric main multiverse universe extra 
```
Then you have 11.10, if not, then whatever it has instead of oneiric.

EDIT: If you have PPAs, make sure you aren't using 12.04 PPAs as they can mess up (They are in /etc/apt/sources.list.d/)

PPAs all "claim" to be Oneric (see attachment)
[ATTACH]213353[/ATTACH]

---

### Post by Lisiano on 2012-02-26
Then it looks like you are on 11.10 and one of those PPAs might have backported 12.04s System Info to 11.10.

At least that what it looks like to me, wait for others to voice their opinion.

---

