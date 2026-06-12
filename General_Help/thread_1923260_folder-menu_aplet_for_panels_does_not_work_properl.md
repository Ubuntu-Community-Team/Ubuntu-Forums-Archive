---
title: "folder-menu aplet for panels does not work properly"
date: 2012-02-10
forum: General Help
---

### Post by WinfriedG on 2012-02-10
I want to insert in my panels a shortcut to certain folders like my e-book folder, which is on my SD card. I thought that the folder menu aplet  will do it; however, the following happens

I select the folder in the preference setup for the folder menu aplet and it shows the path in the first line of the preference edit screen.  I close it.
When I click on the symbol on the panel, it does not show the folder.
Then I open the preference edit screen again for the folder menu aplet and the first line, which should contain the selected path, is empty. And the last line, which should show the path to the icon, contains the path to the folder I want to open

-I wanted to insert here an image but what is the url of an image I have on my netbook- where to upload to?-

:confused:

---

### Post by SteveDee on 2012-02-11
> **WinfriedG said:**
> ...Then I open the preference edit screen again for the folder menu aplet and the first line, which should contain the selected path, is empty...

This "Directory Menu" panel applet is new to Lubuntu 11.10 and I just started playing with it a couple of days ago (see attached my experimental media centre panel).

Unfortunately there seem to be some bugs with it. I've found I can make it work for local directories by typing or copy/paste the paths required in the text boxes rather than using the Browse button feature. Once set you cannot go back to check or edit because (as you point out) the Directory path moves to the Icon text box.

I haven't tested this function with removable drives, so I suggest you try and get it to work with a local directory first.

> 
-I wanted to insert here an image but what is the url

When writing a post, move a bit further down the screen to find the "Manage Attachments" button. When you click on this a dialog opens.
Under "Upload file from your computer" click the first Browse button and find the file on your computer.
With the path & file name in the Browse text box, click one of the Upload buttons.
As long as your file is an acceptable type and not too large it should upload...Close the dialog and your done!

Also note that you can take screen shots on Lubuntu using the "Prnt Scrn" button. Captures are saved in your /home/{username}/ folder.

---

### Post by WinfriedG on 2012-02-12
Thank you @stevedee for the advice. So, I will wait with the folder shortcut until somebody solves the bug. 

Well, I will try with the upload here;( Hurra it worked). So the result of inserting paths in this window close the window open it again for a check is
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=212587&stc=1&d=1329083300[/IMG]

Sorry its in German: Well the folder (=Ordner) should contain the path, which is shown in "Symbol";and the icon (=Symbol) path should point to an /usr.... path but disappeared. 
The paths are obviously misplaced.  
I hope that is reparable quite easily.;)

---

### Post by SteveDee on 2012-02-13
> **WinfriedG said:**
> ...I will wait with the folder shortcut until somebody solves the bug...

...or (if you are very keen) you could also open the panel text files here: /home/WinfriedG/.config/lxpanel/Lubuntu/panels   and edit them manually...

---

