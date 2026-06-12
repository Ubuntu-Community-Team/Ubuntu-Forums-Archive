---
title: "Do I really have an unfixable problem?"
date: 2009-08-04
forum: General Help
---

### Post by malibujohn on 2009-08-04
I posted in the Video forum that I had a problem with a green Ubuntu desktop.
 All the blacks are displayed green. When I receive mail with attachments I have to forward them to my Widows XP side for viewing.
 I had this problem before. I am not sure if it was fixed or I gave up asking.
 I have posted again but still get no response. The windows side displays without a problem so I do not think it is a hardware issue.
 Can anyone out there help?
 John

---

### Post by CrusaderAD on 2009-08-04
When you say windows side, are you referring to another operating system on the same machine? It must be an issue with your graphics card / driver if that's the case.

---

### Post by Locutus_of_Borg on 2009-08-04
Check your gamma settings under display properties

---

### Post by malibujohn on 2009-08-05
> **raptormanad said:**
> When you say windows side, are you referring to another operating system on the same machine? It must be an issue with your graphics card / driver if that's the case.
Yes. My computer has a dual boot capability. I have Widows XP Pro for games & Linux Ubuntu for accessing the web & general computer duties.
 The windows side appears normal but the Linux side has the aforementioned Black = green problem

---

### Post by malibujohn on 2009-08-05
> **Locutus_of_Borg said:**
> Check your gamma settings under display properties
I have checked the menu's in Applications, Places, & systems. I cannot find any reference to "display properties". Although I am not a Newbie per se,I am not educated as to the working & commands of Linux.
 How do I check the "gamma Settings"?.
 Thanks John

---

### Post by malibujohn on 2009-08-05
While searching for "gamma settings", I came across an update for the graphics card. I performed the necessary steps. It resulted in a white screen with no access to turning off the computer. After pressing the "on " button I was able to apply the sudo commands & got my Ubuntu screen back. 
I still have a green desktop screen

---

### Post by CatKiller on 2009-08-05
> **malibujohn said:**
> How do I check the "gamma Settings"?.

If you're using the proprietary NVidia driver, with System &#8594; Administration &#8594; NVidia X Server Settings &#8594; X Server Color Correction. Or from the command line with **xgamma**. I have not idea what tools the proprietary Ati driver comes with, since I've never used it.

---

