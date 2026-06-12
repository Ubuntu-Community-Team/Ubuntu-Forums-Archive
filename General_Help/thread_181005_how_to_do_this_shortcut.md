---
title: "how to do this shortcut"
date: 2006-05-23
forum: General Help
---

### Post by zigoto on 2006-05-23
Hi, can some tell i to do this shortcut...for example a have installed azureus, if i want 
to start azureus i need to do this
Open the terminal and type:
```

marco@marco:~$ cd Programas/azureus/
marco@marco:~/Programas/azureus$ ./azureus

```

It is possible to create a shortcut on the Desktop, that when is clicked that programs starts??

Regards

---

### Post by Ramses de Norre on 2006-05-23
```
ln -s ~/Programas/azureus/azureus ~/Desktop/azureus
```

---

### Post by zigoto on 2006-05-23
Does not work, this create a link, and when i click, it open the bash file!
others sugestions?

---

### Post by jreyst on 2006-05-23
What I don't get is, using Gnome/Nautilus, why can't I easily create a shortcut/link via the gui? I always have to resort to using ln -s which is tedious having to open a terminal when I'm looking at a folder or file and just want a shortcut on my desktop. Maybe I'm dense. Does anyone know how to do it without having to do ln -s?

---

### Post by zigoto on 2006-05-23
it is some thing like that i want, without use the terminal...

---

### Post by aysiu on 2006-05-23
You don't have to use the command-line for shortcuts. People just give you commands because it's easier.

To make a shortcut in Gnome, middle-click-drag the folder or file to where you want the shortcut. Then select "link here."

---

### Post by Ramses de Norre on 2006-05-23
How do you mean open the bash file? In a text editor? If so do ```
chmod +x ~/Programas/azureus/azureus
```

You can right click a file in nautilus and select "make link", then copy the link to where ever you want it.

And I guess I just like the terminal ;) It does things faster for me.

---

### Post by zigoto on 2006-05-23
My problem is not to create a shortcut...i know how to do it. My problem is that when i execute this command:
```

./azureus

```
this is a bash script and if a create a shortcut he will open a text file, with the code...
For example, i have pgadmin3 installed in my pc, at first i need to go to the console and execute:
```

marco@marco:~$ pgadmin3

```
I dont like to have a lot of terminals with this aplications, i want to click on a icon and the aplication start...For pgadmin3 i resolve it, i only need to go to the desktop,click on the rigth mouse buttom and have choose create starter(in portuguese "criar iniciador") and on the window i wrote pgadmin3...and it works, i have tried for azureus but does not work...

---

### Post by jreyst on 2006-05-23
[QUOTE=aysiu]You don't have to use the command-line for shortcuts. People just give you commands because it's easier.

To make a shortcut in Gnome, middle-click-drag the folder or file to where you want the shortcut. Then select "link here."[/QUOTE]
I know and am comfortable using ln -s but I wasn't aware you could middle-click and create a shortcut that way. I'll try it when I get home then, thanks!

---

### Post by zigoto on 2006-05-23
Another thing that i want to do, on windows XP i press shift+delete and the file is removed completed without going to the recycle bin...how can i do it on ubuntu...
other thing, for exemple i waant to do a keyboard shurtcut, for example for show the Desktop i press <control><alt>d but i want to do Super_L d,when i go to the keyboard shortcut configuration when i press Super_L he dont let me press Super_L+d

It is possible to use Super_Ld

jreyst
middle-click-drag the folder or file to where you want the shortcut, this work;) 

Regards!

---

### Post by Bazon on 2006-05-23
[QUOTE=zigoto]Another thing that i want to do, on windows XP i press shift+delete and the file is removed completed without going to the recycle bin...how can i do it on ubuntu...[/QUOTE]
In Nautilus you can enable a contextmenu option to directly delete files:
In Nautilus, Go to (words may vary, I only translated from german translation....): *Edit > Options > Behaviour > Trash* and enable the delete option there.

---

### Post by zigoto on 2006-05-23
Bazon thanks!
I have do it!
Regards!

---

