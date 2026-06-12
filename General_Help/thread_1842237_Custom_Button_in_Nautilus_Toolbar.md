---
title: "Custom Button in Nautilus Toolbar"
date: 2011-09-11
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2011-09-11
I've got Nautilus-actions installed and the interface for adding a custom toolbar seems simple enough but I can't get it to work. Oh, I've gotton an icon to appear on the toolbar but when I link it to a script nothing happens. Here is the script I was testing with, just to verify I had gotten Nautilus-actions to work:

[B]touch '/media/FAT-WD-R5/script testing sandbox/emptytester'

[/B]The script does what I expect when I double click run it from Nautilus or drag it into a terminal  which is to say it creates an empty file named "emptytester" but clicking the button on the Nautilus toolbar does nothing.

I tried killall nautilus and relogging. Still doesn't work.

I'd like to solve this in a general way so I can use nautilus-actions for other stuff but for now my objective is to have a button I can click that will do the same thing as File, Create Document, Empty File. That is to say create the file, or more accurately I suppose the directory entry, and name it whatever I enter with no more steps than necessary. If I can get the button to run ANY script or command I planned on trying to write a script using zenity or dialogue to do the task. So if anyone knows some OTHER way to do this without taming nautilus-actions I'd be interested. The point is to make it as easy as possible to create and name an empty file because I do this frequently.[B]

So if anyone can point out what I'm doing wrong with Nautilus-actions or point me toward a good step-by-step tutorial on using it to create custom buttons (not just show buttons for latent unseen functions nautilus already knows how to do) or suggest another way to do this, I'd appreciate either or both. TIA.
[/B]

---

### Post by kerry_s on 2011-09-11
> script testing sandbox

you didn't escape the spaces, so yeah that won't work.

touch '/media/FAT-WD-R5/**script\ testing\ sandbox**/emptytester'

your also in the wrong section, lubuntu is a different version that use pcmanfm, there is no nautilus.


try not to use spaces in linux, better to use - or _ or . or just remember to \

---

### Post by Dreamer Fithp Apprentice on 2011-09-11
Adding the back spaces [later edit: of course I meant back **slashes**, not spaces] didn't do it but changing the folder name to eliminate the spaces and changing the script and the nautilus-actions command accordingly did. And yes, of course that's better practice anyway.  Thanks.

Sorry I clicked the wrong tag. Didn't see the "l". I don't see any way to edit that mistake out. Maybe an admin can fix it.

---

### Post by kerry_s on 2011-09-11
> **Dreamer Fithp Apprentice said:**
> Adding the back spaces didn't do it but changing the folder name to eliminate the spaces and changing the script and the nautilus-actions command accordingly did. And yes, of course that's better practice anyway.  Thanks.

Sorry I clicked the wrong tag. Didn't see the "l". I don't see any way to edit that mistake out. Maybe an admin can fix it.

hmm, maybe i got it wrong, i haven't used spaces in names for at least 10 years. :lolflag:

glad you got it working. :)

---

