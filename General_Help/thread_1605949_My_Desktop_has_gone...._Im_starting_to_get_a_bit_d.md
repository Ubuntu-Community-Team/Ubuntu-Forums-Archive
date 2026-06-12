---
title: "My Desktop has gone.... Im starting to get a bit desperate, please"
date: 2010-10-25
forum: General Help
---

### Post by PauloFighters on 2010-10-25
[FONT="Verdana"]Hey guys, how are you?

I tried to find a solution on the forum after my Desktop folders, files, everything vanished. What I've got now is "Standard Icons", Home, Pics, Videos, etc.

I tried to locate files via SEARCH on FILE SYSTEM and I couldn't find any. I tried to reset Nautilus and nothing happens. I have a different profile in this Laptop and that profile is UNCHANGED, but mine is screwed.

I'm getting a bit desperate because I have an exam tomorrow and I NEED to access those files.
I Use Ubuntu 9.10, Desktop edition.

Can anyone please HELP ME?

Paulo [/FONT]


IF I TYPE NAUTILUS THE FOLLOWING MESSAGE COMES ON TERMINAL

"paulo@paulo-laptop:~$ 
(nautilus:4730): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

** (nautilus:4730): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:4730): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:4730): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing."

---

### Post by Hakunka-Matata on 2010-10-25
try the ```
locate
``` command from within the Terminal (Applications > Accessories > Terminal)

---

### Post by PauloFighters on 2010-10-25
Hi there, thank you for your help.

The code LOCATE itself tells me "locate: no pattern to search for specified"

So, I tried LOCATE DESKTOP and it gave me a massive list.

If I use "Locate Chemistry", "Locate RMIT" it just gives me what I could find on search anyway. Am I doing something wrong?

---

### Post by Hakunka-Matata on 2010-10-27
No, I don't think you're doing anything wrong.  I use locate when looking for files that might be anywhere on the drive.  Your information says you joined way back in September 2,006, so I suppose you know that file and folder names are case sensitive, right?  So where are your files?, even if they somehow got moved to trash, they should still be there in the trash folder if trash hasn't been emptied???

---

