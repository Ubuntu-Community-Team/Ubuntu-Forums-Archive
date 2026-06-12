---
title: "Nicotine Plus not openning"
date: 2010-05-27
forum: General Help
---

### Post by dogbin on 2010-05-27
Hello if someone could give me some help it would be appreciated

When I try to open Nicotine Plus, the computer thinks for a while and then nothing happens. N+ attempts to open and I see it appear on the panel and then it vanishes

I have tried uninstalling and reinstalling it to no avail. It also worked previously

Any help would be appreciated

Cheers

---

### Post by flipped on 2010-12-03
Hi,

I have exactly the same problem, and I also reinstalled Nicotine+ on my macbook. When i try to open the shortcut it appears in dock, but after a few seconds it disappears. Does anybody have a solution for me???


Thanks in advance!

---

### Post by gandaran on 2010-12-03
> **flipped said:**
> Hi,

I have exactly the same problem, and I also reinstalled Nicotine+ on my macbook. When i try to open the shortcut it appears in dock, but after a few seconds it disappears. Does anybody have a solution for me???


Thanks in advance!
try deleting the user profile (/home/'user'/.nicotine) then start nicotine again.

---

### Post by flipped on 2010-12-03
> **gandaran said:**
> try deleting the user profile (/home/'user'/.nicotine) then start nicotine again.


I can't find a user profile. I went to the home folder - (I don't know what you mean with user, but there's only one user on this mac and that's me. I can't find .nicotine). I deleted all the nicotine files that I could find. 

This is the link that I'm using to download a new version of nicotine: [http://129.125.101.92/nicotine+/nicotine+-1.2.14rc2_OSX.zip ]("http://129.125.101.92/nicotine+/nicotine+-1.2.14rc2_OSX.zip")

And again the same problem... in 2 seconds the shortcut disappears out of dock.

Damn, I'm desperate. Finally when I found a program that uses the slsk client, this is happening...

---

### Post by gandaran on 2010-12-04
> **flipped said:**
> I can't find a user profile. I went to the home folder - (I don't know what you mean with user, but there's only one user on this mac and that's me. I can't find .nicotine). I deleted all the nicotine files that I could find. 

This is the link that I'm using to download a new version of nicotine: [http://129.125.101.92/nicotine+/nicotine+-1.2.14rc2_OSX.zip ]("http://129.125.101.92/nicotine+/nicotine+-1.2.14rc2_OSX.zip")

And again the same problem... in 2 seconds the shortcut disappears out of dock.

Damn, I'm desperate. Finally when I found a program that uses the slsk client, this is happening...
did you look in the hidden files in the home directory? (nautilus » view » show hidden files) you must have the user profile there.

---

### Post by flipped on 2010-12-09
Oke, I downloaden secret so that I can see the hidden files. This is what I see in the folder nautilas: - .com.apple.timemachine.supported 
             - .DS_Store
             - Portfile
             - Files   - patch-nautilus-file.c.diff
                         - patch-nautilus-emblem-utils.c.diff
                         - patch-eel-Makefile.am.diff
                         - patch-configure.in.diff

I don't think these files have anything to do with my user profile, right?

---

### Post by WorMzy on 2010-12-09
You don't need to download anything to view hidden files.

Open up your file browser and browse to your home folder (e.g. /home/flipped).
Then press Ctrl+H to make hidden files visible.
Then find the folder which is called ".nicotine", and delete it.
Then try running nicotine again.

Or

Try launching nicotine from a terminal (Applications -> Accessories -> Terminal), it may tell you why it's not running. If it reports a segmentation fault, then re-installation may help; but if it's some other error then you may need to do something else.

---

