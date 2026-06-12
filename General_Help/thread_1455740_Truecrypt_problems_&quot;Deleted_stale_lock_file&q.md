---
title: "Truecrypt problems: &quot;Deleted stale lock file&quot;; &quot;truecrypt is already running&quot;"
date: 2010-04-16
forum: General Help
---

### Post by jadu on 2010-04-16
hi, I just installed Truecrypt in Ubuntu. I have two problems:

1) After I mount my true crypt volume, I close the truecrypt dialogue box until I want to dismount it. When I try to open truecrypt again to dismount, I get a message "truecrypt is already running". So I can't open Truecrypt. I know I could probably open it with terminal or something, but I would like a solution so it would open in the normal way, since people who don't know computers or Ubuntu have to use this computer.

I found this solution online: 
> If a messagebox TrueCrypt is already running appears when starting TrueCrypt, check for a hidden file in the home directory of the concerned user called .TrueCrypt-lock-username. Substitute username with the individual username. Delete the file and start TrueCrypt again. 

But I couldn't find the file. Also I want to check and ask if it's safe to do that, it makes me nervous to delete a file like that.


2) When I first start Truecrypt, I get a message "Deleted stale lock file '/home..."  Why is this?
This was the only solution I found:

> [http://forum.ubuntuusers.de/topic/truecrypt-programm-vor-abmeldung-schliessen:](http://forum.ubuntuusers.de/topic/truecrypt-programm-vor-abmeldung-schliessen:)
edit the file /etc/gdm/PostSession/Default and add the line
kill `ps -ef | grep truecrypt | tr -s ' ' | cut -d ' ' -f 2`
just before the line with "exit 0" 

it's also here:
[http://wiki.archlinux.org/index.php/TrueCrypt#Encrypting_a_file_as_a_virtual_volume]("http://wiki.archlinux.org/index.php/TrueCrypt#Encrypting_a_file_as_a_virtual_volume")

unfortunately, I don't know how to edit a file. I guessed, I tried logging in as root in the terminal, and then I typed
edit /etc/gdm/PostSession/Default

But that gave me the following message:
> Warning: unknown mime-type for "/etc/gdm/PostSession/Default" -- using "application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"


Any ideas?
thanks a lot!

---

### Post by davidpbrown on 2010-04-16
To check for a hidden file in the home directory, in the Nautilus file manager select [View][Show Hidden Files]. That'll show files starting with a fullstop, eg .xyz, and in the home directory there will be lots of them. Those hidden files are roughly cookie files and folders holding the user settings.


Editing the PostSession file makes some sense but I don't know why it's not being setup appropriately that it closes down in a good way when user shuts the computer down.


This is a guess that might prevent you needing that: In Truecrypt [Settings][Preferences][Background Task] maybe background task is ticked [Enabled] and then running but not obvious as an icon in the notification area and so as you try running another instance of Truecrypt, it doesn't like it?

Maybe untick [Enabled] if it is ticked and see if that helps. Mine is unticked and I haven't a problem with it shutting down. That said I don't know how it unmounts at shutdown, it just works and I don't see errors. I guess each new session it might delete the stale lock file, if it's not closing in an ideal way.


I don't know where you're seeing the message that it's obvious enough to be a problem for other users. Always better to have it tidy though. I'm assuming you're using the graphical interface and not doing it the hard way though terminal.


To edit a system file the like of those in /etc you need to be logged in as superuser/administrator or use sudo command. Each time you do that a hidden backup is created as ~oldfilename in the same location.

'edit' as a command isn't an editor, it's mailcap to determine the filetype and the program that might open it. There are a lot of text terminal editors but not as easy as the graphic ones.


So, if it isn't the background task running where it's not needed then maybe do try the PostSession shutdown command with editing as
```
sudo gedit /etc/gdm/PostSession/Default
```

Also you can do 
```
sudo nautilus
```
navigate to the file you want, right click and open with gedit or another editor. However, be very careful navigating as superuser! You might do something you regret with all that power to hand.


Final point so you're aware, if you do want to login as superuser, then use "su -" to login as another user use "su username".

---

### Post by jadu on 2010-04-16
thanks so much. I tried unticking the background task. It seems to work for both problems-- I don't get the "deleted stale lock key" when I start it, and I can close the dialogue box and open it again.
However, I have a concern-- when I unticked the "background task" box, it gave me the following message--

> WARNING: If the TrueCrypt Background Task is disabled, the following functions, depending on the platform, will be disabled whenever you exit TrueCrypt:

1) Auto-dismount (e.g., upon log off, time-out, etc.)
2) Notifications (e.g., when damage to hidden volume is prevented)
3) Tray icon

However, I just tried turning the computer off with the disk still mounted, and when I turned it back on it was unmounted. But I'm still worried about what it says about auto-dismount being disabled. Do you know if that's a problem?
thanks

---

### Post by cjhabs on 2010-04-16
I have Truecrypt running with Background task turned on.
When I mount a drive and exit Truecrypt it goes into the tray at the top right of the screen.
When ready to unmount, I select the tray icon and unmount. When no drives are mounted and you exit Truecrypt, the program exits and does not sit in the tray.

I have seen the occasional stale lock message - which it deals with itself - maybe if I leave a volume mounted and reboot. I have never had a problem as a result of that.

---

### Post by jadu on 2010-04-16
Hmm, what is the tray at the top right of the sreen? When I turn on background task, it doesn't appear for me. I tried putting truecrypt on the top bar, but clicking on there still doesn't let me reopen truecrypt. Any idea?

---

### Post by 2hot6ft2 on 2010-04-16
> **cjhabs said:**
> I have Truecrypt running with Background task turned on.
When I mount a drive and exit Truecrypt it goes into the tray at the top right of the screen.
When ready to unmount, I select the tray icon and unmount. When no drives are mounted and you exit Truecrypt, the program exits and does not sit in the tray.

I have seen the occasional stale lock message - which it deals with itself - maybe if I leave a volume mounted and reboot. I have never had a problem as a result of that.
Same here. It runs in the notification area. You should be using Exit to close it after mounting the volume(s) and using the notification area icon to open it if you want to unmount volumes since it's running in the background already there's no reason to start it again as if it weren't running.
The Deleted stale lock file popup is a little annoying but I'll live with it.

Notification area icon pic.

---

### Post by jadu on 2010-04-16
I added the notification icon to the top bar and now I can reopen it from there. 
it still says "deleted stale lock file" every time, but that's ok.

thanks!

---

### Post by davidpbrown on 2010-04-16
> **jadu said:**
> WARNING: If the TrueCrypt Background Task is disabled, the following functions, depending on the platform, will be disabled whenever you exit TrueCrypt:

1) Auto-dismount (e.g., upon log off, time-out, etc.)
2) Notifications (e.g., when damage to hidden volume is prevented)
3) Tray icon

I came at it a few days ago from the opposite direction, it was unticked and I wondered if it mattered. I've been using it a long while in the same way.

I suspect the talk of auto-dismount is just that the disk unmounts ok but it leaves the .lock status file where it would like to be tidy and delete it. Then it just cleans up next boot, so I can't see a big problem. Adding to the PostSession/Default file is a manual way to ensure everything is closed end of session, which I expect must be just releasing the lock file.

---

### Post by cjhabs on 2010-04-17
> **jadu said:**
> I added the notification icon to the top bar and now I can reopen it from there. 
it still says "deleted stale lock file" every time, but that's ok.

thanks!

Unmounting the disk in Truecrypt when you are done eliminates the stale lock messages.

---

### Post by t0p on 2010-04-17
> **cjhabs said:**
> Unmounting the disk in Truecrypt when you are done eliminates the stale lock messages.

Yes indeed.  And I would recommend you unmount every time you decide to quit Truecrypt.  It's wise from a security standpoint too I believe.

But there isn't anything to worry about re the stale lock messages.  These are not error messages; Truecrypt is just telling you about a housekeeping functiion it's doing, just in case you see it happening and worry that someone/thing has compromised your files.

Have you read the Truecrypt docs?  I suggest you do so - you can read them [here]("http://www.truecrypt.org/docs/").  Let's face it: you're using Truecrypt because you have privacy issues.  So it stands to reason you should use the app properly, otherwise your enemies may be able to exploit your errors to open your sensitive data.  Truecrypt is a very useful, very hard security tool.  But it's only as strong as the weakest link: the user (ie you).

---

### Post by davidpbrown on 2010-04-18
If it's to be trusted, then it's not unreasonable to expect the default behaviour is safe. So, unmount by system shutdown shouldn't be an issue.

---

### Post by jadu on 2010-04-19
thanks again, for the last comments--

---

### Post by Vand3lay on 2010-05-03
I recently had both these problems and just created a bash file to fix them both and have truecrypt run on startup. I also keep the background task enabled.

```
rm ~/.TrueCrypt-lock-xxxxx
truecrypt
```

Where xxxxx is your username and added the .sh file to my startup applications.

---

