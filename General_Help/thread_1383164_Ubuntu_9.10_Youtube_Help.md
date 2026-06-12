---
title: "Ubuntu 9.10 Youtube Help"
date: 2010-01-16
forum: General Help
---

### Post by Kindersoper on 2010-01-16
I need some help with youtube on ubuntu 9.10 since i just upgraded from 9.04 today. Everytime i try to watch a video, the video box is either grey or is just black. If i wait for 5 minutes, the screen loads but it seems like the bar to move what parts to watch is like opaque so its kinda faded and the video doesnt play. What do i need to do to get my youtube up and running again.

---

### Post by fancypiper on 2010-01-17
What CPU do you have? 32 bit or 64 bit?

# As per [http://ubuntuforums.org/showthread.php?t=1263905](http://ubuntuforums.org/showthread.php?t=1263905)
# Howto fix Flash on Ubuntu 9.10
If you are not able to click on flash (e.g. on Youtube), here is how to fix this known bug (works for both 32-bit and 64-bit):
1. Press ALT+F2 and enter:
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
2. Add the following line before the last line in the file:
export GDK_NATIVE_WINDOWS=1
3. Save and restart Firefox, or if this doesn't fix it, try restarting Ubuntu.

---

### Post by Kindersoper on 2010-01-17
> **fancypiper said:**
> What CPU do you have? 32 bit or 64 bit?

# As per [http://ubuntuforums.org/showthread.php?t=1263905](http://ubuntuforums.org/showthread.php?t=1263905)
# Howto fix Flash on Ubuntu 9.10
If you are not able to click on flash (e.g. on Youtube), here is how to fix this known bug (works for both 32-bit and 64-bit):
1. Press ALT+F2 and enter:
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
2. Add the following line before the last line in the file:
export GDK_NATIVE_WINDOWS=1
3. Save and restart Firefox, or if this doesn't fix it, try restarting Ubuntu.

I did the ALT+F2 but what do i do after that? It gives me the "Run Application" box with stuff like "Run in terminal", "Run with File", etc. Do i enter it in the box and just click the Run button? I did that and then it went to the npviewer thing. where do i enter in the export GDK stuff? do i add it on the same line or put it under the the gksudo line? sorry if you guys are confused, me and my room mates were told to install ubuntu so i need some pointers since i been a windows guys for a long time.

---

### Post by fancypiper on 2010-01-17
> I did the ALT+F2 but what do i do after that? It gives me the "Run Application" box with stuff like "Run in terminal", "Run with File", etc. Do i enter it in the box and just click the Run button? I did that and then it went to the npviewer thing. where do i enter in the export GDK stuff?

You opened a text editor which should be very similar to the Windows Notepad.

Copy/paste or type this line:
**export GDK_NATIVE_WINDOWS=1**
just above the very last line in the file just as I said before. Save the file and exit the editor.

gksudo means change to the super user and use a graphical app, in this case gedit.

---

### Post by Kindersoper on 2010-01-17
ok. Here is what i got so far. I did the whole gksudo thing in the bar and pressed run. The gedit box comes up and it says this exactly....
[                               #!/bin/sh                                                 ]
[                               TARGET_0S=linux                                    ]
[                               TARGET_ARCH=i386                                ]
[                                . /usr/lib/nspluginwrapper/noarch/           ]

where do i enter the "export GDK_NATIVE_WINDOWS=1"? I think i keep on putting it in the wrong place. I put it right next to the "i386" with no space, next to "i386" with a space, and lastly i tried making a new line after the "i386" and entered it in so it looks like this....
[                               TARGET_ARCH=i386                                ]
[                               export_GDK_NATIVE_WINDOWS=1           ]
[                               . /usr/lib/nspluginwrapper/noarch/            ]

what am i doing wrong because whenever i try something and close then open up firefox again, firefox seems way slower so i gotta erase the "export" part so it becomes normal and not slow.

---

### Post by Kindersoper on 2010-01-17
bump. can anyone answer my last question on where i have to input the "export GDK" code?

---

### Post by erinmbates on 2010-01-17
have you tried sudo apt-get install flashplugin to see if you have the latest version?

---

### Post by Kindersoper on 2010-01-18
i did that a while ago. this only started happening when i updated to 9.10 and when i had 9.04, it was perfect and my computer would run super fast. Now it just runs sh!t and all these updates its giving me is not helping at all.

---

### Post by fancypiper on 2010-05-31
Perhaps these two guides can help you:

[Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683)

[What To Do After A Fresh Ubuntu Install: A Script For Ubuntu 10.04 Lucid Lynx](http://www.webupd8.org/2010/04/what-to-do-after-fresh-ubuntu-install.html)

---

