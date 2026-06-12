---
title: "Missing checkgmail appindicator in Ubuntu Unity"
date: 2011-05-12
forum: General Help
---

### Post by volkerbradley on 2011-05-12
Hi,
I cannot see the checkgmail appindicator icon in my newly installed Unbuntu Natty Unity.
Do some of you see this appindicator?  Is there a trick to getting it to show?

---

### Post by ubun_two on 2011-05-12
Maybe try this?

[http://askubuntu.com/questions/30742/how-do-i-access-and-enable-more-icons-to-be-in-the-system-tray](http://askubuntu.com/questions/30742/how-do-i-access-and-enable-more-icons-to-be-in-the-system-tray)

---

### Post by volkerbradley on 2011-05-14
Yes, I tried multiple ways to do this.
I entered CheckGMail at the end of this value and also in the middle of this value. I then logged out and then logged back in.  No CheckGmail icon.
Then I rebooted the system.  No CheckGmail icon.
Then I did sudo dconf-editor and added CheckGmail as instructed and then logged out and also rebooted.  No icon
Then I did sudo dpkg -r checkgmail following by sudo apt-install checkgmail.  Rebooted.  No icon
Any other suggestions?

---

### Post by volkerbradley on 2011-05-14
OK, I got it. From the command line I did:
$: gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
Logged out and logged back in
All the application icons that I wanted to see including the CheckGMail icon are now present in the top panel.
Thanks for pointing me in the right direction.

---

### Post by volkerbradley on 2011-05-16
I found that when I gave the gsettings set com.canonical.Unity.Panel systray-whitelist "['all']" command, the original appicons like sound and networking no longer functioned.
To fix this I opened the dconf-editor and clicked on desktop -> unity -> panel
I clicked on the Set to Default button.
Then I highlighted the systray whitelist and then added Checkgmail and Pidgin and then hit Enter key
The closed the editor and logged out and back in again.  Now all the icons function.  Notice that the name is not CheckGMail but Checkgmail.

---

