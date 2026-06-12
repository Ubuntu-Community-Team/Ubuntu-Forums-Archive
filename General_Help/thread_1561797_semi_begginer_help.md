---
title: "semi begginer help"
date: 2010-08-26
forum: General Help
---

### Post by noideac on 2010-08-26
i got ubuntu 10.04 yesterday and installed it with windows xp home. to day i logged on and i had 4 problems.

1. There is no sound for no know reason

2. wont authorize a USB hard disc i used yesterday just fine.

3. Wont turn on correctly when a thunb drive is plugged in.

4. Wont shut down, just goes to login. Please help!

---

### Post by quixote on 2010-08-28
1. There is no sound for no reason
Sometimes, when you mute sound in the system tray area, and then unmute it there, it doesn't actually unmute.  Open sound preferences by clicking on the little loudspeaker icon, and try muting and unmuting in the main sound preferences window.  That probably won't do it, and then there's command line stuff we can try, but let's hope for the best ;).

2. wont authorize a USB hard disc i used yesterday just fine.
Did you unmount it before unplugging?  If you turned the computer off without unmounting, that's not a problem, and it shouldn't be doing this. Was the USB plugged in before the computer was started on the day that it did work? When you open the file manager, eg by going to Places > Home, does the left pane showing places (hit F3 if there's no left pane) show the drive, it just won't let you look at it?  Or does it not show it at all?  There are ways to tell the machine exactly how to handle a specific drive which I can go into if it looks like there aren't easier answers.

3. Wont turn on correctly when a thumb drive is plugged in.
What are the symptoms?  The computer doesn't boot properly at all?  Grub (the choice of operating systems at the very beginning) does its thing, but then hangs at some point?  (Which point?) Or Ubuntu boots, but there's something wrong with it, and if so what?  Does it do it with all thumbdrives, or only that one?  (In which case there's probably something wrong with that thumbdrive.)  

4. Wont shut down, just goes to login.
What are trying to use to shut down?  If it's a choice that says "logout" all it will do is give you a new login screen.  Stupidly, in my opinion, they've separated shutdown and restart from login, so if this is your problem you need to hunt around for another menu option or icon that gives you a shutdown option.  You can also right-click on an empty part of the panel, select Add to Panel, and then select "shutdown" applet in the list that appears.  Clicking on that will bring up an option to shutdown.

---

