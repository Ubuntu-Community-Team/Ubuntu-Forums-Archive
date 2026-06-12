---
title: "Best place to install tar.bz2 programs"
date: 2011-05-13
forum: General Help
---

### Post by Fabled One on 2011-05-13
I decided to download Blender as a tar.bz2 file from the site instead of using synaptic (synaptic had an older version)

What is the best place to extract such a program? Right now, I just made a folder in my /home/ directory and extracted there. It works, but I want to know if that's the "right" way to do things.

I've read the explanations of linux file system folders, but this is my first practical application of that stuff, and I'm confused.

Am I supposed to put it in /usr/ or /opt/ or something?

---

### Post by papibe on 2011-05-13
You can unpack the tar wherever you want (in its own folder would be better). After that, browse the content of the unpacked folder. Most certainly, it would be text files with more instructions and details. Look for files named like README, HOWTO, etc.

Good Luck!

---

### Post by mcduck on 2011-05-13
Installing such program in your home directory is a completely valid option if you only want it installed for a certain user.

If you want to install something like that so that's it's available to all users of the system, then /opt would be a good option.

I have Blender 2.5 installed in my home directory, works fine since I'm the only user who needs Blender and having it in my home makes updates easy. If you want to, you can link the executable into ~/bin to get it included in your path, so you can launch it from command-line without having to type the full path to where you've installed it. (~/bin doesn't exist by default, but will automatically get included in your path if you create it).

---

### Post by Fabled One on 2011-05-13
Great. Thanks guys.

---

