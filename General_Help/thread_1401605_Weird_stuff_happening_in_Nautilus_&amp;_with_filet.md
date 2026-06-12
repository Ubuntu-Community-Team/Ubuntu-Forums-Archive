---
title: "Weird stuff happening in Nautilus &amp; with filetypes"
date: 2010-02-08
forum: General Help
---

### Post by Objekt on 2010-02-08
I'm having some really odd problems with Nautilus.

The main one is that most of the time, files of various types are not assigned to be opened with the proper app, and I cannot assign an app.  I described this problem in another thread: 
> If I right click a .pdf for example, and select "Open With," the first two suggestions (Leafpad and gedit) are wrong. If I choose instead "Open with another program," I get a dialog with two tabs. One is "Recommended Applications" and is blank. The other is "All Applications." If I click "All Applications," instead of getting a list of apps or having the opportunity to choose one from /usr/bin, the entire dialog disappears abruptly. I'd say that's a "crash."
original thread: [http://ubuntuforums.org/showthread.php?p=8793761#post8793761]("http://ubuntuforums.org/showthread.php?p=8793761#post8793761")

The behavior of Nautilus also depends on how it's started.  If I start it by using any of the first 8 entries on the "Places" menu (Home Folder, Desktop, etc.), I see nothing but "unknown file type" icons (white rectangle with 1's and 0's) and have the problem described above when trying to open anything.

If I start Nautilus by choosing "Computer" or "Network" from the lower portion of the "Places" menu, I can browse into the same folders (Documents in my /home for instance) and Nautilus works properly.  .pdf, .wmv., etc. are recognized and open with an appropriate application when double-clicked.  I can choose to open a given filetype with more than one app, e.g. gedit or Leafpad for .txt files.  Nautilus also works properly when invoked from the command line, either run as user (nautilus) or superuser (gksudo nautilus).

If I choose anything else from the lower portion of the "Places" menu, such as mounted filesystems, again, filetypes aren't recognized, and I cannot assign an application to open a particular filetype.

So why is Nautilus broken, and how do I fix it?  

I can't recall having this problem with Thunar or Dolphin, so perhaps I'll install & use one of those instead.  However, I'm not sure how to make the "Places" menu work properly with anything other than Nautilus.

---

### Post by Objekt on 2010-02-09
Another oddity: when I run Nautilus from "Computer" or the command line, the list of apps I can open a file with is incorrect.  If I go to the list of available applications, there are multiple entries for most programs.  Okular appears a dozen times.  That can't be right, can it?

---

### Post by arrange on 2010-02-09
Try to simulate the crash and then have a look at *~/.xsession-errors*. Does it say anything?
You could also try the nautilus self-check option```
nautilus --check
```

If you see multiple programmes on the list, you can always use the *Remove* button (if I understood you correctly).

---

### Post by jamesisin on 2010-02-09
Sounds like your configuration file for Nautilus (in your profile) is likely to blame.

If you use Nautilus signed in as another user does it work correctly?  If so you may be able to blow out your profile and build another (depending upon how much configuring you have done).

Also, it would be nice to know if this has been happening since installation or if this was something that you evolved into.

---

### Post by Objekt on 2010-02-09
Good idea.  No one else uses my machine, so I haven't had occasion to try things under a different profile.

I can't say when the problems with Nautilus started.  I've only been using Ubuntu as my main OS for a couple of months, and I've been playing whack-a-mole with various other, higher-priority problems.  

Having said that, I guess I'm doing well overall, because I've fixed enough other stuff that I have a chance to work on "nice to have" things.  Like having the right app open when I double-click on a given file.

---

### Post by Objekt on 2010-02-09
Looks like it's the profile.  I created a brand new user, logged in, and Nautilus works fine there, regardless of how I start it.  So how do I wipe out my old Nautilus profile & create a new one?

---

### Post by jamesisin on 2010-02-09
There may be a better way, but this came quickly to mind:

1. copy off any important files
2. login as another user and delete broken user /home/ folder
3. login as user to auto-create /home/ folder

I think that will do it.

---

### Post by Objekt on 2010-02-09
> **arrange said:**
> Try to simulate the crash and then have a look at *~/.xsession-errors*. Does it say anything?

Yes, there's a whole boatload of stuff in .xsession-errors.  What should I look for?

---

### Post by Per Olav on 2010-02-10
Just a small update from my experience, this problem is as suspected related to the 64 bit version. 

If you, like me, were only using the 64 bit version to access all your precious RAM  >3 Gigs, then using the 32bit PAE kernel might also work for you. 

```

user@box:~$ uname -srvmpio
Linux 2.6.31-19-generic-pae #56-Ubuntu SMP Thu Jan 28 02:29:51 UTC 2010 i686 unknown unknown GNU/Linux

user@box:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7942       5999       1942          0        416       5026
-/+ buffers/cache:        556       7385
Swap:            0          0          0

```

---

### Post by Objekt on 2010-02-10
I've considered moving to 32-bit as well.  There's not really anything I do that *requires* the 64-bit kernel.  While it is true that the 64-bit kernel kicks the snot out of the 32-bit version at some tasks, they are not things I normally do (e.g. video encoding).  The most computationally-intensive thing I do is ripping DVDs to .iso files.

Running the 32-bit version of Ubuntu would make some things easier, for instance there would be no additional tinkering required for Ubuntuzilla to work.

Further adding to the Nautilus weirdness: the "hidden" .nautilus folder in my /home directory is completely empty.  Shouldn't there be some profile information there?

I'll have to look at the analogous location in the other user profile (the one I created to test just WTF was going on with Nautilus) to see whether it's empty, as well.  Nautilus works fine under that other profile, so I guess I could try copying the settings over to my main /home folder.

Haven't tried reinstalling Nautilus yet, but it might be easier than trying to switch to Dolphin/Thunar et al.

---

### Post by jamesisin on 2010-02-10
Still seems like ditching the old profile is the simplest route.

---

### Post by Per Olav on 2010-02-10
> **jamesisin said:**
> Still seems like ditching the old profile is the simplest route.

didn't work for me

---

### Post by jamesisin on 2010-02-10
> **Per Olav said:**
> didn't work for me

The OP has confirmed using a different profile does not exhibit the problem.  Deleting the old profile and creating a new one should fix the issue.

---

### Post by Per Olav on 2010-02-11
I am not sure what you mean here, but this is what i tried:

- Created a new user with administator rights (tempuser)
- Logged out my old (failing) user
- Logged in as the new tempuser; confirmed that things still does not work
- Deleted the home folder of the old user.
- Logged out as the tempuser
- Tried to log in as my old user to autocreate new home directory as described here; this did not work, I was not able to log in at all. 

Did I misunderstand something?

---

### Post by Objekt on 2010-02-11
I think you understand, you are just having a different problem than I was.

I created a new user profile ("testmeat"), logged out of my usual profile, then logged in as "testmeat."  When logged in as testmeat, I experience none of the problems with Nautilus that prompted me to start this thread.

One suggested fix: I would move all my personal stuff in /home to the new user's profile, and - presumably - not have any more Nautilus problems, while still having everything else set up the way I'm used to (Thunderbird, Firefox, etc.).  The only exceptions will be any applications that rely on hard-coded links, e.g. expecting "objekt" as the user name instead of "testmeat."

Really, I would rather just reset Nautilus to its defaults, but I haven't yet found any hint of a way to do that.

---

### Post by Objekt on 2010-03-02
OK, I finally figured out what was happening.  At some point I installed the Lightweight X Desktop Environment (LXDE), which uses pcman as its file manager.  Somehow I got a hybrid pcman/Nautilus setup, where some menu choices resulted in opening Nautilus, while others opened the folder in pcman.

The interfaces were similar enough that I didn't notice what was going on until I opened the Help->About menu in both.  

I removed pcman, and now the problems I started this thread about are entirely resolved.

---

### Post by jamesisin on 2010-03-02
Great news.  Tough to decipher, no doubt.

---

### Post by Per Olav on 2010-03-04
I've found the source of my problem too, it was a faulty stick of RAM. I started noticing a lot of corrupted files when working with large ISO's, so I started to use a checksum on everything after a copy to confirm.

A quick memtest run shows me that one of my ram sticks was failing.

---

