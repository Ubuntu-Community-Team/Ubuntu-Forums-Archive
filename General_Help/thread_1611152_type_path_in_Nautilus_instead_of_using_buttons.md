---
title: "type path in Nautilus instead of using buttons"
date: 2010-11-01
forum: General Help
---

### Post by tokoro on 2010-11-01
I have never posted here because i never cared to read the rules or understanding how the forum actually works.

That being said, before 10.04 there was a button on nautilus that let you change the path buttons for a text box so you could type the path you wanted to go.

[IMG]http://www.dedoimedo.com/images/computers/ubuntu-8.10-nautilus-tabs.jpg[/IMG]

Now that it has been removed how can i get it back? I know you can use control L to get a text box but pressing control L again does not return the buttons.

Aso if there is something wrong about my post let me know

---

### Post by spoon_ on 2010-11-01
Pressing ESC after pressing CTRL-L will get you back into button-mode.

But to answer your question, I don't know how to enable the toggle button that existed in previous versions.

---

### Post by seanos on 2010-11-09
This is so annoying!  Both modes are useful so why take away the toggle?

---

### Post by seanos on 2010-11-09
Attached is a Nautilus script to toggle between "Location Entry" (i.e. path via text box) and the "Pathbar" (path navigation via buttons).  Not as good as a toggle button, but it'll do for now.

Extract it to ~/.gnome2/nautilus-scripts and make it executable.  Then in Nautilus you might need to right-click on some blank space and choose "Open Scripts Folder"  from the Scripts menu to make it appear in the Scripts menu.

---

### Post by uRock on 2010-11-09
Crtl+L will give you the text address bar.

---

### Post by Habitual on 2010-11-10
gconf-editor
/apps/nautilus/preferences/always_use_location_entry

check empty box.

If set to true, then Nautilus browser windows will always use a textual input entry for the location toolbar, instead of the pathbar.

---

### Post by The Cog on 2010-11-11
<rant>I have to say, I really don't understand why they chose to remove that toggle option. Just another paper-cut from Gnome.

Maybe they are trying to persuade people to switch to KDE or XFCE instead. Come to think of it, perhaps it is time for me to try KDE again. Last time I looked it was a real wreck, but I keep hearing that it's getting better.
</rant>

P.S. Why not time to try XFCE? Because I'm currently **on** XFCE. Despite being lightweight and fast, it actually seems to have more options than Gnome in many places.

---

### Post by Habitual on 2010-11-11
I loved Xfce and used it for 2 years exclusively, but lately on Xubuntu and Fedora, my thumb drives would mount with a label of ```
?PNG:?
``` on the destop and I couldn't change it.

It mounted correctly at right place, just the label on the desktop made me switch from Fedora Xfce to Ubuntu Gnome.

Silly, the  little things get to us.

---

### Post by itsols on 2010-11-20
hmmm... gonf-editor had no effect.

Furthermore, last night I saw the pencil icon and now it's gone! I think I made a mistake getting on to 10.10... There are many other  issues as well...

---

### Post by SonicSteve on 2011-04-29
I know this is an old dead thread....

In case anyone has updated to Natty 11.04 I can confirm that this Gconf-editor hack still works. I also absolutely need to be able to type a path. Windows share browsing is too unreliable. Not a fault of Ubuntu but being able to type a path instead of browsing solves the reliability issue (Microsoft's fault).

---

### Post by itsols on 2011-04-29
I really don't know how this was resolved and I'm still on 10.10.

Usually, when I first click in the directory while on nautilius, if I start keying in a path, a textbox appears and my entry is seen in it. I don't recall doing anything special to get this back. So I presume it may have been 'one of those little bugs' :)

BTW, I got the upgrade alert as well for 11.04 but I did not want to take a chance until I heard from someone using it first. I think I'll wait for a while before diving in - smiles...

---

### Post by SonicSteve on 2011-04-29
> **itsols said:**
> I really don't know how this was resolved and I'm still on 10.10.

Usually, when I first click in the directory while on nautilius, if I start keying in a path, a textbox appears and my entry is seen in it. I don't recall doing anything special to get this back. So I presume it may have been 'one of those little bugs' :)

BTW, I got the upgrade alert as well for 11.04 but I did not want to take a chance until I heard from someone using it first. I think I'll wait for a while before diving in - smiles...

I don't upgrade immediately I usually wait a few weeks minimum. With the big changes to desktop GUI I decided to test the 11.04 out on a spare machine. I haven't decided yet if I like the changes or not. With some tweaking I may keep it.

Edit,,,

To be clear I never actually use the upgrade option. I use the separate home partition method and install a fresh OS each time then add back my programs and tweak till I like it.

---

### Post by kirby33 on 2012-06-20
Hello everybody!

I have write a patch for nautilus 3.4.2 (Ubuntu 12.04).
This patch adds the Up button and a toogle button for the location bar.
The shortcut <control>L is replaced by F12 and works in toggle mode.
The "Search" label icon has been removed.

[https://launchpad.net/nautiluspatchtogglelocationbar/+download](https://launchpad.net/nautiluspatchtogglelocationbar/+download)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=219009&stc=1&d=1338475048[/IMG]

---

### Post by oldos2er on 2012-06-20
Please don't bump old threads.

---

