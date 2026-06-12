---
title: "Startup disk creator not always loading iso's?"
date: 2010-11-08
forum: General Help
---

### Post by Macfunky on 2010-11-08
I have this problem across all my computers running Ubuntu (Lucid and Maverick installations). It works sometimes but it's hit and miss. Sometimes it will load up an iso no problem and i have a start up flash stick in no length of time. Other time's it will not load up an iso. I have tried formatting my flash drive these times but it doesn't make a difference as the drive is always recognised by the program yet i sometimes can't load an iso. When this happens i find that i generally have the same problem at the same time on my other Ubuntu installations. I find it weird. Anyway it's very frustrating when i come across another distro that i really want to try out and i cannot load the iso in the program. Anyone have this same problem or know how to fix it?

---

### Post by technoboi on 2010-11-15
> **Macfunky said:**
> I have this problem across all my computers running Ubuntu (Lucid and Maverick installations). It works sometimes but it's hit and miss. Sometimes it will load up an iso no problem and i have a start up flash stick in no length of time. Other time's it will not load up an iso. I have tried formatting my flash drive these times but it doesn't make a difference as the drive is always recognised by the program yet i sometimes can't load an iso. When this happens i find that i generally have the same problem at the same time on my other Ubuntu installations. I find it weird. Anyway it's very frustrating when i come across another distro that i really want to try out and i cannot load the iso in the program. Anyone have this same problem or know how to fix it?

I am getting the same problem. I have previously had imported Ubuntu, Mint & Jolicloud distros and they still show up in the list but I can't import any other distros. I tried finding the config files to see if I could locate the problem - like why are these distros still shown - is that normal? So, no, sorry, no answers. I guess if no one comes up with anything a trip top Launchpad might be in order.
I tried running the app from the command line:
usb-creator-gtk
 It launched the GUI but, in the terminal reported:
'Unable to find Joliet SVD'
Thinking, 'I had one of those but the handle fell off', I looked it up on Google but there were only references to distant bugs - nothing in the past year. I checked out the bugs on Launchpad. There was something that sounded similar but I don't think it was the same bug.
"usb-creator silently ignores invalid ISO files without warning the user".
I know that the iso files were OK because I used unetbootin & they worked in there but I prefer usb-creator-gtk.
So, unless I've missed it, I don't think this has been reported as a bug to Launchpad yet. Let's see if someone can come up with an answer, though it's been a week since you posted.

---

### Post by Ulty on 2011-01-04
i think i have the same problem. I downloaded  Fedora-14-i686-Live-Desktop.iso and tried to create a boot able usb thumb drive. The program recognized the usb device without a problem, but  when i tried to load the " Source disc image (.iso) or CD: " from my  download folder, it does not come up in the CD Drive/image field.

---

### Post by technoboi on 2011-01-04
Hmmm, I am beginning to think that it will only work with Debian based distros. I have had it work with Mint. I have several distros now in the same directory. I found that the Debian based ones will load up but others will not.
It looks like it's necessary to use another package for non-Debian distros - Unetbootin for example.

---

