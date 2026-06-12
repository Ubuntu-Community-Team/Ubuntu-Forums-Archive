---
title: "Problems with save-file dialog window default size"
date: 2012-05-16
forum: General Help
---

### Post by Dennis N on 2012-05-16
Computer in question is a laptop with screen size is 1280 x 800.

The "save" or "save as" dialog box for the text editors in Lubuntu 12.04 is so large that the portion with the cancel and save buttons is partly or completely beneath the lower panel. 

I first noticed this with Leafpad. Then I installed and tried gedit, and it has the same problem. Then I tried Libre Office Writer, and the dialog there is so large that the cancel and save buttons are not visible at all. 

Resizing the window is possible by dragging a top corner (the bottom corners are not visible) and moving the window up, but this resizing is NOT persistent across saves. And who wants to have to do that every time? 

The question is: How can I set the default size of this save file window so that this resizing is not necessary with every save of a new file? Where are the default settings kept?

Thank you.

*Additional note: I have Lubuntu 11.04 still installed on a separate partition, and the save windows there resize and stay resized, even across reboots, so something was lost since then.*

---

### Post by cortman on 2012-05-16
Sounds like your screen resolution isn't correct.
Could you post a screenshot of the problem so we can visualize it better?

---

### Post by Dennis N on 2012-05-16
I am attaching a screenshot of this issue. Original size 1280 x 800 resized to 900 x 563 to be within guidelines.

Libre Office has an even worse situation with the buttons out of view.

The save dialog can be resized temporarily, but doesn't save its geometry across saves or reboots. It opens again like this each save. In Lubuntu 11.04, it does save its geometry even across boots.

The Leafpad program window DOES save its size from the last use.

What I am looking for is a configuration file to fix this default size of the save dialog.

---

### Post by cortman on 2012-05-16
I see what you're saying.

I really doubt this is something you can globally set in Ubuntu; I imagine it's specific to each program.
I'm not sure that there is any way to do that other than get the program source code and look in it. I googled around a goodish bit and found a couple questions similar to yours with no answers, and no help elsewhere.
Maybe someone else has an idea.

---

### Post by Dennis N on 2012-05-17
If anyone is curious, I discovered the cause of the save dialog buttons falling behind the panel as discussed in post #1. 

As you increase the default font size in Lubuntu 12.04, the height of the save dialog box actually increases. For my 1280 x 800 laptop, the maximum font size is 11 to keep the 'cancel' and 'save' buttons visible above the panel. Doesn't matter what font face you choose. If you have more than 800 px screen height, you could choose a bigger default font.

The two attachments show the same save dialog with size 11 font and size 12 font. With size 12, the cancel and save buttons are forced behind the panel and hidden. The application is Libre Office Writer.

---

