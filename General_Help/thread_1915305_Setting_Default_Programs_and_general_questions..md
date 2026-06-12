---
title: "Setting Default Programs and general questions."
date: 2012-01-25
forum: General Help
---

### Post by MarkD60 on 2012-01-25
I have Ubuntu 10.10 Netbook.
I recently upgraded to  version 11.04, but it didn't seem to work too well, so I formatted my drive and reinstalled 10.10 Netbook.
Now it seems 'different'. Slow and sluggish. When I close a program, I get a black screen momentarily before everything reappears..

The reason I am posting this, is for info on setting default programs. For photos, I like the program Fotoxx. I can't seem to set it as the default program for opening JPGs. I can right click an image from 'File Manager' ('Files and Folders' seems useless) and select "Open With Other Application', but Fotoxx is not  in the list of programs that appears. How can I select Fotoxx to open my JPGs?

Another problem, which may be related, I uninstalled 'Evolution' email, and installed Thunderbird. Evolution still appears in 'Applications' but is not on my machine. (I can click the icon and nothing happens) How do I get rid of the icon? Also, in the upper right hand corner of my screen, (next to the clock) is another Evolution Icon, with a drop down menu for email, create message and chat. The email icons don't to anything when clicked. I sure would like to get that icon  to open my Mozilla Thunderbird... Evolution does NOT appear in my 'Software Center'  'Installed Software' since I uninstalled it.

Any assistance would be greatly appreciated.
Thanks

---

### Post by MarkD60 on 2012-02-24
I guess this forum is dead. Where's the real forum?

---

### Post by yetiman64 on 2012-02-24
Not sure about the slow opening after reinstall, I will focus on the jpg association with your application (Fotoxx).

First open the 2 locations /home/<user>/.local/share/applications and /usr/share/applications in nautilus.

Copy the laucher from /usr/share/applications for fotoxx to ~/.local/share/applications. Note that the ~ symbol is just a system variable to replace /home/<user>.

Now right click on a .jpg image > Properties and note the mimetype is (if it differs use the mimetype shown in Properties), > image/jpegOpen the file ~/.local/share/applications/mimeapps.list in a text editor, terminal command to do so is ```
gedit ~/.local/share/applications/mimeapps.list
``` Add the line, 
> image/jpeg=fotoxx.desktop to either the [Default Applications] list if you want it as the default **OR** to the [Added Associations] if you want it available to open the program but **not** set as the default handler.

You may have to refresh any open nautilus windows to see the changes in the right click menu.

Please note these changes only affect your user profile, other users on your system will need to do the same to have fotoxx on their right click menus (either to make it available or to set as default handler).

Hope this at least helps with fotoxx. Cheers, yetiman64.

---

