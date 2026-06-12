---
title: "KDE and Gnome competing on my computer?"
date: 2009-08-03
forum: General Help
---

### Post by shelbyvision on 2009-08-03
For several weeks my HP laptop has been acting like it had a stroke. Almost anything involving use of the touchpad is unbelievably slow. It's not the hardware because I tried it with a mouse and it was just as bad. In addition, most of the looks of the desktop have been changed and it will not let me change them back. In the screenshot look at the top menu bar: many of the icons are not default Ubuntu icons, which is what I had. I just recently noticed that in Applications/Other, there are a lot of menu items that didn't used to be there. See the screenshot: Disk and File Systems< Input Actions, Keyboard, Keyboard Layout, Monitor and Display, System Services, and User Management, when opened all say "Configure-KDE Control Module" at the top. I searched "KDE Control Module" in Synaptic, and it showed a lot of packages, but none that are installed. 
I have posted three other times about this problem, and gotten nowhere with it, but I hadn't noticed all those KDE apps before. I'm wondering if I might have inadvertently installed some KDE stuff that's clashing somehow with Gnome and causing all these problems. If so, how would I go about resolving the problem? (OS: Hardy 8.04)
Thank you,
Steve

---

### Post by nikhilk on 2009-08-03
Steve, could you post the configuration details of your laptop? Also do you notice the same mouse sluuggishness when you boot from a live-CD?

Did you install any new packages recently that might have pulled in the KDE related stuff?

---

### Post by shelbyvision on 2009-08-03
> **nikhilk said:**
> Steve, could you post the configuration details of your laptop? Also do you notice the same mouse sluuggishness when you boot from a live-CD?

Did you install any new packages recently that might have pulled in the KDE related stuff?
What exactly do you mean by configuration details? Where do I find it?
I don't have a live-CD for Ubuntu 8.04. I upgraded from Gutsy using synaptic. I do have the 7.10 CD, but I don't think that would be useful(?).
AFAIK, I did not install any KDE packages at the time this started, although I have several KDE applications that I have had installed for quite a while.
Steve

---

### Post by shelbyvision on 2009-08-03
Is this what you mean by configuration details? (See attachment)

---

### Post by nikhilk on 2009-08-04
Yes Steve, that is what I meant. My old desktop has the almost exact configuration and things are very smooth and responsive. I use KDE and not more than a couple of GNOME applications.

You can take a look at the long command given [here]("http://psychocats.net/ubuntu/puregnomedapper") under heading "Remove Kubuntu" to remove KDE apps. Evaluate each KDE application specified there and then uninstall if OK and see if performance improves.

---

### Post by shelbyvision on 2009-08-04
> **nikhilk said:**
> Yes Steve, that is what I meant. My old desktop has the almost exact configuration and things are very smooth and responsive. I use KDE and not more than a couple of GNOME applications.

You can take a look at the long command given [here]("http://psychocats.net/ubuntu/puregnomedapper") under heading "Remove Kubuntu" to remove KDE apps. Evaluate each KDE application specified there and then uninstall if OK and see if performance improves.
My computer used to be smooth and responsive. :(
Thank you for the suggestion. I ran the command, and it told me that not one of those packages was installed. So it looks like my theory is wrong, and it's something else causing the problem.
Steve

---

### Post by nikhilk on 2009-08-04
> **shelbyvision said:**
> My computer used to be smooth and responsive. :(
Thank you for the suggestion. I ran the command, and it told me that not one of those packages was installed. So it looks like my theory is wrong, and it's something else causing the problem.
Steve

Yes, it must be something else then.

Could you check the output of the command top and see is any process is hogging RAM or CPU? After running top, press Shift+P to sort by processor utilization and press Shift+M to sort by memory utilization.

---

### Post by shelbyvision on 2009-08-04
> **nikhilk said:**
> Yes, it must be something else then.

Could you check the output of the command top and see is any process is hogging RAM or CPU? After running top, press Shift+P to sort by processor utilization and press Shift+M to sort by memory utilization.
OK, I did that. All the cpu numbers are small, biggest cpu number is 2%. The biggest memory number is Firefox at 30.5%, all the other memory numbers are very small. Near the top, at the "Tasks" line, the last item is "1 zombie". What's that?

---

### Post by nikhilk on 2009-08-04
> **shelbyvision said:**
> OK, I did that. All the cpu numbers are small, biggest cpu number is 2%. The biggest memory number is Firefox at 30.5%, all the other memory numbers are very small. Near the top, at the "Tasks" line, the last item is "1 zombie". What's that?

Zombie process is a terminated process which has not reaped by its parent process :)
It usually indicates a bug in the application or some forceful abrupt termination of process.

Check for process with Z as STAT value in output of
```
ps ax
```
that will be the zombie process although that may or may not be the culprit for the performance degradation. See if the same process is always seen as a zombie even after several reboots.

---

### Post by shelbyvision on 2009-08-04
> **nikhilk said:**
> Zombie process is a terminated process which has not reaped by its parent process :)
It usually indicates a bug in the application or some forceful abrupt termination of process.

Check for process with Z as STAT value in output of
```
ps ax
```
that will be the zombie process although that may or may not be the culprit for the performance degradation. See if the same process is always seen as a zombie even after several reboots.
Thanks. Here's the only line with a value of Z:
 8743 ?        Z      0:00 [sh] <defunct>
I don't know what that means.
I haven't tried rebooting yet. I give it a try and see what happens.

---

### Post by shelbyvision on 2009-08-04
I did a search and found this:[http://ubuntuforums.org/showthread.php?t=778640]("http://ubuntuforums.org/showthread.php?t=778640")
The zombie turned out to be the deskbar applet. I simply right-clicked on it and removed it, and now the mouse response is working normally. WEIRD! At least at the moment, it appears to be fixed! :)
Thank you Nikhilk for all the help.
Now I just have to figure out how to get my gnome desktop back.

---

### Post by shelbyvision on 2009-08-05
I guess I spoke too soon. The longer I have the computer on, the slower the mouse response gets. The worst part is trying to navigate the bookmarks menu in Firefox, and scrolling in Firefox is delayed, so when I try to scroll, at first nothing happens and then it starts scrolling and keeps going way beyond where I wanted to go. The scrolling is also jerky.There are no zombies now, but getting rid of the one that was there seemed to fix it, but only temporarily. :( :confused:

---

### Post by shelbyvision on 2009-08-05
Here's a new twist: I looked for other apps that could possibly be causing problems and saw the "tracker" icon at the top right of the screen. I closed it, and the mouse response returned to normal again, and after hours of use, has stayed that way. :D I wish I knew why tracker was causing that behaviour. One problem didn't change: that crazy scrolling thing I mentioned in the previous post.

---

