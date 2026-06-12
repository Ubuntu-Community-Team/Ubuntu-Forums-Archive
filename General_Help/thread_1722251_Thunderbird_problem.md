---
title: "Thunderbird problem"
date: 2011-04-05
forum: General Help
---

### Post by Lilbit69 on 2011-04-05
Help, I don't know if this is the correct board or not but I'm kind of new to this. I have my system dual-booting Windows 7 and Ubuntu (not sure which version but pretty sure it's the last LTS). I had my machine booted in Windows for server work and left it up. Someone opened Outlook and downloaded my mail. I already have Thunderbird installed and imported all of my outlook once but it seems now I need to do it again. How can I do this without having to completely reinstall Thunderbird? I had already imported and deleted all old messages as I want to be completely rid of any of Tsar Gates':lolflag: propaganda off of my machine eventually.

---

### Post by irw on 2011-04-05
Someone else might have a better solution, but I have used two different approaches to this in a similar situatios, and to merge two Thunderbird profiles.
I don't know if you can import and add emails to your current profile, but if not try one of these: (but back up first, just in case of problems ...)


1. Create a new folder in Thunderbird and move your current inbox emails and all other folders into it (or more than one if you have different accounts).
- Import all emails from Outlook
- Move original emails & folders back to where they were, merging new with old emails

- OR -

2. If you look in ~/.thunderbird/{profile name}/Mail/Local Folders/ you will see files and folders that match the folders you see in Thunderbird.
- Move these out of this folder somewhere safe
- you will now have no emails when you restart thunderbird - don't worry they will come back!
- import all your emails from Outlook
- Move all of these into a new folder - make sure this has a new different name to any other folders you may use - then close thunderbird
- Move the folders and files you moved somewhere safe back into the ~/.thunderbird/{profile name}/Mail/Local Folders/ directory - don't worry if you are overwriting the inbox, etc - they will be empty at this stage
- restart Thunderbird and move the new emails back into your inbox


A bit involved but it worked for me!

---

