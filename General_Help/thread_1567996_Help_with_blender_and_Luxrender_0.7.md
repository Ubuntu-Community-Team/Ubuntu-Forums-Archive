---
title: "Help with blender and Luxrender 0.7"
date: 2010-09-04
forum: General Help
---

### Post by Mr_VeRiTy on 2010-09-04
Hi, I've been learning to use blender for a while, and i'm trying to install luxrender to create some photo-realistic stills, but When I download luxrender from their website, there is no .deb, it's just a working installation, but that means I have to copy and paste the .py script into the .blender folder in ~/ , so I did that and started blender, opened the scripts window went to luxblend  v0.7 exporter but it says "Python script error: check console." But I don't know where the script console is. How can I get luxrender to work?  


Thanks.

---

### Post by pbrane on 2010-09-04
What I do is run blender in a terminal. That's where the output can be seen.
Applications->Accessories->Terminal
then type *blender*.

When you encounter the error, minimize blender and look at the terminal screen.

---

### Post by Mr_VeRiTy on 2010-09-04
> **pbrane said:**
> What I do is run blender in a terminal. That's where the output can be seen.
Applications->Accessories->Terminal
then type *blender*.

When you encounter the error, minimize blender and look at the terminal screen.
Hmm, I tried this intending to read the terminal output, but when I run it in terminal, I don't get an error, the script works, Is there any way to get the script to work without running it in a terminal?

---

### Post by Mr_VeRiTy on 2010-09-04
Also although it works in the terminal, every time I run blender in the terminal, it forgets where luxrender is instaled, and asks me to set a new path to it, which is annoying.

---

### Post by pbrane on 2010-09-05
it shouldn't matter whether blender is run in a terminal or from a launcher or menu item. I'm not sure what to tell you here. When I have an issue with scripts in blender they fail regardless of how I run blender. Hence my original suggestion. 

Maybe check how the launcher or menu item is setup to fun blender compared to the way you ran it in the terminal.

---

### Post by Mr_VeRiTy on 2010-09-06
> **pbrane said:**
> it shouldn't matter whether blender is run in a terminal or from a launcher or menu item. I'm not sure what to tell you here. When I have an issue with scripts in blender they fail regardless of how I run blender. Hence my original suggestion. 

Maybe check how the launcher or menu item is setup to fun blender compared to the way you ran it in the terminal.

In the launchers The command to launch blender is "blender -w" (or "blender -W" for the fullscreen version) When I launch from terminal I just put blender, So I tried taking the "-w" out of the launcher and that seems to have solved the problem, thanks.

---

### Post by dwende on 2010-09-12
re Blender 2.54 and Luxrender 0.7.

My problem seems to be that blender can't find the luxblend script in the 
user prefs panel no matter where I copy it to.
If I just try and run the script from a Text Panel I get the following error:

  > File "/home/dwende/untitled.blend/LuxBlend_0.7.py", line 88
    print ">>>---- Begin profiling print for %s" % func.__name__

I have a suspicion that the wrong python version is being used.

Thanks

---

