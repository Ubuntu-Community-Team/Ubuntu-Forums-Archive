---
title: "Outlook Express on linux"
date: 2005-03-05
forum: General Help
---

### Post by Mark7805 on 2005-03-05
Hey I need to back up my parents outlook accounts meaning like all there Address books,There accual accounts and there recieved messages.And the only way I can think of that I can get all that stuff is using outlook express on windows xp which is not working at this time.Does any1 know how I can get outlook to work on linix?

---

### Post by kassetra on 2005-03-05
[QUOTE=Mark7805]Hey I need to back up my parents outlook accounts meaning like all there Address books,There accual accounts and there recieved messages.And the only way I can think of that I can get all that stuff is using outlook express on windows xp which is not working at this time.Does any1 know how I can get outlook to work on linix?[/QUOTE]

You could use outlook on linux, but I have a better method for you backup that stuff.  If your parents use Outlook Express:

1. On the windows box look for a .DBX or .MBX file in program files / outlook or something similar (do a search for *.mbx or *.dbx files). That is their email messages. Copy that file to linux (or to a cd or disk).
2. Data about your mail and news accounts are stored in the registry key HKEY_CURRENT_USER\Software\Microsoft\Internet Account Manager. To save this data, start RegEdit and select that key in the left-hand pane. Then from the menu select Registry | Export Registry File. Save the file to a name like "outlookexp.reg" - and then copy that file to linux. 
3. Their address book is stored in a .WAB file in program files / outlook (do a search for *.wab files), copy that file to linux.

If they use Outlook, the steps are similar, but the files are slightly different:
1. .PST, .DBX should be the email files.
2. same.
3. .PAB is the address book.

---

### Post by Mark7805 on 2005-03-05
I can't go on my windows xp though.Theres something horribly wrong with it so I need to reformat my computer.so I need any possible way to get everything back.meaning like I said emails,email accounts and address books

---

### Post by kassetra on 2005-03-05
[QUOTE=Mark7805]I can't go on my windows xp though.Theres something horribly wrong with it so I need to reformat my computer.so I need any possible way to get everything back.meaning like I said emails,email accounts and address books[/QUOTE]

You can mount the windows XP side in Linux and pull the files off of it that way.  Do you know how to mount a partition/drive?

---

### Post by Mark7805 on 2005-03-05
Can't you just tell me the directory of my outlook stuff I need?
I don't wanna do crazy hard stuff
LoLz

---

### Post by kassetra on 2005-03-05
[QUOTE=Mark7805]Can't you just tell me the directory of my outlook stuff I need?
I don't wanna do crazy hard stuff
LoLz[/QUOTE]

If you can't boot into windows, how you do expect to get to the directory?  You want to use Linux to get to the directory, correct?

The windows directories have to be viewable in Linux in order for me to give you a directory that you can get to.  The first step is to make sure that linux sees the windows directories, in other words, to make sure that the windows directories are "mounted" under linux.

It's not crazy hard stuff.

---

### Post by KiwiNZ on 2005-03-05
Mark 

If your XP box is that hosed you can try two things

1. Zap down to a Magazine shop , grab a Linux Mag with a Live Distro on thecover disk like Knoppix and boot from that find the files that kassetra mentions and save to USB key or floppy .
2. If you have another PC take out the hdd and slave mount the hosed disk and recover the files

---

### Post by Mark7805 on 2005-03-05
I'm using the live cd cause I was having problems with getting the real installation of ubuntu to work.and I have 2 cd drives but it doesn't detect my cd-rom only my cd-rw drive so that mean I can't take out the live cd if I wanted to burn all the backup stuff to a cd

---

### Post by kassetra on 2005-03-05
[QUOTE=Mark7805]I'm using the live cd cause I was having problems with getting the real installation of ubuntu to work.and I have 2 cd drives but it doesn't detect my cd-rom only my cd-rw drive so that mean I can't take out the live cd if I wanted to burn all the backup stuff to a cd[/QUOTE]

Ok, with the live cd, it's possible that your windows directories are already mounted.  Can you go to Computer->Disks?  What do you see?

---

### Post by Mark7805 on 2005-03-05
well now I'm using the install ubuntu.I have have the hard drive with the outlook express accounts on.How do I backup all of it?Like I need everything.address books,messages,the acual email accounts.How do I get access to all these files on linux?Like I said my windows is fried so I can't use anything that has to do with windows

---

### Post by kassetra on 2005-03-05
[QUOTE=Mark7805]well now I'm using the install ubuntu.I have have the hard drive with the outlook express accounts on.How do I backup all of it?Like I need everything.address books,messages,the acual email accounts.How do I get access to all these files on linux?Like I said my windows is fried so I can't use anything that has to do with windows[/QUOTE]

Ok, similar to how you look at files through "My Computer" you're going to browse around to find your directories in order to save the files with linux.

1. Go to Computer->Disks
2. Click on a hard-drive looking icon (possibly named hda or something like that)
3. Now tell me what you see.

---

### Post by Mark7805 on 2005-03-05
I see ATI,Documents and Settings,My Downloads,Nvidia,Program Files,Recycler,System Volume info. and windows

---

### Post by kassetra on 2005-03-05
[QUOTE=Mark7805]I see ATI,Documents and Settings,My Downloads,Nvidia,Program Files,Recycler,System Volume info. and windows[/QUOTE]

Ok!  go into "Program Files"
If you see an Outlook or Outlook Express directory/folder in there, open it up.  If not, go into "Documents and Settings"
You're first looking for a file that ends in .DBX, .PST, or .MBX

When you find that file, right click to open a little menu, then left click on copy. Right click on your desktop and left click on paste.

Let me know if you can't do this.

---

### Post by Mark7805 on 2005-03-05
All I see in the Outlook folder is dlls and exe's

---

### Post by kassetra on 2005-03-05
[QUOTE=Mark7805]All I see in the Outlook folder is dlls and exe's[/QUOTE]

Ok, instead of hunting and pecking around, here's what we're going to do, it's quick and painless:
1. Go to Computer->Search for Files...
2. Type in *.pst in the "Name contains:" box.
3. Change the "Look in folder:" by clicking the Browse... button.  
4. When the "Browse" window pops up, you *should* see the hda or whatever the name was that you saw in the Computer->Disks window that led to you to your windows directories in the left hand side.  Double click it.
5. Now click Open.
6. Now click Find.

If you do not see results, change "Name contains:" to *.mbx and click Find.  If still nothing, change "Name contains:" to *.dbx and click Find.

---

### Post by Mark7805 on 2005-03-05
only found 1 pst out of 3 I found no mbx and found a whole bunch of dbx

---

### Post by kassetra on 2005-03-05
[QUOTE=Mark7805]only found 1 pst out of 3 I found no mbx and found a whole bunch of dbx[/QUOTE]

Ok.  The pst is your mailbox.   Go back to the pst find (drop down the box in the search and choose *.pst and click find again)
Right click on the pst line in the "Search results:" area, and then left click on "Open folder" ...
This will pop up the folder that contains the pst file.  Find the pst file, right click on it and choose "copy" ... then on a clear spot on your desktop, right click and choose "paste"  ... this will copy your pst file to your desktop ... so then you've backed up your emails.  

When that's done, do a search for *.wab or *.pab  (that's your address book)  and do the same open folder & copy/paste.

How many dbx files did it find?  20?  30?  (you can guess, it doesn't need to be an accurate number)

---

### Post by Mark7805 on 2005-03-05
I fount 36 what are dbx?

---

### Post by kassetra on 2005-03-05
[QUOTE=Mark7805]I fount 36 what are dbx?[/QUOTE]

dbx is one of the formats of mailboxes that outlook express uses... you might want to save those, just in case.

Now do a search for *.reg and copy & paste that as well (that will have your email accounts as well as lots of other stuff, but since you can't use windows right now, this will have to do.)

---

### Post by uc50_ic4more on 2005-06-03
[QUOTE=kassetra]dbx is one of the formats of mailboxes that outlook express uses... you might want to save those, just in case.

Now do a search for *.reg and copy & paste that as well (that will have your email accounts as well as lots of other stuff, but since you can't use windows right now, this will have to do.)[/QUOTE]

Can anyone confirm that Evolution will be able to *import* .dbx and .wab files? From the Evolution import dialog, only OE v4 (.mbx) are listed as "importable"... I have about 6 people who I have convinced to switch; but their lives revolve around OE v6, and I have been apprehensive, although Evolution was able to import the old Thunderbird data (*not* listed in the Evolution import dialog...) I had without incident...

I assume also that people who have several different sub-sub-sub folders in OE are going to have to import each individually.

Kassetra - what good are the registry values going to do us back in Ubuntu land?

Thanks!

---

