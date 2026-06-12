---
title: "Why is &quot;umount&quot; not named &quot;unmount&quot;?"
date: 2010-05-12
forum: General Help
---

### Post by pytheas22 on 2010-05-12
I've always wondered why the "umount" command isn't "unmount" instead.  Do any Unix veterans know if there's a reason, beyond saving a keystroke?

---

### Post by CharlesA on 2010-05-12
Thought you could use either commands.

EDIT: Scratch that. Just tried unmount and it asked if I meant "umount"

I use umount all the time, and don't even think about it anymore.

---

### Post by pytheas22 on 2010-05-12
I don't remember any Linux distribution where "unmount" was recognized.  I assume there's some historical reason for this, but I'd love to know what it is!  I assume that if they were just looking to make the command faster to type, they would have used something like "umnt," so it doesn't make sense that they took out the first "n" just to save a keystroke.

---

### Post by CharlesA on 2010-05-12
Well I guess it kinda makes sense, since you mount drives with the mount command and unmount them with the umount command.

I did fine some old IBM documentation that said that umount/unmount were both usable. Maybe that's changed since then.

---

### Post by lisati on 2010-05-12
> **CharlesA said:**
> 
I did fine some old IBM documentation that said that umount/unmount were both usable. Maybe that's changed since then.
I've seen stranger. On an IBM mainframe I once used, the "F" command at the operator's console was an abbreviation for "modify", which in turn meant "pass the following text info to a job/program"

---

### Post by lvleph on 2010-05-12
I am going to guess that it has to do with saving space.

---

### Post by rnerwein on 2010-05-12
hi
if you want to call umount --> unmount too. use: sudo ln /bin/umount /bin/unmount 
this will cost you only a entry in the directory ( because of the same inode  ).
and about the reason why it's not called "unmount" --> umount is shorter to type :-)  :-)
ciao

---

### Post by bville09 on 2010-05-12
Maybe it was something to do with not being able to have the same two characters in a command, or maybe a command character limit or something?

Interesting thing, never gave much thought to it, but when I was first starting out with linux (and FreeBSD especially) I was extremely annoyed at why they didn't just name it "unmount" anyway. Seems like a lot more logical thing to have than "umount".

---

### Post by maedox on 2010-05-12
umount is faster to type than unmount. Just try it.

And I'm sure there are worse examples. Open a terminal and hit Tab a couple of times, then y and take a look.

---

### Post by koostudios on 2010-05-12
How much faster is unmount that umount... one character - maybe if you're doing it multiple times. I'm sorry but I'm very much intrigued about this umount thing :) I would laugh if it was simply a typo from ages ago that we're still using now. :)

---

### Post by bville09 on 2010-05-12
> **maedox said:**
> umount is faster to type than unmount. Just try it.

And I'm sure there are worse examples. Open a terminal and hit Tab a couple of times, then y and take a look.
Ha! That's so funny. I never knew you could do that. Good thing it limits them to one page, otherwise the whole computer would die. I wonder if it works in BSD or just linux?

I also attempted to google the history of the command, but couldn't find anything about it. Very curious also.

---

### Post by bumanie on 2010-05-12
I read that when unix was all cli, it was decided to use umount to save on some typing! This may have been an 'old-wives tale' - I can't be sure.

---

### Post by maedox on 2010-05-12
As far as I know the keyboard is layed out the way it is to combat keys sticking together on an old fashioned typewriter. But I think there has to be some thought in terms of quick typing. Moving one finger from 'n' to 'm' is ineffiecient, as is typing words like security and trying because the keys are so close together (and your mind gets all screwed up over the placement of keys). I usually type fairly fast, and the difference in typing unmount and umount is not very big, but it is noticeable.

---

### Post by iponeverything on 2010-05-12
> **pytheas22 said:**
> I've always wondered why the "umount" command isn't "unmount" instead.  Do any Unix veterans know if there's a reason, beyond saving a keystroke?

This is funny :)

It is all about the keystrokes! Most of us UNIX guys started out as touch typist and the keystrokes add up quickly. I am sure Benjamin Franklin would approve! 

cp
mv
ls
rm
ar
as
at
bc
[..] and many more [http://people.cs.uchicago.edu/~ahiorean/two-letter-commands.html](http://people.cs.uchicago.edu/~ahiorean/two-letter-commands.html)

---

### Post by ronnielsen1 on 2010-05-12
I've wondered this myself. They almost typed the whole word in. I think it was a typo and they went with it.

---

### Post by t0p on 2010-05-12
I did [a bit of googling]("http://bit.ly/bAHnK2") and couldn't find an explanation; so I'm going to make a little guess: I think it's a hangover from the days when computer resources were far more scarce and valuable than they are today.  Back then, omitting that "n" might have represented a saving worth having.  Nowadays, that extra character makes little/no difference.  But in days of yore, when computers were tiny creatures (in a big case) that "n" could have made all the difference.

I'm probably wrong, and a [touch more googling]("http://bit.ly/bAHnK2") may reveal the truth.  But I think my explanation seems plausible.  So unless anyone wants to prove me wrong: I'm right, and I'm accepting kudos through PMs.  Expressions of thanks in this thread are also welcome.  :p

---

### Post by John Bean on 2010-05-12
> **iponeverything said:**
> This is funny :)

It is all about the keystrokes! Most of us UNIX guys started out as touch typist and the keystrokes add up quickly. I am sure Benjamin Franklin would approve! 

cp
mv
ls
rm
ar
as
at
bc
[..] and many more [http://people.cs.uchicago.edu/~ahiorean/two-letter-commands.html]("http://people.cs.uchicago.edu/%7Eahiorean/two-letter-commands.html")

Ok, so why isn't umount just "um" then?

The OP was asking why it was "umount" rather than "unmount" not about all the 2-char commands that exist.

---

### Post by iponeverything on 2010-05-12
> **John Bean said:**
> Ok, so why isn't umount just "um" then?

The OP was asking why it was "umount" rather than "unmount" not about all the 2-char commands that exist.

The point is to save a keystroke. The point in the showing the 2-char commands, is to better illustrate keystroke saving obsession. That said, 1 search in google found this to contradict my theory:

> Because memory and CPU power were at a premium in those days, UNICS (eventually shortened to UNIX) used short commands to minimize the space needed to store them and the time needed to decode them - hence the tradition of short UNIX commands we use today, e.g. ls, cp, rm, mv etc.

From Here: [http://www.doc.ic.ac.uk/~wjk/UnixIntro/Lecture1.html](http://www.doc.ic.ac.uk/~wjk/UnixIntro/Lecture1.html)

Just found this additional information:
> Unix&#8217;s Short Commands &#8211; ls, cp, &#8230;

Wow! Okay, I finally heard the best explanation as to why Unix uses ls instead of list, or rm instead of remove.

In the past techies would say that these commands had short names because back in 1965 or so when all of this stuff was created, memory and disk were expensive and so they did everything to they could do to save space by shaving letters where they could.

But that didn&#8217;t answer questions for me like mount, umount, cpio, sleep, etc. My personal belief was that PhDs don&#8217;t really like typing and so why make the command longer if you don&#8217;t have to. So the commands were shortened just for speed. The designers never really saw Unix taking off like it did. Unix was written by PhDs for PhDs so what we might consider normal today wasn&#8217;t written for back in 1968. For example when you remove a file on Unix, it just does it; whereas on other operating systems it will ask you if you really want to remove it. After you say yes it will say &#8220;filename removed&#8221;. Unix doesn&#8217;t do that.

So why are these commands so short? Modems.

Yes, modems. Back in 1969 modems ran around a top speed of 150 baud. That is about 1000 times slower than internet access at home today. Imagine taking 30 minutes just to wait to see google&#8217;s home page. That&#8217;s what it would have been like back then if there were websites. Just a small picture would take 3 hours to see.

So common activities like moving files, deleting files, or duplicating files could be done faster if less data is traveling from the terminal to the server. These commands were done a lot. A lot more than most commands, and so to hasten data travel across slow modems copy, list, and remove were made cp, ls, and rm.
From Here: [http://jordanteam.com/blog/?p=18](http://jordanteam.com/blog/?p=18)

Now I just need find a reason as to why the English always seem so cranky. ;)

---

### Post by John Bean on 2010-05-12
So I repeat: why isn't it just "um" if space was so important?

If "remove" was abbreviated to "rm" it wouldn't be unreasonable for "unmount" to become "um" - but it became "umount" instead. There has to be a more convincing reason than saving one character when they could have saved five.

---

### Post by r m h on 2010-05-12
> **John Bean said:**
> So I repeat: why isn't it just "um" if space was so important?

If "remove" was abbreviated to "rm" it wouldn't be unreasonable for "unmount" to become "um" - but it became "umount" instead. There has to be a more convincing reason than saving one character when they could have saved five.

As the previous poster mentioned, it was all about the frequency of the command and the number of characters for that command.  Mounting and Unmounting filesystems was VERY UNcommon back then, so the penalty of the extra 4 characters wasn't an issue.  

We didn't have auto-mounting of filesystems back then, nor did we have point and click GUIs with all the functionality we do today.

We didn't have USB or firewire back then, mounting a filesystem back then meant either mounting a 9" tape, a very large highly expensive hard drive, or, as the years went by, a primitive network filesystem.

(perhaps your paradigm hasn't shifted enough?)

---

### Post by 3rdalbum on 2010-05-12
What about 'passwd'?

---

### Post by pytheas22 on 2010-05-12
Thanks to all of you who have replied.  I still don't feel very convinced that the peculiarity has to do with saving a keystroke, however.  If they wanted to save keystrokes, the command should have just been "um," or at least "umnt."  And if they didn't care about saving keystrokes because the command was not used frequently enough, then why not just use "unmount" without cutting out a single letter?

The suggestion that the first "n" was removed because it makes the word difficult to type quickly is interesting, but not really convincing, I think.  Is there evidence to back up the idea that keys that are close together are difficult to type sequentially?  And even if that is true, it seems like the unmount command would not be used frequently enough for this to be a real issue.

Another thought: why have a separate command for unmounting at all?  Why not just pass an argument to "mount" in order to unmount, such as "mount -u"?  After all, that's how you would remount a file system; there's no separate "rmount" command...

---

