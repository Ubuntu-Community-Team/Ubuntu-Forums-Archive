---
title: "OpenOffice crashed, document erased.  Due tomorrow!"
date: 2011-02-27
forum: General Help
---

### Post by 0_irishboy_0 on 2011-02-27
I need help!:confused:

 
My computer froze while I was typing a paper for school.  Everything had completely froze, could not exit out of OO, open a terminal, anything.  I was forced to do a hard reboot since I have been working on this paper all week and knew there was a copy on the hard drive, even if the work I had done tonight was not saved. 

I restarted my computer, clicked on OO.  It asked me if I wanted to recover the file I was working on.  I clicked yes.  A window popped up asking to enter ASCII Filter Options.  I left everything on the default settings (Unicode (UTF-8), Liberation Serif, English (USA)).  The file is now completely blank.  There also was not a copy saved to the backup folder.



Is it possible to recover any of the text in the document or was it corrupted during the hard reboot?  It is over 7 pages long and due tomorrow morning, so hopefully you guys can help me out!


EDIT: I should probably specify that I'm using 3.2.

---

### Post by jeremyjjbrown on 2011-02-27
Please back up your work every 20-30 minutes and you'll never suffer this issue again.

If you just can't make yourself back up use Google docs and they will do it for you.

---

### Post by amsterdamharu on 2011-02-27
if you know the name of the file or even part of the file you can have Ubuntu search for it with the following commands:

```
sudo updatedb
locate mydocument
```

How big is the file and what happens if you open OO and not choose to recover? Then open the document as it is?

---

### Post by 0_irishboy_0 on 2011-02-27
The file is now renamed > .~lock.Lab 4 Questions.odt# and shows that the size is 0 bytes.  When I click on it, the ACSII Filter Options window comes up.

---

### Post by slooksterpsv on 2011-02-27
Well..... get working on the paper again, and save often. If the file is blank, it's not going to be recoverable it sounds like.

---

### Post by houseworkshy on 2011-02-27
That doesn't sound encouraging.  However as you know where the file was and what it was called take a look at the grep command by opening a terminal and entering "man grep" it's a searching command.  Then try searching for some phrase that is definatly in the document and probably not anywhere else on the system.  Try looking both in the place it was and in the backup areas.  It's a long time since I installed open office, so I could be wrong about this, but I have a vauge memory that the auto backup was enabled....you might get lucky.  Temporary files may be worth looking at too also your ram which is probably bubble memory though I'm not sure how it is done.  After that undelete software does exist and searching for "undelete" , in the repro's, should get it.  There are also rescue distros. 

There is a chance that you can get it but whether it is in time for your deadline is dubious.  If you can phone your tutor and explain in advance of turning up in the morning, maybe without the paper, they may be more forgiving, always worth letting people know. Maybe bang your head against it until it isn't too late to phone ( and re-write, amazing how fast one can work when the pressure is on...so don't despair  .. you have a backup of sorts in your mind already so the 2nd version won't take nearly as long as the first did. ), then ring.

I've often forgotten to back stuff up so now enable the auto backup  which remembers for me, only a tick in a box, then never again.  I don't mean to be tiresome with advice about what to do with doors on empty stables and wish you luck with getting the runnaway back.

Good luck and hurry

Second thought.  Rescue cd's take a long time, too long for this occasion, so don't bother with them for this occasion and only use undelete software if there is an option for specific folders/files, that also takes a while and if it needs to look at the whole disk then forget that too for now.

---

### Post by 0_irishboy_0 on 2011-02-27
Thanks for the quick replies.  Houseworkshy, I tried running man grep with no luck.  

I began retyping using Google Docs (thank you for the tip jeremyjjbrown) and I figure it will be a better use of my time trying to retype what I can rather than continue trying to recover.  My university has a pretty strict "computer issues are not an excuse" policy and actually has a section in the student handbook stating to save your work on multiple drives.  Maybe I should have listened, lolol.

Thanks anyway everyone!  Maybe when I get some time this week I will try to recover the file just for the hell of it and see if we can solve this issue.

And FYI, I'm using 10.10 64bit.

---

### Post by amsterdamharu on 2011-02-27
Did you try the commands I posted, let Ubuntu look for it maybe it'll find something

```
sudo updatedb
locate Questions
```You could try the trash bin in nautilus, maybe it's in there.
The file you refer to is a temporary file made when you edit the original document I think so where is the original document?

---

### Post by 0_irishboy_0 on 2011-02-27
Amsterdamharu, I was able to locate the document using that method.  My problem that I am having is that the document is still completely blank.  My guess is that the file was corrupted during the hard reboot, but I'm just taking a wild guess when I say that.

---

### Post by houseworkshy on 2011-02-27
By "man grep" I meant enter it in the terminal to open the manual page for the grep command.  If that didn't work it is not a good sign unless you deliberately removed the man pages previously, should be standard that it is there.
Time passes so maybe start rewriting very soon.  

You mentioned a freeze, that could happen again I suppose.  One way out of quite a lot of them is Alt +F2 this opens a run programs dialouge ( which you may want, system monitor for eg)  but what it also does is bypass some crashes and let you get menu bars back if you happened to be in full screen something when the freeze happened.  

As the pc is playing up play safe and don't go full screen with open office, maximise instead so you can get around oo and at the rest of the system if something goes boing.   Maybe try an update before working just in case whatever is wrong is fixed by it.

You could, as you don't really have time to mend a broken oo or java ( if it is just the application ) install abiword and use that instead in the hope that it is only an open office problem.  It's a good backup wp. 

Don't use too much time here but some other time maybe come back and try to find out what went wrong and how to fix it.

Google docs is ok sorry didn't properly read the above.  If you have trouble with google docs though ( which is basically a branded open office ) abiword is a lot lighter on system resources.  Good luck with the rewrite, I won't distract you further.  Make time to eat, brains need calories especially when ducking a nights sleep.

---

### Post by slooksterpsv on 2011-02-27
I'm sorry if my comment sounded harsh, at least with Google Docs, the document is in the "cloud" so-to-speak. And it does save a draft every so often (usually when you stop typing). I wish there was another way to get your hard work back, but it sounds like OpenOffice didn't actually save a backup.

Good Luck, and best Fishes.

---

### Post by amsterdamharu on 2011-02-27
> Amsterdamharu, I was able to locate the document using that method. My problem that I am having is that the document is still completely blank

You posted here that you found a file beginning with ".~lock", that is not the document nor is it a copy of the document. This is a file OO creates when opening the original document. My question is that if it didn't find the original and it's not in trash than how is it deleted?

Not only is it unlikely that the original file is deleted it is highly unlikely that the backup you made is deleted as well and they both or one of them don't show up in trash. If a system crash causes such things then it would indicate a damaged harddisk or filesystem and you would have many more files disappearing or be left with a system that won't even start anymore. 

If the file really isn't there anymore and not in trash then you could try to boot off a live CD and recover the file with the following commands:
```
sudo apt-get install testdisk
sudo photorec
```

Choose the partition where the document should be and see what it can recover. This might take a long time to finish and give you a lot of files. I am not sure how to use photorec but it's the program that recovers most file types as far as I know.

---

### Post by amsterdamharu on 2011-02-28
By the way the auto backup usually goes in /home/[COLOR=Red]your_user[/COLOR]/.openoffice.org/3/user/backup but since the locate command could not find it I assume it was deleted after a failed recovery and then closing Openoffice.

---

### Post by houseworkshy on 2011-02-28
Well whatever happened hass happened by now, hope it was ok.  On double checking I gave you some duf advice.  The idea behind using grep was that you could search for text within a file in case a copy existed with a differant name.  It seems that one can only do that with text files.  The odd thing is I remember useing something which would find the lot.  I tend to have a lot of documents lying around many of which are 0dt's.  I'd been sorting out old work and had had to search multiple files for specific chunks of text because I knew the contents I wanted but couldn't remember the titles.  It was probably something I'd put in.  So sorry about that.  Wish I remember what the thing was.
I hope that you either got it done or that the tutor was understanding.

---

### Post by Hagar Delest on 2011-02-28
In such case, check also the temporary folder of the system (see in OOo Tools>Options>OOo>Paths). If there are folders like sgmlf.tmp with a file having the same name inside, make a copy of that file, rename it in .odt and cross your fingers.

---

