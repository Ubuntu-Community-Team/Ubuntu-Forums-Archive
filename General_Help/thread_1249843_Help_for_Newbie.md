---
title: "Help for Newbie"
date: 2009-08-25
forum: General Help
---

### Post by mvalenti on 2009-08-25
I had an issue after uninstalling ubuntu media via package mgr. System hangs on boot. I was able to use session option xterm to see that all my files were still on the drive. Now I cant even do that. I have ubuntu live with the hopes of mounting the drive and pulling all the files off I need and then reformat..... I can mount the drive but no files are visible, only recycle bin,..... I used gparted to assure myself there was enough disk space... at least 30 g free...  HELP!


Thanks in advance.......


-Mark

---

### Post by Talon2 on 2009-08-25
I can't help with specific issue but please let me give you a little advice:

Please use a title that reflects what the problem is.  A lot of folks are like me in that when we see a topic we know we try to help.  I don't have the time to filter through all the "Newbie needs help" titles so I simply ignore them.

---

### Post by MTGap on 2009-08-25
When you say hangs you have to be a little more clear, how far do you actually get? And have you tried going through recovery mode? (At grub there is usually two entries that have the same kernel one normal and the other recovery) 

Most likely some packages got messed up, try to learn to use apt in the terminal it works a whole lot better and you can actually see what's going on.

---

### Post by theozzlives on 2009-08-25
> **Talon2 said:**
> I can't help with specific issue but please let me give you a little advice:

Please use a title that reflects what the problem is.  A lot of folks are like me in that when we see a topic we know we try to help.  I don't have the time to filter through all the "Newbie needs help" titles so I simply ignore them.

How about you. Go to System > About Ubuntu > About the Name and try to learn manners.

---

### Post by MTGap on 2009-08-25
-- Stop taking over the thread with nonsense.

---

### Post by wootah on 2009-08-25
When GRUB pops up, change the boot option for the current kernel to boot into single user mode (add a 1 to the end of the line).

Find the current kernel you are using in the list, press E, and add 1 to the end of it. Then press B. This will boot into root user mode. Mount your drive and check the contents from there.

You might also be able to use the recovery option from the live CD, or the recovery option from the GRUB menu.

You may have to press ESC as your computer boots up to have the grub menu appear.

---

### Post by akakingess on 2009-08-25
> **MTGap said:**
> -- Stop taking over the thread with nonsense.

Actually, I don't think his response was nonsense, when it comes to newbies and lack of experience they may not know what went wrong and may have trouble with specifics, especially if there may be more than one issue going on, let's try to keep this a friendly community. Also, I definitely reccomend to the OP that he give a few more details within the message (how far does the system go before it hangs, have you tried doing ctrl+h to see if some of the files are hidden, and does the recovery option help at all) we are here to try to help if we can, because we were all newbies at one point or another and some of us (me for example still are), but are willing to assist if at all possible, keep your chin up and we will get you through this slight bump in the road.

---

