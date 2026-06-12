---
title: "deleted photorec backup files taking up disk space."
date: 2011-03-13
forum: General Help
---

### Post by MadTeaParticipant on 2011-03-13
I used photorec to recover lost files and it brought up 70gb worth of files, when I was done looking through them I deleted these files. 
but these files still seem to be taking up my disk space. When I try to access my trash bin with root I get a message that reads...."The folder contents could not be displayed. sorry, could not display all the contents of "trash": operation not supported."
if I open my trash bin when I'm not in root, the bin is empty. 

How do I free up my disk space?

---

### Post by MadTeaParticipant on 2011-03-14
anyone know?

---

### Post by MadTeaParticipant on 2011-03-14
bump

---

### Post by agent319 on 2011-03-31
I had the same problem and then I realized that when you use photorec it will ask for sudo access to get to the drive (in most cases). If you delete the files through a sudo nautilus session (this is what I did >.<) they will go to the root trash and make it so that your regular user does not have access to these files. 

What you will need to do is run a "sudo gnome-terminal" and then navigate to /root/.local/share/Trash/files rm the files that are there and you should be all set!

---

### Post by scubscub on 2011-09-16
Hi all,  I have this problem after trying to recover files with Photorec as well.  Problem is, the /root/.local/share/Trash/files folder is full of directories (e.g. recup.dir.2.2.2) which I can't rm.  Each of these has 500 files inside it, do I have to go into each of about a hundred directories and delete 500 files individually?  Or is there a way I can simply get rid of all the directories in the root Trash?  

BTW I also tried this by dragging Nautilus onto a sudo launcher, then navigating to /root/.local/share/Trash/files.  Still couldn't delete anything, because when I selected "move to Trash" stuff would reappear in exactly the same folder I was trying to delete it from...

---

### Post by scubscub on 2011-09-16
SUCCESS!!  If like me you are having trouble with deleting directories in the root trash, here is a way that worked.

First, I have a gksudo launcher in my gnome panel, this allows me to drag programs that will then launch in sudo. This way you can use the GUI and not mess with the command line (sorry, purists).

So I drag nautilus to the launcher and navigate to /root/.local/share/Trash/files. Select all, and maximize permissions.

Then I drag another instance of nautilus to the launcher, and created a folder called "Junk" on my desktop.  This folder also has to be opened in sudo, or you can't copy the trash files into it.

Back to the /root/.local/share/Trash/files folder, select all, and drag them into the Junk folder on the desktop. The root trash is now empty, and all the files are off the root and on the desktop. Close all your nautilus windows that are in sudo! The Junk folder or its contents can now be moved to your regular trash, and the trash emptied.

---

### Post by coldraven on 2011-09-16
scubscub, why not just select all with Ctrl+A then press Shift+Delete. They get deleted without going to the trash can.

---

### Post by The Cog on 2011-09-16
> This way you can use the GUI and not mess with the command line (sorry, purists).I don't think it's being purist. It really wouldn't occur to me to use the GUI for that - it's just quicker and easier in the command line. 

On top of which, if you're telling others how to do it in the GUI, it's **gksu nautilus** in Ubuntu, **kdesu dolphin** in Kubuntu, **gksudo thunar** in Xubuntu, and I don't know what in Lubuntu. And that's before describing how to see hidden directories.

> scubscub, why not just select all with Ctrl+A then press Shift+Delete. They get deleted without going to the trash can.Same as on windows. I am in the habit of doing that, and just once in a while, I really, **really** wish I hadn't. :o

---

### Post by scubscub on 2011-09-16
> **coldraven said:**
> scubscub, why not just select all with Ctrl+A then press Shift+Delete. They get deleted without going to the trash can.

Ah, I didn't know I could do that.  But who wants a simple, quick answer when an indirect, complicated one will suffice?


And Master Cog, thanks for the corrections.  The only real problem with the command line is, you have to know the commands.

---

