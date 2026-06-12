---
title: "Is there any way to add run application by entering.."
date: 2006-02-22
forum: General Help
---

### Post by darknightuk on 2006-02-22
Is there any way to add run application by entering a command to the main gnome menu i know i can add this to the panel?

---

### Post by audax321 on 2006-02-22
You should be able to add it by going to Applications > System Tools > Applications Menu Editor and adding the appropriate command. But I can't seem to find out what the command is.. :-k 

I do know that it should come up if you push ALT+F2 on your keyboard. There used to be a Run Application shortcut in Hoary but it was replaced with the keyboard shortcut in Breezy. If you can get a hold of a Hoary LiveCD, try booting with it and then install SMEG and see if you can find out what command that menu shortcut is running. Then all you have to do is boot into Breezy and add the same command. I'll look for Hoary LiveCDs, but I don't think I have any.

---

### Post by darknightuk on 2006-02-22
[QUOTE=audax321]You should be able to add it by going to Applications > System Tools > Applications Menu Editor and adding the appropriate command. But I can't seem to find out what the command is.. :-k 

I do know that it should come up if you push ALT+F2 on your keyboard. There used to be a Run Application shortcut in Hoary but it was replaced with the keyboard shortcut in Breezy. If you can get a hold of a Hoary LiveCD, try booting with it and then install SMEG and see if you can find out what command that menu shortcut is running. Then all you have to do is boot into Breezy and add the same command. I'll look for Hoary LiveCDs, but I don't think I have any.[/QUOTE]thanx didn't know bout the alt+f2 i will av 2 find a cd somewhere

---

### Post by audax321 on 2006-02-22
I found a LiveCD in my desk and gave it a try, but the Run Application shortcut doesn't show up in SMEG. So, then I dragged it to the panel and  made a launcher icon. But when I right click the launcher it has no Properties dialog so I can't tell what the command that brings up the run dialog is. Sorry, don't really have any other suggestion for you. :-k

---

### Post by engla on 2006-02-22
By strange ways I think I found the solution in [this thread]("http://ubuntuforums.org/showthread.php?p=487717&highlight=run#post487717").

Suggested solution: (I haven't tried this)
1. Install the 'openbox' package. No need to use the actual program, but it will install the small needed tool we need.
2. Now you can create a launcher with the command 'gnome-panel-control --run-dialog' which should display the run dialog.


I've heard rumors that there is another simpler solution, though...

---

### Post by audax321 on 2006-02-22
I found another solution here:
[http://darkness.codefu.org/wordpress/index.php?s=gnome-run](http://darkness.codefu.org/wordpress/index.php?s=gnome-run)

It's basically a program you compile and then just link to the binary and the run dialog pops up. I went ahead and compiled it so if you want the compiled binary here it is: [ATTACH]6348[/ATTACH]

---

### Post by darknightuk on 2006-02-22
thankx:KS

---

