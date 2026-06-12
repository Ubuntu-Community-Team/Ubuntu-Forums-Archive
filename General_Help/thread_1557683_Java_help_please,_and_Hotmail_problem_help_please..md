---
title: "Java help please, and Hotmail problem help please..."
date: 2010-08-21
forum: General Help
---

### Post by liviococcia on 2010-08-21
Hello Members
I'm thinking that the two issues are related, but i don't know.

If i log on to my Hotmail account using Firefox, i first get to the Windows live page and by clicking onto the 'inbox' link, i then get to my email folders.

What seems to happen is, after reaching to my account folders and clicking on any email, or any of the folders, i find nothing opens it's as if these are all just non-functioning, but i can click onto other parts of the account i.e menu items, and they will work. If i then log out and log in again (i may need to do this a few times) the account and page will operate correctly.

The problem made me think that it might be a Java problem, and that maybe i don't have the latest Firefox Java plug-in, or Java RE package, would Firefox not update itself automatically though with regards to the plug-in?

I have looked at the various help posts and links to FAQ info, but is there a simple way of getting the latest Java RE package with the browser plug-ins, how i do get Ubuntu to first look for it, and if necessary download and install it automatically the way it does for all the other updates Ubuntu needs, when it's doing it's 'Update Check' routine?

Any help would be grateful.

Kind regards
Livio

---

### Post by oldos2er on 2010-08-21
> **liviococcia said:**
>  is there a simple way of getting the latest Java RE package with the browser plug-ins

Activate the partner repository (System, Administration, Software Sources), then in a terminal run ```
sudo apt-get update && sudo apt-get install sun-java6-plugin sun-java6-jre
```

---

### Post by liviococcia on 2010-08-21
Thanks oldos2er for the help.

I did activate a 'Partner' repository by going to LucidLynx Release notes (link below), and following the instructions in the section 'Sun Java moved to the Partner repository' from the help page if any newbie member needs to know.
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)

....so, i opened a 'Root' terminal, copied and pasted the instruction below into it as directed..

add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"

... and hit the 'Enter', and the went to check if the 'Partner' repository had been added (system > administration > software sources > 'other software' tab), and it had.

Then i opened the 'Root' terminal window again, and followed instructions in oldos2er post.

Regards
Livio

---

