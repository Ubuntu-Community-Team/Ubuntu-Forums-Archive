---
title: "Mount&amp;Blade can't find dinuput8.dll"
date: 2010-03-11
forum: General Help
---

### Post by LauriT on 2010-03-11
The first time I installed Mount&Blade, my character couldn't turn 360 but I fixed it with this:

> How to solve mouse problem
by Dany on Friday June 26th 2009, 2:25
- download the hacked dinput.dll.so from: bugs.winehq.org/attachment.cgi?id=15550 

- overwrite dinput.dll.so found in /usr/lib/wine on 64bit machines (or maybe /usr/lib/wine on 32bit) with the hacked one 

- launch M&B application with these commands: 

cd /home/user/.wine/drive_c/Program Files/Mount&Blade **or the path of the folder the exe is locate into** 
export WINEFORCEMOUSEWARP=yes; wine ./mount\&blade.exe 

Now i can turn 360° and more... 

It works for me.

I messed my computer and had to re-install wine and Mount&Blade but now when I replace dinput.dll.so with the new file I get error > Cannot find DINPUT8.dll, please re-install this application 

How to fix this problem?

---

### Post by Intrepid Ibex on 2010-03-11
The wrong place for this kinda problem but I take it you should also download the dinput8.dll from some (that should be a trusted) dll site.

---

