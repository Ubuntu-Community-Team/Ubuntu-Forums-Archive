---
title: "Still no way to change scroll speed?"
date: 2010-04-09
forum: General Help
---

### Post by pfunkman on 2010-04-09
Any way this can be done yet? Its really annoying to have my mouse scroll so slowly.

---

### Post by wojox on 2010-04-09
1. Open Firefox, then type about:config in the address bar and hit Enter.

2. In the Filter box, type mousewheel.withnokey.

3. Right-click mousewheel.withnokey.sysnumlines and then click Toggle. This should set the value to False.

4. Right-click mousewheel.withnokey.numlines and then click Modify. Bump the value to 6 or so, click OK, and then switch to another tab to see if you like the scroll speed. (Thankfully, you don't have to restart Firefox every time you make a change.) If not, experiment a bit until you find a number you like.

---

### Post by pfunkman on 2010-04-10
> **wojox said:**
> 1. Open Firefox, then type about:config in the address bar and hit Enter.

2. In the Filter box, type mousewheel.withnokey.

3. Right-click mousewheel.withnokey.sysnumlines and then click Toggle. This should set the value to False.

4. Right-click mousewheel.withnokey.numlines and then click Modify. Bump the value to 6 or so, click OK, and then switch to another tab to see if you like the scroll speed. (Thankfully, you don't have to restart Firefox every time you make a change.) If not, experiment a bit until you find a number you like.

So thats a no then? If its just the FF fix its pretty much worthless to me. Thanks though.

---

### Post by Do We on 2010-11-16
I found a standard-solution here:

[Os-Novice Blog: Increasing mouse scroll speed in firefox]("http://osnovice.blogspot.com/2007/04/test.html")

Worked for me very well on a fresh Ubuntu 10.10 install and Firefox 3.6.10.

EDIT: Not seen solution a few posts ago.

---

### Post by pze7 on 2011-02-19
You might want to take a look at the [**synclient**]("http://ubuntuforums.org/%28http://manpages.ubuntu.com/manpages/maverick/man1/synclient.1.html") program (l[ong list of options here]("http://manpages.ubuntu.com/manpages/maverick/man4/synaptics.4.html")).

The solution I used to solve my touchpad scrolling issue is to add the following item to the list under System -> Preferences -> Startup Applications:
[INDENT][FONT=Verdana]Name: Touchpad scroll speed adjustment
Command: synclient VertScrollDelta=600
Comment: Use synclient to slow down vertical trackpad scrolling. [/FONT]
[/INDENT]The higher you set the VertScrollDelta variable, the slower your scroll speed will be. Play around in a terminal and see what suits you, and when you find the optimal value, replace the '600' above. The setting will persist after rebooting.

Regards

---

### Post by wog on 2011-02-19
The synclient link points to an all-text version of the forums.
The "long list" link points to the manual page for 'Synaptics touchpad input driver'

Thank you, I did not know there were such nicely formatted manuals for Ubuntu! Unfortunately, neither of the above links points to a solution for a mouse scrollwheel that scrolls 4 lines with the smallest motion.

I tried the Firefox solution, and that was an improvement. Before I did that, the smallest movement would scroll half a page.

I'm hoping somewhere is a way to get the scrollwheel to move just a single line at a time.

Thanks!

---

