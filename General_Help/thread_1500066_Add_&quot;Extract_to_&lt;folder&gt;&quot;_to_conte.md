---
title: "Add &quot;Extract to &lt;folder&gt;&quot; to context menu"
date: 2010-06-02
forum: General Help
---

### Post by nano278 on 2010-06-02
There's any way to add the "Extract to <folder>" to context menu in Nautilus and Gnome Commander where <folder> is de name of the archive that I want to extract?

---

### Post by Rubicon421 on 2010-07-20
Did you ever find a way to do this? I'm looking for the same thing. I'll update the thread if I find anything.

---

### Post by valbaca on 2010-07-20
There is already an "Extract here" option.

---

### Post by Rubicon421 on 2010-07-20
Yes, but there is not an "Extract to <Folder-Name of Archive> option. If the Archive's root directory has several files this makes a bit of a mess in the directory it is extracted to.

---

### Post by endotherm on 2010-07-20
the Extract Here option does that already. it's differant from winrar, where "here" means within the folder that contains the archive. ubuntu will always try to extract into a folder named after the archive unless you specify otherwise in the archive manager.

---

### Post by Rubicon421 on 2010-07-20
> **endotherm said:**
> the Extract Here option does that already. it's differant from winrar, where "here" means within the folder that contains the archive. ubuntu will always try to extract into a folder named after the archive unless you specify otherwise in the archive manager.

Huh, I guess I should have tried it first! Thought it would be similar to Windows. Just tried it and it does make it's own folder!

---

### Post by Vaphell on 2010-07-20
on a sidenote - you can install nautilus-actions and add your custom stuff to the context menu. if that 'extract to' didn't work like you wanted already, you could easily create proper menu entry yourself.

---

### Post by valbaca on 2010-07-20
> **Rubicon421 said:**
> Huh, I guess I should have tried it first! Thought it would be similar to Windows. Just tried it and it does make it's own folder!
 
 If this worked, please help other users by marking this thread as [Solved].

To do this, go to [COLOR=red]_Thread Tools _[/COLOR][COLOR=black]in the top right and click on "Mark thread as solved"[/COLOR]

Thank you

---

### Post by mikethehard on 2010-12-22
Hi,

I think I found a possible solution for this. 

I download movies as RAR in separate parts to my downloads folder and want to be able to extract them to my Videos folder to share on the network.

Right click on a RAR and choose 'Open with Another Application' then use a Custom Command:

> file-roller -e "/home/michael/Videos/"

Now when I click on part 1 of a set or RARs it will extract the whole movie to my Videos folder.

Hope this helps.

---

