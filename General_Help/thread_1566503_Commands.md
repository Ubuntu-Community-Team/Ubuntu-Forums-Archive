---
title: "Commands"
date: 2010-09-02
forum: General Help
---

### Post by stalkingwolf on 2010-09-02
Where can I find a List of general commands for Ubuntu?  Specifically 9.10 and 10.04.

---

### Post by CharlesA on 2010-09-02
It's not the best, but it should get you a little familiar with the basic commands.

[http://www.computerhope.com/unix.htm](http://www.computerhope.com/unix.htm)

---

### Post by oldfred on 2010-09-02
Are you looking for command cheat sheets?

Commands (Google has many more)
[http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/](http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/)
[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)
[http://www.scottklarr.com/topic/115/linux-unix-cheat-sheets---the-ultimate-collection/](http://www.scottklarr.com/topic/115/linux-unix-cheat-sheets---the-ultimate-collection/)

Or info on Ubuntu:
[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Ubuntu Documentation:
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
[https://help.ubuntu.com/10.04/index.html](https://help.ubuntu.com/10.04/index.html)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[http://www.linuxlinks.com/article/20090405061458383/20oftheBestFreeLinuxBooks-Part1.html](http://www.linuxlinks.com/article/20090405061458383/20oftheBestFreeLinuxBooks-Part1.html)

---

### Post by sikander3786 on 2010-09-02
Many useful links on this page.

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by stalkingwolf on 2010-09-04
Thank you all. I havent had a chance to check the links out, (life intruded)
but hope to this weekend.

---

### Post by stalkingwolf on 2010-09-08
i am using super OS based on 9.10.   What i need is the command to reconfigure the graphics card.  I have a unichrome pro ipa that has to be manually configured.

I have the command for 8.04 but nothing since

---

### Post by Iowan on 2010-09-08
Basic commands don't change very often - although I occasionally stumble across a "new one" (to me anyway...). What was the 8.04 command?

---

### Post by bodhi.zazen on 2010-09-08
[http://manpages.ubuntu.com/](http://manpages.ubuntu.com/)

You can add a search bar to ff (and other browsers).

---

### Post by stalkingwolf on 2010-09-11
Thanks Everyone. I have check the links, add the search plugin.  I still have had no luck finding the command i need,  probably havent hit the right
syntax yet.

---

### Post by stalkingwolf on 2010-09-17
In 8.04 i used this command to manually configure my graphics adapter.
sudo displayconfig-gtk

I would like to do the same thing in 9.10 and 10.04.  How do i do it?

---

### Post by bodhi.zazen on 2010-09-17
> **stalkingwolf said:**
> In 8.04 i used this command to manually configure my graphics adapter.
sudo displayconfig-gtk

I would like to do the same thing in 9.10 and 10.04.  How do i do it?

xorg has significantly changed and displayconfig-gtk has not been maintained for 2 years (an as far as I know will no longer work with the new xorg).

I suggest you start a new thread (rather then posting on a thread with a title of "commands"). Be sure to include your hardware (videocard, monitor, desired resolution, etc).

---

### Post by stalkingwolf on 2010-09-18
I was under the impression that multiple threads on the same topic was verbotten on this site.

---

### Post by CharlesA on 2010-09-18
> **stalkingwolf said:**
> I was under the impression that multiple threads on the same topic was verbotten on this site.

It's a different issue, so it would need a different thread. :)

---

### Post by stalkingwolf on 2010-09-19
im not sure how its a different issue.  I am trying to find a command.
and fwiw i was asked what the command was i used in 8.04.

the staff comments here have pretty much killed any chance of getting an answer here anyway.

thanks for the help and support.

---

### Post by NFblaze on 2010-09-19
Looks like that has been removed from all versions since Gutsy, although, the PPA and source code for it is still available here [https://launchpad.net/~displayconfig-gtk/+archive/ppa](https://launchpad.net/~displayconfig-gtk/+archive/ppa) I think we all just use gnome-display-properties now.

Also, at this point you could also email the former maintainer and ask him what deprecated it. Good Luck.

---

### Post by stalkingwolf on 2010-09-21
so what you are saying is that since 8.04 there is no way to manually configure a video display adapter.  either it works or it dont.  

Sounding more and more like windows every day.

---

### Post by bodhi.zazen on 2010-09-21
> **stalkingwolf said:**
> so what you are saying is that since 8.04 there is no way to manually configure a video display adapter.  either it works or it dont.  

Sounding more and more like windows every day.

No,you have the wrong impression.

It depends on your hard ware.

You can write an xorg.conf yourself and it will work.

The specific graphical tool you are asking about is no longer maintained and is not available. That is not the same as concluding "there is no way to manually configure a video display adapter".

---

### Post by stalkingwolf on 2010-09-24
I knew that tool no longer worked before 8.10 was out of beta.  the question was was nothing done as a simple replacement for it?

It would seem that this os is going backwards.

---

### Post by bodhi.zazen on 2010-09-24
> **stalkingwolf said:**
> I knew that tool no longer worked before 8.10 was out of beta.  the question was was nothing done as a simple replacement for it?

It would seem that this os is going backwards.

Aye. In this case it was X org, so it is this way now on all versions of Linux.

In general, X works better "out of the box" and there are less threads with complex configuration of xorg.

In the event X fails though, it is a pain, and xorg.conf is depreciated, so sometimes even editing xorg.conf does not fix the problem.

If you want support, start a thread, or report a bug (on launchpad). Be sure to include more details on your hardware (videocard, monitor).

---

### Post by stalkingwolf on 2010-09-25
i have had little luck with launch pad or reporting bugs but i will try it. thank you.

I would seem that this os is becoming as propritary as windows.

---

