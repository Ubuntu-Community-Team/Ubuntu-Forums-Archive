---
title: "Internet Icon missing from Gnome panel"
date: 2009-11-30
forum: General Help
---

### Post by Pesky_Programmer on 2009-11-30
[COLOR=black][FONT=Verdana]While rearranging my icons in the top panel of Ubuntu I may have accidentally deleted the icon that allows me to choose/connect to my Internet connection. I tried adding just about every item from the add icon list to panel and couldn't seam to find the one for Internet.[/FONT][/COLOR][COLOR=black][FONT=Verdana]I included a picture of the menu that I am attempting to get back to my panel for clarification. I would like to know how to get the icon back on my list. The sound icon is missing as well.[/FONT][/COLOR]
 

[COLOR=black][FONT=Verdana]Also ever since I lost the Internet icon I get an error message every time I reboot. Im not sure if this is related to the missing icon or if it has to do with the fact I tired adding and removeing all, if not most, of the icons avalible to be added to the panel.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Included below is the error message; for the moment I have just been clicking the x on the window as im not sure what it is asking me to delete or if Ishould delete it.[/FONT][/COLOR]


[COLOR=black][FONT=Verdana]Thanks for reading and for help in advance.[/FONT][/COLOR]

---

### Post by mkvnmtr on 2009-11-30
I have no experience with   but I would delete it like it says. Then I would go to the package manager and find it. If it is installed I would completely uninstall and reinstall. Then look for the icon to put back on your panel. I am sure you know a right click on the panel will bring up add to panel.

---

### Post by raktarok on 2009-11-30
The icon is provided by the program nm-applet, and is the part  of notification area. What you should do is check if the nm-applet is running. See the system monitor. 
OR from a terminal, try to start the nm-applet. Do this:
nm-applet &
If this fails, then try **killall nm-applet**, and again try to start nm-applet. If you still don't see the icon, then post the error output that you see. 
You can also try removing the package and reinstalling it, as suggested above.
Hope this helped!

---

### Post by Pesky_Programmer on 2009-11-30
mkvnmtr: I have tried going to delete, and once again tried all of the icons available to be added to my panel. While doing this I encountered the same error while trying to add the highlighted item. Refer to picture. I also ran a search for that item, the one Ubuntu wants me to delete, as a package and found nothing. 
 
Raktarok: I will now try your advise just have to reboot back to Ubuntu, I'm using Windows to communicate  on forms at the moment due to my missing icon.

---

### Post by Pesky_Programmer on 2009-11-30
oops forgot to include the picture

---

### Post by Pesky_Programmer on 2009-11-30
I was able to get the Connections Icon back by typing  nm-applet into the terminal as you said. nm-applet was not running until I started it myself.

 However nm-applet will only stay running for as long as I have the terminal Window open. I also loose my connection to the Internet once once nm-applet is no longer running.

So how do I make nm-applet run all the time like it used to?

Thanks for the help so far.:D

---

### Post by raktarok on 2009-11-30
You can add it to your startup applications list. Go to System > Preferences > Startup Applications
Actually, there should be an entry there named Network Manager. Its the same thing as nm-applet, so first see if the entry is present and there is a tick beside it.
If there is no such entry, then create one yourself. Click on Add,you can type any name, but in the command place this: **nm-applet --sm-disable**
Now in your next relogin, you should have the icon back.
This should solve this completely, Post again if it does not.
Good Luck!

---

### Post by Pesky_Programmer on 2009-11-30
Unfortunately it did not work.

As you said there should already be an entry for the nm-applet and there was. To my surprise it was already checked. I scrolled down the list some and found an entry for my sound icon that was also missing and also checked.

 So I unchecked both of them and rebooted. I then went back to the list and rechecked them, and again rebooted. The icons were still missing after that. 

I then tried deleting the original entry for my network manager, first copying all of the contents for its config to notepad, and then recreated it just as you had told me to. Again I reboot and the icons are still missing.

So back to the terminal to get my Internet working again and I noticed as I connected I got an error message in the terminal. Not sure if its related to the issue at hand or its just normal computer stuff that goes on in the background but figured I should post it just in case.

> 
** (nm-applet:2187): DEBUG: foo_client_state_changed_cb
** (nm-applet:2187): DEBUG: foo_client_state_changed_cb


Thanks for your patience.

---

### Post by raktarok on 2009-11-30
Hmm...the problem seems to be with the gnome-applet. Can you add applets from the "add to panel" dialog? Select the notification area from it and try adding. This is where the icon should appear. Does it give the same error as above? Also, during startup,when you are asked to delete, what happens if you delete?
 The problem seems to arise due to the terminal server client applet, so try removing its package and see if that helps. Do this:
```
sudo apt-get purge tsclient
```
Now try adding the notificaion area applet. Try logging of and relogging too. 
In the end, if the problem is solved, you may install the tsclient package again:
```
sudo apt-get install tsclient
```

---

### Post by Pesky_Programmer on 2009-11-30
I have come to the conclusion my computer hates me.... :icon_frown:

There was already a notification area present. I removed it and added a new one. I then rebooted and still nothing new. I even added a second new one for good measure.

I then used the your command for removing the tsclient and rebooted..... nothing. 

I then, using the second command you gave me, reinstalled it and rebooted... still nothing. 

so I went back to terminal and reconnected to post my results. 


The window asking me to delete has not returned since I went to delete.


Maybe I will just reformat my drive and start over. :rolleyes:

---

### Post by raktarok on 2009-11-30
This is weird...event though nm-applet is in the startup list, it's not appearing in the notification area.

Okay, try to see if there is an error during startup. Open the file /home/your_username/.xsession-errors (you will have to do a Ctrl+h to see that file in your home folder, its hidden) and navigate to the end to see if there is any error related to nm-applet or the volume icon.Or you can attach that file here too, if you want to. I will have a look at it.

In the mean time, maybe you can try this to solve the problem temporarily..
Open gedit and paste these lines:
```
#!/bin/sh
killall nm-applet
nm-applet --sm-disable &
touch ~/Desktop/script-executed
```

Save the file with any name you like, and then make it executable by right clicking it, going to the Properties and then the Permissions tab, and selecting "execute this file as a program." Then open the 'startup applications dialog' and add the path to this script as the command. 
Relogin and see if this solves the problem. You should see a file named script-executed in the desktop, if the file was read during startup. I added that just to test if the file gets read or not.

---

### Post by Pesky_Programmer on 2009-11-30
Thanks for adding that ctrl h in couldn't find the file at first and skipped that step. But later found it after you edited. I'm not really sure what the file says :-? I understand some of it....I think. Anyway here it is for your enjoyment. I had to put it in a text file because the attachment manager didn't like it.

Also I did what you said but can't seam to get any files to be outputted to my desktop. I will retry it in the meantime while you read the other file.

Thanks

---

### Post by raktarok on 2009-11-30
Sorry,but at the moment, I have no idea why its not working. I will try to look at the problem and see if I can find a solution.

For the time being, you should be able to get the icon by using the script I gave you. Try making a launcher out of it (Click add to panel and then Custom Application Launcher. Get the empty 'command' field by hitting Browse, and then navigating to the folder with the script) 

If the script is not running, check the permissions first - it should be executable. Just run this command from the terminal to ensure that the permissions for the script are all right: (You can also change the permissions from the properties window of the script, as I told you earlier):
```
sudo chmod 755 /home/yourusername/script_name
```
Here, I have assumed that the script is in your home folder. Change the path to the appropriate one and then the script should run.

To stop the script from making the file 'script-executed' in your desktop, just remove the line starting with 'touch'.

Thus, for a temporary solution,  add the script to the startup applications list after changing the permission and see if it works. Otherwise,create a launcher for it. 

I don't have any good suggestion to actually solve the problem, sorry! maybe others can help you....

---

### Post by Pesky_Programmer on 2009-11-30
Thanks for the help you have shown a lot more dedication then most paid computer techs and for that you have my gratitude. I will try your last bit of advise but it might just be that me and Linux just weren't meant to be. 
I never get the normal problems. :-(

---

