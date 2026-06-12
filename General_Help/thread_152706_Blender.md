---
title: "Blender"
date: 2006-03-30
forum: General Help
---

### Post by Micro$oftWinblows on 2006-03-30
I tried installing Blender 2.41 straight from a tar file but couldn't get it to work. Noob here.

I went to install Blender 2.41, the latest version, from the package manager but only found 2.37a there. How often are packages updated, or is this something I have to do myself?

---

### Post by graigsmith on 2006-03-30
it would be easiest to use the blender thats already in synaptics. it would be updated every 6 months or so.

how did you try to install it?  double clicking it, probably wont work.

most likely you will need to run the file from the command prompt.  you may even need to set run permissions on the file that got extracted.

tell us the name of the file inside the archive, and try running the file from the command prompt, tell us exactly what you type.

To run something from the command line, you navigate to the folder you extracted it to. if you extracted the file to the desktop. you would type this to get to that directory from the command prompt.  i dont know how much you know about command prompts so here's how you use some of the basic commands that will let you run that file from the command prompt.  also take note, you dont have to type everything out.  if you type half of something, and hit tab, it will autocomplete it for you.  like if you type cd Desk and hit tab, it will fininsh it as Desktop.  Also remember, that the command prompt in linux is case sensitive, so dont type desktop, it is Desktop.

```

cd ~    <this takes you to your home directory.
cd Desktop
ls  <this lists the files on the desktop.
cd <type the directory name here>

<then to run the file you type>

./<name of file>
```
tell us any error messages.   or just use the version in synaptics, there probably isn't much of a difference between those 2 versions.

---

### Post by Micro$oftWinblows on 2006-03-30
Argh I was too late. Sorry, problem solved.

I manage to change the Breezy repositories to Dapper ones and installed Blender 2.41 from there.

Thanks though. :)

---

