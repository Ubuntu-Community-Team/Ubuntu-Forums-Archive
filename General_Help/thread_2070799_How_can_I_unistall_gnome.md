---
title: "How can I unistall gnome?"
date: 2012-10-13
forum: General Help
---

### Post by TheodoreP on 2012-10-13
I was bored and decided to go into the terminal and obtain gnome via the sudo command: sudo apt-get install gnome and it installed alot of stuff. However I realize that I don't like gnome as much as I do unity, so I go to remove via sudo apt-get remove gnome or sudo apt-get autoremove gnome and only thing is targeted. Could anyone please help me figure out how to permanently remove gnome and all programs and files associated with it?

---

### Post by cariboo on 2012-10-13
> **MasterProgram said:**
> I was bored and decided to go into the terminal and obtain gnome via the sudo command: sudo apt-get install gnome and it installed alot of stuff. However I realize that I don't like gnome as much as I do unity, so I go to remove via sudo apt-get remove gnome or sudo apt-get autoremove gnome and only thing is targeted. Could anyone please help me figure out how to permanently remove gnome and all programs and files associated with it?

You can't completely remove gnome, because Unity runs on top of it. If you have synaptic installed on your system, you can check the history, and remove the packages that were installed on that date.

---

### Post by TheodoreP on 2012-10-13
Ok, how can I get the grub menu from this ugly old looking debain screen back to the ubuntu screen that looks cleaner? As well how can I make the lightdm the default display manager and remove the gdm? That's the really reason I want to get rid of or undo what I installed. I looked in the synaptic package manager and could see where to click to get the screen to look like your screen grab, so if you could walk me through that as well. I may have a screen name of MasterProgram but I am still a noob with an affinity for computers and the only reason I went with that name is because I believe I was watching Tron or Tron Legacy when I signed up.

Thanks again for all your help!

---

### Post by cariboo on 2012-10-13
Moved to General Help, as this type of question doesn't belong in the Cafe.

---

### Post by TheodoreP on 2012-10-13
Ok, I'm sorry for posting it in the wrong section of the forum, but could you please try and help me out with my problem?

---

### Post by Lyfang on 2012-10-13
The GNOME metapackage installs many packages. Find out what programs that were installed that don't wreck Unity (that are safe to uninstall).

---

### Post by wojox on 2012-10-13
You should be able to run:
```
sudo dpkg-reconfigure lightdm
``` 
to reset it. If GDM is loaded you may have to kill it:
```
sudo service gdm stop
```

---

### Post by TheodoreP on 2012-10-13
Is there a command for the terminal that will allow for me to remove and purge several packages at once?

---

### Post by critin on 2012-10-13
Post number 2 by [[COLOR=#97310e]**cariboo907**[/COLOR]]("http://ubuntuforums.org/member.php?u=77104")  gave instructions on how to remove that day's installs.

---

### Post by TheodoreP on 2012-10-13
Alright I think I have got it back in order, however the grub splashscreen is still coming up with this ugly debian themed screen. What I want is to put it back to the ubuntu screen that is programmed into ubuntu? Any ideas, like is there a specific grub version I need and if so which is it? Is it just a file that need to modify? Oh and for some odd reason gnome classic is still an option on the login screen. Any ideas how I can eliminate that option?

Thanks for all your help.

PS.
For some odd reason even though I removed and purged the epiphany web browser from the system it still shows up in the hud. Any ideas?

---

### Post by wojox on 2012-10-14
> **MasterProgram said:**
> Any ideas, like is there a specific grub version I need and if so which is it?
[Reinstalling GRUB 2 from a Working System]("https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System")
> **MasterProgram said:**
> 
For some odd reason even though I removed and purged the epiphany web browser from the system it still shows up in the hud. Any ideas?
Try deleting your history here.

---

