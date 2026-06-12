---
title: "How To &#8594; Fix The Indicator Applet and Me-Menu...the (relatively) easy way."
date: 2010-06-22
forum: General Help
---

### Post by noob555 on 2010-06-22
**Overall Problem:** The Me Menu and Indicator Applet are large, don't work with Thunderbird, don't give appropriate notifications for new mails or chats, and generally difficult to customize.  I and others have complained about this in [_various_]("http://ubuntuforums.org/showthread.php?t=1311812") [URL="http://ubuntuforums.org/showthread.php?t=1466061"]_places_.
[/URL]
Below is the best solution that I could find to (almost all) of the problems.  If you follow my instructions, then you can remove the Me-Menu and the Mail tray icon while increasing functionality.
[B]
(1)Create a New Mail Indicator for Thunderbird[/B]

_Problem:_ The Indicator Applet does not work with Thunderbird, so the new mail indicator is effectively useless in this regard.  

_Solution:_ As I see it, you have two separate options.
[I]
First,[/I] if you want to keep the Indicator Applet, then you can use the following hack on [this post]("http://ubuntuforums.org/showthread.php?t=1439519").  No guarantees from me as I didn't try it.  But check the thread and see what other say.  There are other solutions out there as well.  Just search a bit.
[U]
Second,[/U] if you want to get rid of the Indicator Applet's Mail icon (which I did because it seriously annoys me) then you can download the Thunderbird Add-On called _[firetray]("https://addons.mozilla.org/en-US/thunderbird/addon/4868/")_.  This add-on is a nice little linux-specific addition that I found, which creates a Thunderbird tray icon and an inidicator of however many new messages you have.  Also, you might download _[Mozilla Notification Extensions]("https://addons.mozilla.org/en-US/thunderbird/addon/11530/")_, which will better integrate the new mail bubble notifications from thunderbird with gnome.  

(NOTE: One problem that I had with firetray is that the new mail count includes all unread mail in every subscribed folder – including junk, trash, et cetera.  This was a bit of a problem at first.  But the answer is easy.  On the left hand table in Thunderbird where your mail folders are listed, simply right-click on the appropriate folder and then choose “subscribe...”.  A list of all of the associated mail folders will show up.  Simply un-check the folders that you do not want firetray to count.  As you'll find, it's an imperfect solution, but it's the best I could find after weeks of searching for easy answers.)
[B]
(2)Better Indication for New Chat Icons (Empathy)[/B]

_Problem(s):_ 

_New chat Indications:_ some people do not like the “new incoming chat” indicator in the indicator applet.  I personally hate it.  Under my customized theme, it turns the mail icon from light shade of gray to a dark shade of gray.  It is much too subtle and I consequently miss a lot of chats.

_Change Status/Quit:_ The functionality for Empathy is Split between the Indicator Applet and the Me Menu.  This means that you must have both applets running in order to have basic functionality.  

_Solution(s):_ Again, there appear to be two separate solutions.
[I]
First,[/I] if your only problem is the poor indication of an incoming IM., then you might try changing your theme.  Some posts suggest that the problem is theme specific.  If you aren't using a lot of gray on your panels, then you probably won't have this problem.  (I use a lot of gray because it reduces the strain on my eyes after hours of computing.  So this does not work for me.)  To change your theme, go to System &#8594; Preferences &#8594; Appearance and choose from the available themes.
[I]
Second,[/I] and this is what I did, give up on Empathy altogether and just go with Pidgin.  It is available in the Ubuntu Software Center and does everything the Empathy can do.  There are also a range of available plug-ins allowing for libnotify pop-ups and better message notification.  Better yet, It runs off of its own tray icon so you don't need two large screen-hogging applets to run it as is the case with empathy.  Also, I find that the indicators are easier to see.

**(3)Volume Control & Battery Indicator Applet**

_Problem:_ The tray indicator for volume control is tied to the indicator applet.  So too is the battery indicator.  I find this annoying because I do not like the mail/chat indicator and want it gone.
[U]
Solution:[/U] Go into Synaptic and find the package “indicator-messages”.  This is the mail tray icon.  Right-click and “mark for removal”.  Voilà!  It's finally gone.  But you volume control and battery indicator are still there.  Also, the Indicator Applet is tied to several other applications including Rhythmbox and Transmission.  So getting rid of it altogether is not really an option unless you want to lose functionality with some applications.

That said, you might not use Rhythmbox or Transmission.  Or you might use them without using the tray icon.  So if you just want to have the volume control, then the solution is also easy.  Got to System &#8594; Preferences &#8594; Startup Applications &#8594; Add.  Then type “gnome-volume-control-applet” into the command line.  Voilà!

**(4)The Me-Menu is Obnoxious**

If you've done everything above, then just remove it altogether.  You don't need it anymore because you can change your status from the Pigdin tray icon.  Depending upon your set-up, you might just find that you need to add a “shut down” button.  That's easy.  Just right-click on the panel &#8594; Add to Panel &#8594; Shut Down...  This will give you a button that allows you to easily shut down, suspend, re-start, and hibernate.

**(5) Unsolved: The awkward spacing on the Indicator Applet**

As you may have noticed, you still need the Indicator Applet for several applications including your volume control, battery, and miscellaneous other applications.  The spacing between these icons is awkward and obnoxious.  I have no idea how to fix this.

---

### Post by gmargo on 2010-06-22
I have noticed that when the Me-menu (aka "Indicator Applet Session") is removed, then two new entries (logout and shutdown) magically appear in the Menu Bar->System menu.  So no real need for the additional shutdown applet unless you must have a hibernate entry.

---

### Post by temporos on 2010-07-02
How do you remove the Me menu?  I'm using the Netbook Edition, and when I right click on the Me menu, the "Remove from panel" option is greyed-out.

**Edit: **Two more questions for now:
[LIST=1][*]I am not seeing a panel icon for Pidgin (after removing the indicator-messages package).  Did you have to install a specific package to get the Pidgin panel icon?
[*]What command did you add to the Startup Applications to get Pidgin to automatically hide itself to the panel?
[/LIST]

---

### Post by noob555 on 2010-07-07
Sounds like you've got some issues related to the Netbook addition.  I'm no help there.

As to getting Pidgin to auto-hide to the panel, I don't know either.  I just start pidgin.  It loads the window and I can close it if I want to.  So long as you have the Notification Area added to the panel, you should have a permanent tray icon loaded whenever you are signed on.

---

### Post by wowshailen on 2010-07-14
With every new release, the number of Ubuntu bugs seem to soar. Ubuntu tries too much to force its way of doing things on people, and this is very bad to the liberty of expression and usage of the computer.

If i want to completely disable the indicator-applet, please allow me to do so. Why is the option 'Remove from panel' greyed out !?

---

### Post by temporos on 2010-07-15
> **wowshailen said:**
> If i want to completely disable the indicator-applet, please allow me to do so. Why is the option 'Remove from panel' greyed out !?

That, my friend, is the $10,000 question...

---

### Post by kayzu on 2010-10-08
> **noob555 said:**
> **(5) Unsolved: The awkward spacing on the Indicator Applet**

As you may have noticed, you still need the Indicator Applet for several applications including your volume control, battery, and miscellaneous other applications.  The spacing between these icons is awkward and obnoxious.  I have no idea how to fix this.

There has been a patch out for this issue since may, but for some reason the spacing apparently isn't considered a bug.
[https://bugs.launchpad.net/indicator-application/+bug/527267/comments/30](https://bugs.launchpad.net/indicator-application/+bug/527267/comments/30)

---

### Post by Its_Rishi on 2011-01-02
> **wowshailen said:**
> With every new release, the number of Ubuntu bugs seem to soar. Ubuntu tries too much to force its way of doing things on people, and this is very bad to the liberty of expression and usage of the computer.

If i want to completely disable the indicator-applet, please allow me to do so. Why is the option 'Remove from panel' greyed out !?
i added the indicator applet there it comes with volume button after that run the following code
sudo apt-get purge indicator-sound
then the volume button disappears from the indicator applet
again i tried added the indicator applet but the volume button doesn't appears
could u please help me how to bring back the volume along with indicator applet?

---

