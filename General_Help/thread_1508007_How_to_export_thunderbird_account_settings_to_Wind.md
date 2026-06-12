---
title: "How to export thunderbird account settings to Windows computer?"
date: 2010-06-12
forum: General Help
---

### Post by inverseroom on 2010-06-12
I've finally got all my accounts the way I like them in Thunderbird.  I'm using IMAP and so don't have to move the emails, but how do I migrate my account settings to my other computers?  The other machines are running WinXP.

---

### Post by SlidingHorn on 2010-06-12
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

This one's about going from Win to Ubuntu, but it couldn't hurt as a bit of a reference: [https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows/TransferringFilesAndSettings](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows/TransferringFilesAndSettings)

Same thing here: [http://www.linuxquestions.org/questions/linux-software-2/moving-from-thunderbird-in-windows-to-thunderbird-in-linux-336797/](http://www.linuxquestions.org/questions/linux-software-2/moving-from-thunderbird-in-windows-to-thunderbird-in-linux-336797/)

---

### Post by oldfred on 2010-06-12
I have not totally converted to Lucid so TB2 in Karmic is in a slightly different location. I have my profile in a NTFS shared partition anyway and edit profile.ini to find it. I copy the entire profile for both thunderbird and firefox to my portable when we travel and back when we return.

[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)

older info
[http://www.mozilla.org/support/thunderbird/profile#locate](http://www.mozilla.org/support/thunderbird/profile#locate)
[http://kb.mozillazine.org/Profile_Manager#Linux](http://kb.mozillazine.org/Profile_Manager#Linux)
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Category:Profiles](http://kb.mozillazine.org/Category:Profiles)

---

### Post by inverseroom on 2010-06-12
Thank you!  I will try this later, and mark the thread solved if it works.

---

### Post by inverseroom on 2010-06-12
FYI, it DOES work--you just replace the folder in XP's %appdata% with the one from Ubuntu, after first running the program to get it to create a folder in appdata.  HOWEVER, if you get a message to the effect that Tbird is already running, even though it isn't, you have to go into profiles.ini and change the name of the default profile folder to the one you imported from Linux.  You might also have to delete .parentlock, but since Linux and XP don't name this file the same way, you probably don't.

Thank you!

---

