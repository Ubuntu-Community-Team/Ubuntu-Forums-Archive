---
title: "Terminal Navigation Problem ( SSH )"
date: 2012-07-11
forum: General Help
---

### Post by ubunwhat on 2012-07-11
I've never actually been great at understanding where I am at any given time when using Terminal, but now I'm totally confused.  I am using openssh in the terminal and trying to move a directory from a remote machine to a folder on this machine.  I simply cannot get the syntax right for my local machine.  Let's say that when I log in I log in as user Joe.  So, when I click the home folder icon in Unity it opens up to Joe, and I see all of my other folders that are inside Joe.  Now, let's say that within Joe I have a folder titled Remote.  And in Remote I have a folder titled Box.  In using the scp command from the remote computer I cannot get it to copy to Joe/Remote/Box.  I keep getting the message that this file does not exist because I'm using the wrong path.  Here is a partial list of what I've tried so far:

Joe/Remote/Box
~/local/Joe/Remote/Box
~/Remote/Box
~/Joe/Remote/Box
/home/Joe/Remote/Box
~/home/Joe/Remote/Box

Ok, so I give up.  Where, exactly does the terminal point to when using SSH?  Where does it think I am relative to Box so I can get the path right?

---

### Post by GreatDanton on 2012-07-11
It should be:
/home/<username>/Remote/Box/

Try it. And don't forget to pay attention on big letters. If your folder is named ex. ReMoTe then you should type ReMoTe, not remote.

Also don't put ~ in front of this. Just type it like I did.

Hope this helps.

Edit; ooops, you also tried my suggestion. Then check only if you type name of the folders exactly like they are.

---

### Post by ubunwhat on 2012-07-11
I am absolutely mystified here.  I wound up just using "." which copies to the current directory on the local machine.  The process ran and said it was completed but I cannot find the files that were copied anywhere locally.  I've tried search, find, etc but it all comes up empty.  I'm going a bit batty here.

---

