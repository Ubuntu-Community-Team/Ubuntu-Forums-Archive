---
title: "Still trying to kill Recently Used"
date: 2012-09-02
forum: General Help
---

### Post by arsenic23 on 2012-09-02
Alright.  I have been trying to completely stop all items from being added/shown in the Recently Used heading of the open dialog.  I'm using xfce with nautilus rendering my desktop and marlin as my file manger.  I started with an ubuntu install and have xfce, mate, cinnamon, gnome3, and unity all (still) installed.  I also have enough of KDE installed to meet the library requirements for programs like Konversation.

Here's what I've done so far:

I have ran an apt-get purge on 'zeitgeist*'.  Then I went and looked up all of the locations where it could store information and removed them. 

Then I emptied the contents out of ~/.local/share/recently-used.xbel and made it uneditable with ```
sudo chattr +i ~/.local/share/recently-used.xbel
```This has kind of worked.  If I open so many files in gedit (or any program) they still remember them until all instances of that program are closed.  I really need to get this completely disabled; it makes me so angry.

[COLOR="DimGray"]If you are wondering why this bothers me so much, please imagine this:  You have a wife or husband who sits in the kitchen all evening and when you open the fridge and get something out they write down the time and the item you removed from the fridge.  Why would they do that?  It's infuriating![/COLOR]

---

### Post by emarkay on 2012-09-02
Delete Zeitgiest with Synaptic, and install Bleachbit?

---

### Post by dragonfly41 on 2012-09-02
[http://ssokolow.com/gtk-recent-scrubber/#stealthy](http://ssokolow.com/gtk-recent-scrubber/#stealthy)

---

### Post by dcstar on 2012-09-03
Be warned that things like VMware Workstation/Player utilise the "Recently Used" file to list client VMs.

Clear out or lock that file and you lose that functionality.

---

### Post by jmate24 on 2012-09-03
take and create a new folder in ~/.local/share/
then delete the recently-used.xbel and Rename the folder by right clicking on it and copy and pasting: recently-used.xbel. 

Because if the file is a folder then the os cannot write to it.

best of luck.

jmate24

---

### Post by arsenic23 on 2012-09-03
> **dcstar said:**
> Be warned that things like VMware Workstation/Player utilise the "Recently Used" file to list client VMs.

Clear out or lock that file and you lose that functionality.

That's interesting; and terrible; and luckily won't effect me on this machine.


Also, I would like to repeat that I have completely removed all traces zeitgeist from my system and have rendered recently-used.xbel completely uneditable even by root.

My problem seems to be happening in memory.  If I open gedit in one workspace and then open some files in another instance of gedit I get a list of those files in the open dailog of any instance of gedit until every instance of it has been closed.  This is true for any program using GTK open dailogs.

---

### Post by ssokolow on 2012-10-30
> **arsenic23 said:**
> That's interesting; and terrible; and luckily won't effect me on this machine.


Also, I would like to repeat that I have completely removed all traces zeitgeist from my system and have rendered recently-used.xbel completely uneditable even by root.

My problem seems to be happening in memory.  If I open gedit in one workspace and then open some files in another instance of gedit I get a list of those files in the open dailog of any instance of gedit until every instance of it has been closed.  This is true for any program using GTK open dailogs.

Did you try [http://ssokolow.com/gtk-recent-scrubber/](http://ssokolow.com/gtk-recent-scrubber/) as dragonfly41 suggested?

When I was writing it (I'm the author), I noticed that GtkRecentManager seems to notify all running applications to re-read the on-disk file whenever it's used to remove an entry.

Assuming gedit doesn't behave fundamentally differently from all the GTK+ apps I use, that'd mean that, with my script running, undesired entries would vanish from the recent list 1-2 seconds after being added.

(And it *is* prefix-based so, if you really want to disable the list completely, you can just tell it to scrub all entries with paths beginning with "file:///", "http://", and so on.)

---

### Post by James Paige on 2012-12-10
Is there a way to stop Recent Files from being the default ocation of the filepicker?

I see that I can delete the list of recent files, but why is it the default location for File-Open? Can anything be done about it? (I have been googling this extensively, and finding no answers)

---

