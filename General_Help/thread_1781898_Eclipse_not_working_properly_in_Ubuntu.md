---
title: "Eclipse not working properly in Ubuntu"
date: 2011-06-14
forum: General Help
---

### Post by 98174 on 2011-06-14
I am trying to change a function in a JavaScript file via the "Refactor->Change Function Signature" right-click pop-up box.  When I hit 'preview,' nothing changes.

This occurs in both the official Eclipse from the Ubuntu repos as well as Eclipse 3.6.  I am currently using JavaScript Development Tools from official repo for Eclipse for 3.5 and Web Tools for Eclipse 3.6.

I have installed and am using the Sun Java VM.

I have verified that this works properly in Eclipse 3.6 on Windows.

---

### Post by timvoet on 2011-06-14
Hi,

i can't confirm if your statement is "nothing happens" as in the button doesn't do anything, or the refactoring isn't applied. but on Ubuntu, i've discovered that alot of the "button clicks" don't go through unless you set a flag in either your bash profile, or the eclipse startup script

i've added this to my .bashrc

export GDK_NATIVE_WINDOWS=1

to get eclipse to behave better.

---

