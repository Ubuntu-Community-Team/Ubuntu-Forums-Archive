---
title: "Keyboard layout in LinuxMint"
date: 2010-12-27
forum: General Help
---

### Post by DeMus on 2010-12-27
Hi,
I re-installed LinuxMint 9 Isadora today (based on Lucid), after having tried the LMDE10 version which is based on Debian instead of Ubuntu. During installation I choose the keyboard layout: "USA with Eurosign on 5" (see picture).
I do get however the layout USA as well. This one I never use, I always use the one with the Eurosign on the 5. Because I have 2 different layouts now, on the right side of the lower panel I see the text USA. It's a button with which I can switch between the two layouts. I don't need that and I don't want it.
I can erase the USA layout, but the next time I log in it comes back.
How can I make the USA layout disappear for good? With earlier installs I never had this, now I can't get rid of it.
Who can help please?

---

### Post by bobcollard on 2010-12-27
You should be able to highlight the "USA" on the second line and click [Remove] without losing the combined "USA with Eurosign on 5"

---

### Post by DeMus on 2010-12-27
> **bobcollard said:**
> You should be able to highlight the "USA" on the second line and click [Remove] without losing the combined "USA with Eurosign on 5"

Thank you Bob for your answer, but if you read my post well, you can read I can erase the USA layout BUT with the next boot it is back. Somehow it always keeps coming back.
How do I erase it permanently?

EDIT: I can also push the button: "Restore to Defaults." So, apparently the default situation is one layout, the one I want. Nevertheless the second one comes every time I boot. Why, how?

---

### Post by Andy Meier on 2010-12-28
"USA with Eurosign on 5" is a variant of the "us" layout,
means contained in the "us" file,
therefore I guess, you can not get rid of "us" layout...

perhaps read my thread from today about keyboard layout...
[http://ubuntuforums.org/showthread.php?p=10286878#post10286878](http://ubuntuforums.org/showthread.php?p=10286878#post10286878)

---

### Post by DeMus on 2010-12-28
> **Andy Meier said:**
> "USA with Eurosign on 5" is a variant of the "us" layout,
means contained in the "us" file,
therefore I guess, you can not get rid of "us" layout...

perhaps read my thread from today about keyboard layout...
[http://ubuntuforums.org/showthread.php?p=10286878#post10286878](http://ubuntuforums.org/showthread.php?p=10286878#post10286878)

Thanks for your answer. Somehow it makes sense what you write, but when I had the same OS installed before I did not have that annoying thing in my panel. Maybe I also had 2 layouts then and never knew I had them, but I did not have the choice in the panel. Do you know how to get rid of that?

---

### Post by Andy Meier on 2010-12-28
as I read: the default keyboard will annoy you as it remains always... 
   If you like to get rid of this, edit
   /var/cache/gdm/$USER/dmrc
   and place any existing layout as your new default: "Layout=xxx"
   then reboot..
if you can find out, how to name your variant (here xxx), this should work also in your case!

---

### Post by DeMus on 2010-12-28
Thank you Andy for your help. It's just that it doesn't help me much. No matter what I do the choice between the two layouts keeps coming back.
When I click on the button "Reset to Defaults" I have one choice: the one that I want. So, obviously I did set one choice during installation. Where does the other one coming from? Can there be a program which does it, a program I didn't have before? I have used Linux Mint 9 before already and I never had this. So where does it come from now?
I hate it that I can't find it. I searched my home folder for the word US and didn't find anything which indicates to the problem I have at the moment.

EDIT: the keyboard layout name is printed in the Notification area. Strange fact is that I did not install the Notification area, it's not in Synaptic at all. I can choose to add or to remove it from the panel, but since I want to see the other items I need to have it added to the panel.

---

### Post by Andy Meier on 2010-12-28
ok just tried with Mint on my laptop:
indeed I was not able to get rid of "us", 
or to find out how to specify a variant in /var/cache/gdm/$USER/dmrc

setxkbmap -layout us -variant euro
gives correct result: means your variant must be declared as "euro" 
Place this somewhere in a startup procedure...

or create your own layout according my description!
this enables you to include other useful keys also,
quick and easy to do, and it works reliable!

---

### Post by DeMus on 2010-12-28
> **Andy Meier said:**
> ok just tried with Mint on my laptop:
indeed I was not able to get rid of "us", 
or to find out how to specify a variant in /var/cache/gdm/$USER/dmrc

setxkbmap -layout us -variant euro
gives correct result: means your variant must be declared as "euro" 
Place this somewhere in a startup procedure...

or create your own layout according my description!
this enables you to include other useful keys also,
quick and easy to do, and it works reliable!

Hi Andy, I couldn't quite follow you in your last post, but I tried some stuff. I first edited the dmrc file and replaced layout us into layout euro. This gave me an extra choice, making it 3 layouts to choose from. Then I placed a '#' in front of the line which didn't work at all. After reboot the '#' sign was gone. So I deleted the whole line and that did the trick. Now after rebooting I have one keyboard layout and I don't see the USA text in my lower panel anymore.

Thanks for all your help. Glad this problem has been solved.

---

### Post by DeMus on 2011-01-07
I marked the thread as unsolved again since the keyboard choice came back and this time I can not make it disappear.
I did a normal installation, choosing the US keyboard with the Euro sign on the 5. Just as I have tens of times before with other OS'es. Now I always get the choice between this one and the normal US keyboard. The choice can be done through an item in the notification area in my lower panel. I don't want to have the choice, I just want to have one keyboard (with the € on the 5) and that's it. How do I do that and why does it always come back with the choice I don't want?

---

