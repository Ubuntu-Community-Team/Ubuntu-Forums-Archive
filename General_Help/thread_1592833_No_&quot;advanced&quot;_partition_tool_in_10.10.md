---
title: "No &quot;advanced&quot; partition tool in 10.10?"
date: 2010-10-11
forum: General Help
---

### Post by rastoboy on 2010-10-11
I was installing 10.10 for the first time on a new machine, and it doesn't appear to have an "advanced" partition tool in the setup.

Or is it carefully hidden?

This is madness...why should not an "advanced" user be able to specify/resize partitions at will?

---

### Post by CharlesA on 2010-10-11
It's there. It's at the same place where you pick how you want to install Maverick - side-by-side, etc.

---

### Post by rastoboy on 2010-10-11
Thanks for that, I wasn't as thorough as I could have been.

I did see that, but I couldn't resize the ntfs partition that filled the whole drive.

---

### Post by CharlesA on 2010-10-11
Normally, you'd resize the partition before you run the install, or just select the "side-by-side" option.

---

### Post by rastoboy on 2010-10-11
Would you normally resize the partition before installing?  I wouldn't.

The side-by-side does not give you any options about partition sizing (unless I missed it).

I really feel the partition tool is crippled, and replaced with very nice looking but less capable interface.

I normally don't complain about stuff and am insufficiently motivated to post--I felt this was important enough to actually post on the forms lol.

Sorry for being insufficiently precise in my first post tho.

---

### Post by CharlesA on 2010-10-11
I don't know where you are looking but it lets me resize an NTFS partition after I pick "advanced" then selected the partition I wanted to resize when click on "change."

EDIT: Same goes for ext3 and ext4. Should be the same for all supported partition types.

---

### Post by rastoboy on 2010-10-11
Siiigh.  Okay, I see what happened.  I didn't click on the partition.

Wow, what can I say? I'm kinda dumb.  I saw "change" greyed out, but it simply didn't occur to me to click on it, and I don't think that's an unreasonable requirement:popcorn:

I'm glad it's not messed up!

Sorry for wasting your time.

---

### Post by CharlesA on 2010-10-11
Glad you got it sorted. Don't forget to mark the thread as solved from thread tools.

---

### Post by oldfred on 2010-10-12
We typically recommend using windows tools to modify Vista & 7 partitions as after a resize they will at the minimum want to run chkdsk and sometime have other issues. After resizing windows then reboot several times to make sure windows is ok with its new smaller size.

Then you can install into the free space or use gparted to create your partitions in advance if you want more than the standard / (root) and swap that the installer defaults to.

---

### Post by CharlesA on 2010-10-12
Indeed. Especually since Vista and 7 can shrink the OS partition without the use of third-party tools. Granted if probably won't get as small as some want, but it's better then nothing.

---

### Post by rastoboy on 2010-10-12
@oldfred: I'm not so concerned about "people like us"--I spent the evening jacking around with a gparted boot cd and played with the latest Ubuntu installer afterward.  It's the newbs I (was) concerned about.

I've actually gotten a 60+ year old lady installing Ubuntu, and I'm convinced that as of about version 8.x Ubuntu truly became the best desktop OS in the world.  So I'm keen to see it continue to be installable by newbs.

It must be said that the "side by side" option does work well for those folks.

But yeah it appears perhaps I was a little too sleepy when I ran through it the first time. :guitar:

---

### Post by TheAnachron on 2010-10-12
I know this has been solved but you can run the live Ubuntu and install/use GParted.

---

