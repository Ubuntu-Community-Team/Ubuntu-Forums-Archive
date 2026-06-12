---
title: "I'd like to create shortcuts to network shares on the desktop."
date: 2011-03-11
forum: General Help
---

### Post by Roasted on 2011-03-11
I'm in a situation where we might see a few Ubuntu machines added to the fleet of systems here at work (school district). A problem that I'm facing is I would like to do a very, very simple task in Ubuntu, which is to create a shortcut share to a network resource.

On Windows, you can right click - new - shortcut - \\server\share, done. Then when you click on it, you have the appropriate permissions within the folder based on what permission settings exist on the actual server where the folder resides.

In Ubuntu, the closest I can get is to create these shortcut links on the left side of Nautilus in the bookmark pane. Here's the part that rages me to no end. If I log out and back in, they're ALL renamed to "smb". LOL. What. Really?

SO... I'd like to create shortcuts for several network resources. I'd like these links to either be within the Nautilus bookmark area, or within the desktop itself. Ubuntu is on the domain, so it'll already have domain credentials with appropriate permissions linking accordingly.

How can I make this work?

---

### Post by Morbius1 on 2011-03-11
> Here's the part that rages me to no end. If I log out and back in, they're ALL renamed to "smb". LOL. What. Really?
[] You can rename the bookmark. Right click the bookmark > Rename

[] You can also set up a Desktop Launcher - for example:

Right Click the desktop > Create Launcher >

Type: Location
Command: smb://192.168.0.100/share-name

[] Finally you could use Gigolo so that it will automount when the server is up and you will get a mount ICON automatically:
[http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

---

### Post by Roasted on 2011-03-11
Right click desktop - create launcher - smb://server/share sounds exactly like what I want. It threw me through a loop first as I got an error, but I have it working now. I just had to select "Location" in the drop down menu, as it was "Application" by default.

Thanks!

---

### Post by Roasted on 2011-03-11
UPDATE - NOT solved. When I add these links to /etc/skel and boot up into a new user, the links are just dead and won't fire up accordingly. I'm back at square one and stuck.

If we're going to have Ubuntu on the network here, I NEED this *very* simple solution. A shortcut on the desktop to a network resource.

How can I do this...

---

### Post by Roasted on 2011-03-14
Up. :popcorn:

---

### Post by Roasted on 2011-03-14
Alright, we got it.

What I did was I mounted the share in Nautilus using smb://server/share. I noticed that because of the spaces in the share, Ubuntu was entering %'s in there. So I just copied that entire line and used THAT as the actual "command" with the custom launcher. So I did:

Right click desktop
Create launcher
Drop down list - "Location"
Paste in command, name it, choose icon
Done

I added it to /etc/skel and it carries over to the new users accordingly. Likewise, because this box is on the domain, they automatically are set up with the permissions on the Windows server. So if Bill Gates logs in, he cannot get to Steve Jobs' share on the server, etc.

Solved.

---

