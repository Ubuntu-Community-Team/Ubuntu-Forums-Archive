---
title: "defualt window sizes"
date: 2009-11-12
forum: General Help
---

### Post by rexxxlo on 2009-11-12
i have an asus eee 701 it runs fine but due to the 800x600 resolution some windows and programs are not made to fit it correctly i assume they are set to default to 1024x786?

one program in particular linuxdc++ has me stumped it has resize-able areas inside of the window that are adjustable some times but not others 

the click and drag border is there but it will not let me resize them 

where can i fix this ? im sure there is a setting in the program somewhere but it not in the gui so im kinda stumped 

it seems to be a programing thing and i have no idea how or where to alter that stuff to make it work better

---

### Post by Giblet5 on 2009-11-12
You have a very limited display and limited displays have limited capabilities.

There are many MANY things you won't be able to do with that display and it is perfectly reasonable for graphics applications to assume that the resolution will be 1024x768 or higher.

1024x768 was considered Very Low Resolution in 1990 and that was another millenium.

On the plus side, you saved a lot of money. So there's that.

---

### Post by rexxxlo on 2009-11-12
understood but im not asking about changing my display that is fine

im asking about the programs constraints to resizing the boxes inside of it 

it is simply not an option if more than 3 tabs are open they default to one size 

if 3 or less tabs are open all boxes resize to any size i want

i am asking about a programs limitations or preset interface options 

sorry idont know what to call it because i have never seen this spoken of

---

### Post by Giblet5 on 2009-11-12
> **rexxxlo said:**
> understood but im not asking about changing my display that is fine

im asking about the programs constraints to resizing the boxes inside of it 

it is simply not an option if more than 3 tabs are open they default to one size 

if 3 or less tabs are open all boxes resize to any size i want

i am asking about a programs limitations or preset interface options 

sorry idont know what to call it because i have never seen this spoken of


dc++ imposes "minimum geometry constraints" on its MainWindow windows. In other words, the subwindows can be just so small, and once the available screen real estate is used up, they will not respond to resize events any longer.

Your choices are bigger screen, modify the source code to remove the constraints on sub-windows and panes, or contact the dc++ dev team and ask them to provide a sub-window-minimize capability that reduces the sub-windows to an icon on their main interface background. That's how Borland used to handle this problem .. well.

If you modify the source code, it is unlikely that the sub-windows will remain useful, since they will be resizeable to 0x0 (nothing to grab, no way to do anything with it).

---

### Post by rexxxlo on 2009-11-13
That's wonderful thank you I wasn't to sure what the termenology was.

Well the funny thing is that the minimum geometry constraints only change after there is 3 or more tabs open.

I don't need an icon for each window I just need the constraints to not change.

This is very similar to nautilus when the dise bar is open showing the drives and folders like home, music, pictures and if you click the dividerbar you can make the area grow shrink or totally dissapear but they don't chage if you have more than one tab open.
 
Thanks off to google to see what I can do/learn

*ny recomended reading?

---

