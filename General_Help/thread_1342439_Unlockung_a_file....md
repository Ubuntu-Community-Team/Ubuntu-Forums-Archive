---
title: "Unlockung a file..."
date: 2009-11-30
forum: General Help
---

### Post by Himself2007 on 2009-11-30
Hello

Few hours ago I created in Windows XP a folder that has fonts in it.
This was to import through my network a set of fonts to install in Ubuntu 9.10.
This folders is in my Ubuntu share folder on my desktop.
Everything is fine and my fonts work properly.
But now that I'm finished with this folder I am not able to delete it.
When I click on "Move to trash", I have the "error while deleting" message.
And if I choose "Show more details", it says "Error removing files : permission denied".
If I right click on the files and click to properties/permissions, the "owner" is specified as "nobody".
The question : how can I change this property to be able to delete this folder?
Thanks and learning further on Ubuntu from you!

Luc

---

### Post by mkvnmtr on 2009-11-30
The file might need to be deleted on the computer it came from.

---

### Post by Himself2007 on 2009-11-30
> **mkvnmtr said:**
> The file might need to be deleted on the computer it came from.

Hello mkvnmtr

I did it before and it changed nothing.
It was still there.

Luc

---

### Post by sisco311 on 2009-11-30
never mind 

EDIT:
Sorry I misread the OP.

Did you try to press F5 to reload the content of the directory.

---

### Post by Himself2007 on 2009-11-30
Hello sisco

Yes I did it but it changes nothing.
What is the point?

Luc

---

### Post by sisco311 on 2009-11-30
Is the "Ubuntu share folder" a network share or a local directory?

---

### Post by efflandt on 2009-11-30
Open a terminal.
**cd** to the directory that dir is in.
**sudo rm -r that-dir**

Or in a terminal type **man chown** to see how to change ownership of files (which would also require sudo before the command).  While you are at it see **man rm**.

One thing you [COLOR=Red]NEVER[/COLOR] want to do is **sudo rm -r *** from / (unless you really want to erase your entire system).

---

### Post by Himself2007 on 2009-11-30
> **sisco311 said:**
> Is the "Ubuntu share folder" a network share or a local directory?


It's a normal folder with the sharing attribute to be "seen" by my other computer having windows XP.

Luc

---

### Post by Himself2007 on 2009-11-30
> **efflandt said:**
> Open a terminal.
**cd** to the directory that dir is in.
**sudo rm -r that-dir**

Or in a terminal type **man chown** to see how to change ownership of files (which would also require sudo before the command).  While you are at it see **man rm**.

One thing you [COLOR=Red]NEVER[/COLOR] want to do is **sudo rm -r *** from / (unless you really want to erase your entire system).

efflandt

You just gaved me an idea and something just seemed to work.
I guess!
I opened a terminal and type <gksu nautilus>.
By the way this is a command I used to install my fonts.
As I understood this nautilus command seemed to have special rights.
So in Nautilus I went in the desired folder and proceeded to delete "the folder".
And it worked! Vanished!
Did I do the right thing?

Luc

---

### Post by sisco311 on 2009-11-30
> **Himself2007 said:**
> It's a normal folder with the sharing attribute to be "seen" by my other computer having windows XP.

Luc

Start your file manager as root, press Alt+F2 and run:
```
gksu nautilus /
```

Navigate to the directory (/home/*username*/Desktop/*shared-dir*), right click on the directory -> Properties -> Permissions tab and set your users as the owner. Close the root file manager. 

Delete the directory.

---

### Post by Himself2007 on 2009-11-30
> **sisco311 said:**
> Start your file manager as root, press Alt+F2 and run:
```
gksu nautilus /
```

Navigate to the directory (/home/*username*/Desktop/*shared-dir*), right click on the directory -> Properties -> Permissions tab and set your users as the owner. Close the root file manager. 

Delete the directory.

sisco311

Gee!
That's amazing.
Did you see the coincidence?
We just had the same idea.
We were just writing the same solution at the same moment.
Well what can I say...Thanks!!!
And also thanks to efflandt.
Did he inspired you the same as I?

Luc

---

### Post by sisco311 on 2009-11-30
> **Himself2007 said:**
> efflandt

You just gaved me an idea and something just seemed to work.
I guess!
I opened a terminal and type <gksu nautilus>.
By the way this is a command I used to install my fonts.
As I understood this nautilus command seemed to have special rights.
So in Nautilus I went in the desired folder and proceeded to delete "the folder".
And it worked! Vanished!
Did I do the right thing?

Luc

The directory is now in the root user's Trash, you may want to empty it.

Yes you did the the right think. But be careful when you run nautilus as root.

---

### Post by Himself2007 on 2009-11-30
> **sisco311 said:**
>  But be careful when you run nautilus as root.

Tell me...what are the dangers?
As I'm not awared of.
Just to know more...

Luc

---

### Post by sisco311 on 2009-11-30
> **Himself2007 said:**
> Tell me...what are the dangers as I'm not awared of?
Just to know more...

Luc

As root you can do anything you want, you can delete/move/edit any system file, you can purge your whole OS.

That's why I try to find an alternate solution to the problem before I post instruction on how to rm files as root.

---

### Post by Himself2007 on 2009-11-30
> **sisco311 said:**
> As root you can do anything you want, you can delete/move/edit any system file, you can purge your whole OS.

This is what I thought...special rights.
I'd say more as you told me...ultimate rights!
By the way, did you see my post #11, before?

Luc

---

### Post by Himself2007 on 2009-11-30
Oh by the way...I have another question.
I usually use "SUDO" in the terminal.
But I used "GKSU".
What is the difference compared to "SUDO"?
This is a command I learned from a previous post I has been given in the forum.

Luc

---

### Post by sisco311 on 2009-11-30
> **Himself2007 said:**
> Oh by the way...I have another question.
I usually use "SUDO" in the terminal.
But I used "GKSU".
What is the difference compared to "SUDO"?
This is a command I learned from a previous post I has been given in the forum.

Luc

gksu is for GUI apps, sudo is for cli apps/commands

[http://psychocats.net/ubuntu/graphicalsudo]("http://psychocats.net/ubuntu/graphicalsudo")

---

### Post by Himself2007 on 2009-11-30
> **sisco311 said:**
> gksu is for GUI apps, sudo is for cli apps/commands

[http://psychocats.net/ubuntu/graphicalsudo]("http://psychocats.net/ubuntu/graphicalsudo")

Thanks for all your help!
It's appreciated.

Luc

---

### Post by sisco311 on 2009-11-30
> **Himself2007 said:**
> sisco311

Did he inspired you the same as I?



Not really, when I post this kind of instructions I have to think twice, just to be sure that my instructions are safe and don't harm your system. 

Like I said before running an application/command as root may be dangerous, I have to be careful too. :)

---

