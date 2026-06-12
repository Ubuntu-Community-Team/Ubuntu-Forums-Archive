---
title: "Help, please!  I broke Ubuntu!"
date: 2011-07-13
forum: General Help
---

### Post by BeastMode on 2011-07-13
I'm really not sure what caused my problem.  I did a full reinstall of Ubuntu on a laptop so that now that laptop only has Ubuntu on it.  Everything was going well.  I installed some apps, like Ubuntu Tweak, Docky, Kopete, Jasper, and a Mac theme.  When I restarted the computer, it went to the purple screen, then the Ubuntu splash with the five dots, and then it just goes blank.  It's still backlit, but it never makes it to the login screen.  If I hit control alt delete, it shuts down with the ubuntu splash screen again, restarts, but the same thing continues to happen.

I'm certain this is not Ubuntu's "fault", but I don't know what I did.

What did I do, and how can it be fixed?

---

### Post by BeastMode on 2011-07-13
Shameless Bump while I try to find the answer through the search...with no luck to this point.

---

### Post by dragonfly41 on 2011-07-13
Is there a ubuntu recovery option in your grub boot list you can try?

---

### Post by Quackers on 2011-07-13
Was a new kernel installed with updates?

---

### Post by ~!geek!~ on 2011-07-13
I don't know how to solve ur problem but You may try this:
Start the machine,  when grub menu shows up select the ubuntu and press 'e' key once.(I hope grub shows up with only one ubuntu also). Now Go to the second last line and remove quiet splash words using delete key. Then hit ctrl+x. 
Ubuntu should start with the black screen with text flowing down (if not, hit left or right arrow key once or twice during the boot process)

See where it stucks. You may post the last one or two lines here too or google it.

---

### Post by BeastMode on 2011-07-13
> **dragonfly41 said:**
> Is there a ubuntu recovery option in your grub boot list you can try?

No, Sir (or Ma'am).  I was able to get it to come up ONCE, but I didn't know what to do with it when I got it there.  The computer ONLY has Ubuntu on it, so I don't get that typical "dual boot" screen you would normally get on a Ubuntu install.

---

### Post by BeastMode on 2011-07-13
> **Quackers said:**
> Was a new kernel installed with updates?

I don't know.  I don't THINK so, but that one time I was able to get into the grub menu, I didn't see more than one option for kernels.

---

### Post by BeastMode on 2011-07-13
> **~!geek!~ said:**
> I don't know how to solve ur problem but You may try this:
Start the machine,  when grub menu shows up select the ubuntu and press 'e' key once.(I hope grub shows up with only one ubuntu also). Now Go to the second last line and remove quiet splash words using delete key. Then hit ctrl+x. 
Ubuntu should start with the black screen with text flowing down (if not, hit left or right arrow key once or twice during the boot process)

See where it stucks. You may post the last one or two lines here too or google it.

I'll go give this a shot right now.  I'll let you know the results.

---

### Post by BeastMode on 2011-07-13
OK, I at least now know where it hangs.  

It says "Stopping System V runlevel compatibility".

I have ZERO clue what that MEANS, but at least I know now that seems to be the problem.

---

