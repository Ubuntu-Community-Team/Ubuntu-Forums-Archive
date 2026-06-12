---
title: "After click Places tab no Nautilus"
date: 2011-04-07
forum: General Help
---

### Post by jorgeaz on 2011-04-07
I am new to ubuntu but I love it.....
I don't know what I did in the terminal trying to encrypt files but now when I click on something in places tab to open it using Nautilus, it does not, instead  it open in a tab of Mozilla Firefox, I don't like it. How can I revert back to Nautilus like normally is ?
Thanks!!!!

---

### Post by flipper T on 2011-04-07
Go to your "Places" menu, and open up "Computer"
Go into your "file system" , find the "Home" folder, 
and right click it,
then choose "Open with other application". 

When the list of applications comes up, 
Scroll down to "Open Folder", Select it, 
and at the bottom of the window, you'll see a check box, that says "remember this application for file folders".
(make sure it's checked)

Then simply click the "open" button at the bottom right,
and now whenever you open a folder..
it should open correctly.

---

### Post by WorMzy on 2011-04-07
Alternatively, edit the ~/.local/share/applications/mimeapps.list file, and remove the inode/directory line.

---

### Post by jorgeaz on 2011-04-07
Thank you very much !!!!

---

