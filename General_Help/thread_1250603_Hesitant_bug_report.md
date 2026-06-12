---
title: "Hesitant bug report"
date: 2009-08-26
forum: General Help
---

### Post by Manyette on 2009-08-26
As a newbie I am somewhat hesitant to report a bug, but in finding a very minor one, I found a somewhat more important one.  Not sure what to do now.

First I found that if you move the Trash Icon from the right side of the lower panel to the left side (which is where I've been used to having it) then the minimize function of a window does not work, and the window, mostly firefox, but others as well, merely closes.  I know this is a minor item, but I though i would mention it for some future work.  But after reading through all the bug reporting info, I decided that the best way to report it would be with the ubuntu-bug option.  That is when I found that that doesn't work in this version.  Executing Alt F2 brings up the window, and after selecting ubuntu-bug and Run, or Run in Terminal, nothing at all happens.

This behavior is repeatable in 9.04 with both the 11 and the current 15 kernel.  (I just did a reinstall and tried it before doing all the updates).

The machine has all current updates as of this date and time.  Fix for the minimize problem is "don't move the Trash Icon)!  The second problem I have no clue, and don't know if this is even worth mentioning, with all the serious problems being worked on. Any help appreciated.

---

### Post by balaknair on 2009-08-26
Trash Icon>

I wonder if the issue you're experiencing with the trash icon at the left end is a bug or just that the trash applet is so far to the left that it squeezes the the 'window list applet' too thin to show the minimised windows buttons.

Do the windows that appeared to close when you minimsed them reappear when you move the trash can back to the right?

Take a look at the attached screenshots if you didn't understand what I meant.

1: The 'Window List' as it normally looks.
2: The 'Trash' applet has been moved to the left, and the 'Windowlist' appears to be shrinking.
3: The Trash applet is now at the left end of the panel, and the windowlist has shrunk so much that it doesn't show the windows buttons
4: Move the Trash icon away to the right, and the windows list reappears.

To get the 'Trash icon at the extreme left end, you will have to 'unlock' the windowlist so that the trash icon can cross over the window list and move beyond it.
To unlock the windowlist> right-click on the left end of the window list(just to the left of the first window-button in the list) and uncheck the 'Lock To Panel' option. 
Now you can move the trash icon beyond the windowlist.
To move it to the extreme left(beyond the 'Show Desktop' icon) you have to 'unlock' the 'Show desktop' icon too.

Ubuntu-bug>

To generate a bug report with ubuntu-bug, you have to tell it what app to report.
eg: If you want to report a bug for the Ekiga Softphone VOIP application, the command in the Run dialog(alt+F2) should be ```
ubuntu-bug ekiga
```

Hope this was helpful.
To know more about bug-reporting with ubuntu-bug, you might want to check this webpage out
[https://help.ubuntu.com/community/ReportingBugs#Filing%20a%20bug%20with%20ubuntu-bug](https://help.ubuntu.com/community/ReportingBugs#Filing%20a%20bug%20with%20ubuntu-bug)

All the best.

---

### Post by Manyette on 2009-08-26
Thanks for the fast response.  Eveything you have said is correct, but misses the point.  As long as the trash icon is at the left end of the panel
those minimized icons will not appear under any circumstance, and so you will not know they are there.  i.e. they cannot appear to the right of the trash icon.  As I said it is a minor point, perhaps worth working at some point in the future.  As for the ubuntu-bug, the documentation for it says that it is best used when the component or program is not known.  It does not mention that the program name is needed, and in fact the statement implies that it's used in the case where it is NOT known.  Perhaps I should know what component is responsible for the panel problem, but I do not.  I guess I should explain that I used Unix on a Sun Solaris system 30 years ago working for Cyrix, and haven't used it since, and have NEVER had any experience at administrating a *nix system.  Basically I was a user, and little more, and have a great deal to learn.  I suspect this note has made that perfectly clear, unfortunately.  Again, thanks for the response.

---

### Post by balaknair on 2009-08-26
> **Manyette said:**
> Thanks for the fast response.  Eveything you have said is correct, but misses the point.  As long as the trash icon is at the left end of the panel
those minimized icons will not appear under any circumstance, and so you will not know they are there.  i.e. they cannot appear to the right of the trash icon.  As I said it is a minor point, perhaps worth working at some point in the future.  

I'm not quite sure if we're on the same page here. Did you try moving the WindowList to the right of the Trash icon
Could you try the following:
1) Right click on the little line(looks like 3 small horizontal lines) just to the left of the first icon in the Windowlist (Screenshot 1)
2) Uncheck the 'Lock to panel' option (Screenshot 2)
3) Right click again and select 'move', grab and move it a few centimeters to the right. (Screenshot 3)
4) Right click on the Trash icon> Move> shift it to the left so that it is now on the left side of the Window list. (Screenshot 4)
5) Now you can position the Windowlist applet just the way you want it.
(Screenshot 5)

> **Manyette said:**
> As for the ubuntu-bug, the documentation for it says that it is best used when the component or program is not known.  It does not mention that the program name is needed, and in fact the statement implies that it's used in the case where it is NOT known.  Perhaps I should know what component is responsible for the panel problem, but I do not.

I'm not really an expert on Ubuntu-bug, but I haven't come across a lot of good documentation other than the man pages and the link I posted in the previous reply. So AFAIK, you do have to give ubuntu-bug the app/package which is acting up. The linked page also contains a link to another page which describes how to find the right package against which to file a bug-report.
[https://wiki.ubuntu.com/Bugs/FindRightPackage](https://wiki.ubuntu.com/Bugs/FindRightPackage)

But that aside, I still feel that this isn't really a bug, just a minor glitch with the settings(the panel items are locked --> the windowlist isn't shifting to the right of the Trash applet). Could you please try the steps I mentioned and post a reply?
Thanks.

---

### Post by Manyette on 2009-08-26
Well, you're right. We are definitely not on the same page.  I don't understand your point.  I'm not interested in moving the window list.  I did as you asked, left the windowlist on the right side of the panel, Moved the trash icon to the left side of the panel. Conditions are as I described. Minimized icons are hidden.  That's my point?  Now, did I still miss your point?

---

### Post by mc4man on 2009-08-27
Possibly a little clarity, maybe not.

> I did as you asked, left the windowlist on the right side of the pane

Actually he said to move the windowlist area a few centimeters to the right, not to the right side. (just enough to fit the trash icon to it's left

The windowlist, like english, reads and expands from left to right, if you move it too far to the right there's no room to display icons, text and  expand as additional windows are minimized.
Move it back to the left side,  right up against the trash icon you placed (in other words as far to the left as it will go

---

### Post by balaknair on 2009-08-27
Could you post a screenshot of what it looks right now(just press the Print Screen(PrntScrn) button on your keyborad to get a screenshot).

Just so I can be sure i understand you correctly.

---

### Post by Manyette on 2009-08-27
Genlemen:  First, I do know how to move panel objects.  No need to explain.  Second, the default trash icon is hard up against the sindow list which is hard up against the right edge of the panel.I followed your instructions and then moved the trash icon to the left, and as it moved over the minimized icons it "compressed" them until they disappeared.  Move it right and they reappear.  My main point is that there is NO Way that those icons can appear to the left of the trash icon, no matter where it is located.  I think we're all talking at cross purposes, it's late, and I'm tired, so I think I will call it a night.  It just isn't that important to me; I can live with it in the default position.  Thanks, and take care.

---

### Post by mc4man on 2009-08-27
Your right - really isn't important,
will leave screen for the night and then remove
trash on the left, trash on the right and anything in between including minimized windows. Either trash could be removed or left without affecting anything else

---

### Post by balaknair on 2009-08-27
OK Manyette. I apologize if my explanations seemed condescending.


I hope you get this issue cleared up, though I do agree with your assessment- it's no big deal.

Either way, wish ya luck, and have a good night :) .
Bye

---

### Post by Manyette on 2009-08-27
MC4MAN, this is apparently more complex than it first appeared.  In looking at your last scren shot it works for you, and does not for me. If you will look at the three attached screen shots, I have set my panel up as you have in the first shot.  I then minimized the firefox window, and took the second screen shot.  No ff minimize icon on the panel. I first moved the trash applet on the left to the middle of the panel, and expected the minmize icond to reappear but the minimized window did not appear. I then removed the applet and it still did not appear.  Still there was no minimize icon for the ff window displayed, either when I moved the icon or when I removed it.  ?There is apparently some system difference between the two machines. Prior tests showed that with only one trash applet on the left side of the screen, when I moved it to the right, it would uncover the minimized icon which had been hidden.  Very puzzling.  But again, for me it is not a big deal either way.  Was trying to be a "good doobie" by reporting what I thought was a minor problem and now regret bringing it up.  In any event, I thank you both for trying to straighten me out.  Perhaps some other app is interfering, or some other system difference is at work.  Again, thanks for your efforts.[ATTACH]126461[/ATTACH]

[ATTACH]126462[/ATTACH]

[ATTACH]126463[/ATTACH]

---

### Post by mc4man on 2009-08-27
No need to regret anything

Just for info's sake

I **never moved the trash icon **at all, just the minimized window space and the show desktop icon.

For the 'minimized windowed space' - with no windows minimized, right clicked on the blank area just to the right of the 'show desktop' icon and unlocked the 'minimize window' area. 

Then moved it slightly to the right, maybe a quarter of an inch.
Then did the same for the 'show desktop' (keeping it to the left of the slightly moved 'minimize window' space

Then in the **newly created free space** at the very far left end **added** a trash icon, locked it, then moved the 'show desktop' back to the left as far as it would go and locked.

Finally moved the minimize window to the left back up against the 'show desktop' and also locked

---

### Post by balaknair on 2009-08-27
Hello Manyette
In the image(Screenshot2) you posted, the Window list is at the left edge(see the marked pic I've attached), followed by the desktop and trash icons. For the window list icons to be visible, right click on the stippled bar-> make sure the 'Lock to panel' option is unchecked-> 'move' the stippled bar(window list so that it reappears to the right of the trash and desktop icons.

OR: a much simpler option I should have mentioned earlier:
1) Right click on the stippled area> remove from panel
2) Right click on a point just to the right of the trash icon> add to panel
3) Select 'Window List' from the list> click Add

You're done. 

The window list acts a bit funny when you're moving it across/beyond another applet, so you have to move the cursor well beyond the other applet for it to reappear on the other side.

---

### Post by Manyette on 2009-08-27
Hi Balaknair,
>  In the image(Screenshot2) you posted, the Window list is at the left edge(see the marked pic I've attached), followed by the desktop and trash icons.
No, in that picture the windowlist is on the right side.  So I'm not sure where you are going with this post.  Can you clarify for me?  Thanks, Don

Added:  Strangly enough, after appending this post, I have reinstalled the whole system, and now the minimize does not work at all, even with the default lower panel.  Definitely something weird going on.  Apparently something in this machine.  In any event, I have wasted enough of your very enlightening time. So, again my thanks, and I am going to give this up as a bad job.

---

### Post by balaknair on 2009-08-27
Hello Manyette
Sorry for the delay in replying
I think I finally see the source of the misunderstanding.

> **Manyette said:**
> Hi Balaknair,

No, in that picture the windowlist is on the right side.  So I'm not sure where you are going with this post.  Can you clarify for me?  Thanks, Don


Actually no it's on the left edge. 
[ATTACH]126527[/ATTACH]

The position of the window bar is marked not by the empty space on the panel but by the little stippled bar I'm pointing to in the screenshots.
[ATTACH]126526[/ATTACH]
[ATTACH]126528[/ATTACH]

The size of the Window list is the free space immediately to the right of the little stippled bar. See this image with three window lists- one at the left edge totally squished by the desktop icon, the second somewhat squished by the trash icon and the third 'unsquished'
[ATTACH]126530[/ATTACH]

So in the screenshot you posted(the attached pic titled 'On the left') it's at the left edge of the panel and is squished by the trash and desktop icons so that the minimized windows are not visible.

I hope this helps you understand what I am trying to say.

---

### Post by balaknair on 2009-08-27
I have to be off now(gotta get to work), but I'll check back in about 4 hours. 

All the best, and have fun.

---

### Post by Manyette on 2009-08-28
Hi Balaknair, well that's my problem.  Terminology.  I now realize that read windowlist as desktop.  So when you say windowlist, you are referring to the icon which hides or displays desktop apps?  That helps a lot.  But as I said, I did a complete reinstall of 9.04, and as a default out of the box, the minimize button does not work.  So I deleted the lower panal, Added a new panel, with nothing on it at all, and still nothing appears on it when I minimize.  Don't know if install went wrong, or there is still more I just don't understand.  I'm still trying to figure it out.  But at least I've learned a bit more of the terminology.  Let you know if anything occurs to me, and again, thanks. - - - Don

---

### Post by balaknair on 2009-08-28
On the new panel(with nothing on it)> Right click> 'Add to Panel'> Window List
Minimised windows should now show up.

A newly created panel contains nothing(no window list, trash or any other applet)

---

### Post by Manyette on 2009-08-28
Hi Balaknair - Well, I bit the bullet and did another reinstall, this time saving some things to a thumb drive which made it a bit easier.  (If nothing else, I sure am getting good and installs, anyway!!!)  I have been reinstalling items one at a time, and checking after each to see if the minimize function is working.  So far, so good.  I believe something went wrong with the last install.  This one seems to be behaving much better.  Will keep you posted if it goes wrong again at some point, but meanwhile, thank you very very much.for all your help.  Someday maybe I'll get to the point where I can do likewise for others.  Take care - Don

---

### Post by Manyette on 2009-08-28
Hi again, Balaknair, Well, it definitely was a bad install earlier.  I have resinstalled everything, and the panel works exactly as all said it should.  It sort of bothers me as to why the install was bad, but that was definitely was the problem. And again, many thanks again. -  Don

---

### Post by balaknair on 2009-08-30
Hello Manyette.

Good to hear that you managed to get things sorted out. Bad installs do happen, or in my case I manage to turn perfectly installs bad by incessant tweaking and installing a whole bunch of unstable 'beta' apps to test. :D
I'm putting off doing a total reinstall of Ubuntu 9.04 for now, since I plan to install Ubuntu 9.10 Karmic Koala once it hits the Alpha 6 stage(Sept 16th).

I hope you don't run into any further problems :D

Have fun with Ubuntu

---

### Post by Manyette on 2009-08-31
Hi Balaknair, Once again you have saved me much grief. The "reconfigure-panel" did fix the panel problem.  It did work fine.  And hopefully there were no more errors in the faulty install.  Once again, I thank you very much for your help. - - Don

---

### Post by balaknair on 2009-08-31
Glad to hear that, Manyette. :D

All the best.

---

