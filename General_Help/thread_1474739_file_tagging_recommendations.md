---
title: "file tagging recommendations"
date: 2010-05-06
forum: General Help
---

### Post by kokoshmusun on 2010-05-06
I'm not happy with the hierarchical (folders) way of organizing my files.  I need a file-tagging system.  I just want to tag my files, store them in the same folder, and bring up the ones that have a certain tag or a set of tags.  That's all.

I don't really need it to apply to email or anything else, just physical files (images, music, pdf, docs, etc.).

Can you recommend some tools to get me started?*  Thanks in advance...*

---

### Post by kokoshmusun on 2010-05-08
No reply, but I found a good discussion that points to some solutions, I'm posting it for anyone interested:

[http://superuser.com/questions/81563/whats-a-good-solution-for-file-tagging-in-linux](http://superuser.com/questions/81563/whats-a-good-solution-for-file-tagging-in-linux)

Here's another:

[https://blueprints.launchpad.net/ubuntu/+spec/tag-based-filesystem](https://blueprints.launchpad.net/ubuntu/+spec/tag-based-filesystem)

---

### Post by Ixtao on 2010-05-08
I'm exactly in the same need.. This would be perfect;

[http://www.youtube.com/watch?v=QQ5YyMsLtyE](http://www.youtube.com/watch?v=QQ5YyMsLtyE)

But somehow an hour of trying to get it didn't do it for me.. What I found out is you can get the best working Tracker here

[https://launchpad.net/~tracker-team/+archive/tracker-unstable]("https://launchpad.net/%7Etracker-team/+archive/tracker-unstable")

Tracker claims integration support for nautilus on[ their website]("http://projects.gnome.org/tracker/documentation.html");

> There are Tracker plugins     for [Totem]("http://projects.gnome.org/totem/"), [Nautilus]("http://projects.gnome.org/nautilus/")     and the GTK+ File Chooser.Then @[ the nautilus website]("http://live.gnome.org/Nautilus/Extending") it says See also;

> [Tracker  Tag]("http://svn.gnome.org/viewcvs/tracker/trunk/python/nautilus/tracker-tags-tab.py?view=markup"), adding Tags to files in [Tracker]("http://www.gnome.org/projects/tracker/")Yes, I want it!! but how to do it.. OMG??

So I have this tracker tag extention for nautilus, but the [gnome documentation library]("http://library.gnome.org/users/user-guide/unstable/nautilus-extensions.html.en") doesn't go further then saying 'Nautilus extensions are typically  installed by your system administrator.' 

Tomorrow I will have a look at[ this post]("http://brib.wordpress.com/2007/10/18/howto-enable-tagging-in-ubuntu-gutsy-in-4-simple-steps/") and [this post ]("http://blog.ibeentoubuntu.com/2009/04/fix-your-crap-1-want-tracker-support-in.html")and try again..

---

### Post by kokoshmusun on 2010-05-08
I played with Oyepa today but it messed up my system a bit (like gnome do) and the GUI was horrible.  But if you wanna give it a shot:

[http://pages.stern.nyu.edu/~marriaga/software/oyepa/](http://pages.stern.nyu.edu/~marriaga/software/oyepa/)

Tracker has promise from what you said. It's a bit beyond me, but please post here if you get progress on getting it to tag.

I found something called SCAN on sourceforge.  Looks decent, installation was easy because it's Java.  Will try it soon:

[http://scan.sourceforge.net/](http://scan.sourceforge.net/)

---

### Post by Ixtao on 2010-05-13
A more detailed video of why we want to tag our files; [http://www.youtube.com/watch?v=XFiLjB9UNaA](http://www.youtube.com/watch?v=XFiLjB9UNaA)

I'm so far I figured out [the nautilus extention]("http://svn.gnome.org/viewcvs/tracker/trunk/python/nautilus/tracker-tags-tab.py?view=markup") simply works when you put in in the designated folder. I didn't see a way to download the text from the link so I attached it to this post. Put the file in $HOME/.nautilus/python-extensions and restart nautilus or the computer. I was assuming it didn't work at first cause I expected the feature to show up in the sidebar 'Information' like in [the clip]("http://www.youtube.com/watch?v=QQ5YyMsLtyE"). But after a while I discovered[ another video]("http://www.youtube.com/watch?v=IIjlYArPy68") and opened the the Properties window of a file and there it was.. the tag-tab. access it directly from the right-click menu. So now there's a way to add one or multiple tags to files and folders. 

Now how do I get an overview of the files that belong to a tag? The search bar applet  for finding content stored in Tracker doesn't show the files with the tag I search for.

---

### Post by Ixtao on 2010-05-14
> Now how do I get an overview of the files that belong to a tag? The search bar applet  for finding content stored in Tracker doesn't show the files with the tag I search for.

Ah, it's because of [a bug]("https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/397784") *sigh*

---

### Post by djpemberton on 2010-06-07
I have been searching all over for a tagging solution. So far I could find nothing to work for me. I'm using Ubuntu 10.04, both 32 and 64 on various computers. Though I have installed everything I have been told to, and placed the script everywhere I possibly could, I cannot get the Nautilus extension to work. It does nothing for me.

Have you tried SCAN yet?

I do not know much about all of this, only that I desperately want to be able to utilize file tagging more easily.

Has anybody found a solution yet? Particularly for 10.04?

Thank you.

---

### Post by djpemberton on 2010-06-07
Well,

as I was typing my last message, I was also installing the latest unstable Tracker from [https://launchpad.net/~tracker-team/+archive/tracker-unstable](https://launchpad.net/~tracker-team/+archive/tracker-unstable)

It seems that it automatically integrates tagging into Nautilus. I haven't tested it much yet, but it looks promising to me. Has anyone else tried it?

---

### Post by kokoshmusun on 2010-06-08
Depending on your exact needs, SCAN seems like it can be the solution or part of the solution.  It's not a bad piece of software, give it a try.  Tracker is probably more powerful and system-wide.  Let me know if you can get it to work well and I might begin to use it.

---

### Post by djpemberton on 2010-06-08
While I am able to tag documents from Nautilus now, I cannot figure out how to search based on tags in the gui, which makes tagging rather useless for me. Of course, I can search for them in the terminal, providing me with a list, but it would be so much more handy in the gui. I'm sure this will clear up with more development, but I would like to figure something out now.

Any tips? Searching from Nautilus or Tracker using "tag:[tagname]" or "tag:tagname] doesn't give any results, though I do have tagged items.

SCAN seems like it would be a good tool, but it can't handle encrypted pdf's, which makes it much less useful for me.

---

### Post by djpemberton on 2010-06-09
How would one usually search for tags in the tracker gui?

---

### Post by Ixtao on 2010-06-13
Like I mentioned in post #6 it seems to be a bug.

---

### Post by t.rei on 2010-06-16
I feel dump... installed tracker and... well nothing. It doesn't start indexing and tracker-control only states "Found 190 PIDs&#8230;"

while tracker-status states something about not being able to establish a dbus connection to tracker.

---

### Post by djpemberton on 2010-06-18
Yes, Tracker isn't yet able to search based upon tags in gui. Hopefully that gets worked out soon. There doesn't seem to be another option for me right now.

---

### Post by yuno.33 on 2010-11-11
guys, i cannot follow :(
i have the same need as thread starter states at the first post. along the way, i figured the tracker can do partial trick. but after i install tracker from ubuntu software center, i can't do a thing. can somebody sum it for me how to make my nautilus able to organize files/folders based on tags?

update
alright, i install tracker from ppa, unstable, just now
restart nautilus, and got tabs at right-click menu and tags tab at properties window
i can tag files and folders
but i cannot arrange files and folders according to its tags
(inability to search files/folders upon its tag is already mentioned, so i don't have to repeat)
can somebody help me to arrange things according to its tags?

---

