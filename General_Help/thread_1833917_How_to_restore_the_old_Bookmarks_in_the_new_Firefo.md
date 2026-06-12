---
title: "How to restore the old Bookmarks in the new Firefox?"
date: 2011-08-26
forum: General Help
---

### Post by BSG Fan on 2011-08-26
Okay, I saved in a CD the old bookmarks because I installed the new Ubuntu :)
my question is,
How I restore that file (now in my documents) ?
I can not see the "Restore Bookmarks from File"

Thanks you in advance

;)

---

### Post by papibe on 2011-08-26
Bookmarks -> Organize Bookmarks -> Import and Backup.

Hope it helps,
Regards.

---

### Post by BSG Fan on 2011-08-26
> **papibe said:**
> Bookmarks -> Organize Bookmarks -> Import and Backup.

Hope it helps,
Regards.

Hello Papibe
Yes, you are very right. But that was only seen in Ubuntu 8 to Ubuntu 10.
In Ubuntu 11 I can not see that. Where it is?

:(

---

### Post by ron999 on 2011-08-26
Bookmarks -> **Show All Bookmarks** -> Import and Backup

---

### Post by e79 on 2011-08-26
> **BSG Fan said:**
> Hello Papibe
Yes, you are very right. But that was only seen in Ubuntu 8 to Ubuntu 10.
In Ubuntu 11 I can not see that. Where it is?

:(

If you are using the latest Ubuntu edition (Natty 11.04) with Unity, then, when having your focus on a Firefox window, drag your mouse to the top panel and you will see the usual menu, with 'Bookmarks' included.

Hope this helps

---

### Post by BSG Fan on 2011-08-26
> **ron999 said:**
> Bookmarks -> **Show All Bookmarks** -> Import and Backup

I did it but does not work.
The error massage says:
"Unable to process the backup file".

So, what I do?

---

### Post by BSG Fan on 2011-08-26
> **e79 said:**
> If you are using the latest Ubuntu edition (Natty 11.04) with Unity, then, when having your focus on a Firefox window, drag your mouse to the top panel and you will see the usual menu, with 'Bookmarks' included.

Hope this helps

Jello e79: Thank you

I am trying to do that... but I don't see the usual Menu. Where exactly in the top panel I click with the mouse?

---

### Post by e79 on 2011-08-26
My suggestion was useless since (as seen on your screenshot) you are not using Unity but rather Gnome interface. Anyhow, you got exactly where you had to go, in the Bookmarks menu that is.

As for your bookmarks backup, is it a single file ending in .json ? If not, how did you made your backup ?

---

### Post by lovinglinux on 2011-08-26
> **BSG Fan said:**
> I did it but does not work.
The error massage says:
"Unable to process the backup file".

So, what I do?

There is a list of backups in the Restore submenu. They are created automatically. If you are trying to restore an exported html bookmark file, it won't work. You need to import those.

---

### Post by BSG Fan on 2011-08-26
> **e79 said:**
> My suggestion was useless since (as seen on your screenshot) you are not using Unity but rather Gnome interface. Anyhow, you got exactly where you had to go, in the Bookmarks menu that is.

As for your bookmarks backup, is it a single file ending in .json ? If not, how did you made your backup ?

Yes, the file is an .json (plain text document (text/plain))
I do not know what to do
This problem with the bookmarks only occurs in the Ubuntu 11
:confused:

---

### Post by BSG Fan on 2011-08-26
> **lovinglinux said:**
> There is a list of backups in the Restore submenu. They are created automatically. If you are trying to restore an exported html bookmark file, it won't work. You need to import those.

Hi, no, I am not trying to import any HTML file, but a .Json file.
I am confused...
The same error keeps happening
[I]The error massage says:
"Unable to process the backup file".[/I]

The bookmark file I have saved (before installing the new Ubuntu) always opened as a "restore file" before...
:confused:

---

### Post by e79 on 2011-08-26
One thing I'd suggest as this point if you have the time. Boot up with a LiveCD and try to import your backup and re-export your bookmarks again to see if it helps. Try with the distribution you used before reinstalling...I begin to suspect something wrong between Firefox's version or something...

If it still does not work, you could give a try to Firefox Sync (see attached screenshot).

---

### Post by BSG Fan on 2011-08-26
> **e79 said:**
> One thing I'd suggest as this point if you have the time. Boot up with a LiveCD and try to import your backup and re-export your bookmarks again to see if it helps. Try with the distribution you used before reinstalling...I begin to suspect something wrong between Firefox's version or something...

If it still does not work, you could give a try to Firefox Sync (see attached screenshot).

Okay, I see that a little 'complicated' for my limited understanding...
I will try the Firefox Sync

---

### Post by lovinglinux on 2011-08-27
> **BSG Fan said:**
> Okay, I see that a little 'complicated' for my limited understanding...
I will try the Firefox Sync

If you haven't enabled Firefox Sync before, then it won't work. 

If you still has access to the profile you want to import the bookmarks, then simply copy the places.sqlite file to the new profile. You can find the profiles under ~/.mozilla/firefox

---

### Post by BSG Fan on 2011-08-27
> **lovinglinux said:**
> If you haven't enabled Firefox Sync before, then it won't work. 

If you still has access to the profile you want to import the bookmarks, then simply copy the places.sqlite file to the new profile. You can find the profiles under ~/.mozilla/firefox

No, it does not work  :(

If I could open that backup file from other web browser and later transfer it to Firefox?

I tried with Chromium but I couldn't...
Guys, I am almost surrendering

:KS

---

### Post by lovinglinux on 2011-08-27
> **BSG Fan said:**
> No, it does not work  :(

If I could open that backup file from other web browser and later transfer it to Firefox?

I tried with Chromium but I couldn't...
Guys, I am almost surrendering

:KS

What exactly is your scenario? I suppose you did a backup of your bookmarks, wiped your HD, installed a new Ubuntu and the only copy you have is that json file. Is that correct?

---

### Post by BSG Fan on 2011-08-27
> **lovinglinux said:**
> What exactly is your scenario? I suppose you did a backup of your bookmarks, wiped your HD, installed a new Ubuntu and the only copy you have is that json file. Is that correct?

yes, that is it.

---

### Post by lovinglinux on 2011-08-27
> **BSG Fan said:**
> yes, that is it.

In this case, I suppose you are in trouble. Most likely that your json file is corrupt. To make sure, I have attached a json file that is working. Extract the tar file to get the json. Test it and let me know if it works or not.

If it works, then we need to figure out a way to fix your json file.

On a side note, I strongly recommend that, if possible, reinstall Ubuntu making sure you have separate partition for home. This way you can re-install Ubuntu any time you want, without losing your personal files.

---

### Post by BSG Fan on 2011-08-27
> **lovinglinux said:**
> In this case, I suppose you are in trouble. Most likely that your json file is corrupt. To make sure, I have attached a json file that is working. Extract the tar file to get the json. Test it and let me know if it works or not.

If it works, then we need to figure out a way to fix your json file.

On a side note, I strongly recommend that, if possible, reinstall Ubuntu making sure you have separate partition for home. This way you can re-install Ubuntu any time you want, without losing your personal files.

Okay, wait. I will use that file

Hey, LovingLinux:
Your file worked!
It opened right here: in my Ubuntu thread: Re: How to restore the old Bookmarks in the new Firefox?

So... my backup file is corrupted?  It is 3.9 MB (4090400 bytes) the encyclopedia-backup of over 2 years of bookmarks... I don't think it has something negative to do, no?

---

### Post by lovinglinux on 2011-08-27
> **BSG Fan said:**
> Okay, wait. I will use that file

Hey, LovingLinux:
Your file worked!
It opened right here: in my Ubuntu thread: Re: How to restore the old Bookmarks in the new Firefox?

So... my backup file is corrupted?  It is 3.9 MB (4090400 bytes) the encyclopedia-backup of over 2 years of bookmarks... I don't think it has something negative to do, no?

Try to download [Firefox 3.6 from Mozilla]("http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.6.20/"), extract it to your home, close all instances of Firefox and launch the *firefox* file inside the extracted folder using the following command (assuming you extracted to your home):

```
~/firefox/firefox -P
```

This will launch the profile manager using FF 3.6. Create a new profile and start it. Restore your backup. Close Firefox, open the profile folder under ~/.mozilla/firefox/<profilename>/ and copy the *places.sqlite* file to the default profile used by FF 6.

Start Firefox 6 and see if your bookmarks are there.

---

### Post by BSG Fan on 2011-08-27
> **lovinglinux said:**
> Try to download [Firefox 3.6 from Mozilla]("http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.6.20/"), extract it to your home, close all instances of Firefox and launch the *firefox* file inside the extracted folder using the following command (assuming you extracted to your home):

```
~/firefox/firefox -P
```

This will launch the profile manager using FF 3.6. Create a new profile and start it. Restore your backup. Close Firefox, open the profile folder under ~/.mozilla/firefox/<profilename>/ and copy the *places.sqlite* file to the default profile used by FF 6.

Start Firefox 6 and see if your bookmarks are there.

===
Okay, 
I will download "linux-i686 04-Aug-2011 17:36" -choosing "en-US 04-Aug-2011 21:15", choosing "firefox-3.6.20.tar.bz2 03-Aug-2011 22:53 10M"

I will let you know what happens...

---

### Post by BSG Fan on 2011-08-27
LovingLinux:

Okay, I am reviewing:
1- Before downloading the file I went to my home (my user name) and created a folder called "Firefox 3.6" (later changed to Firefox)

2- I downloaded the file in that folder.

3- I extracted the file inside that folder. (see attachment)

4- I found that "Firefox" file, and I clicked, with the hope to see a terminal and paste ~/firefox/firefox -P , and click enter, and see codes running, etc.

A fast terminal opened but it disapeared instantly.
My firefox opened (with all my home pages) but I don't know what to do
So, I did not see the profile manager launched to use the FF 3.6.

Till there, I am.

---

### Post by BSG Fan on 2011-08-27
and the last 2 screens

---

### Post by BSG Fan on 2011-08-27
LovingLinux!

It worked!!!!!!!!!!!!!!!!!!!!!!!

You are the master of all the Ubuntu kids in this world!

Thank you for having so many patience with me.

Note:
and thanks to all the other users that helped me in this ex-nightmare.

---

### Post by lovinglinux on 2011-08-27
> **BSG Fan said:**
> LovingLinux!

It worked!!!!!!!!!!!!!!!!!!!!!!!

You are the master of all the Ubuntu kids in this world!

Thank you for having so many patience with me.

Note:
and thanks to all the other users that helped me in this ex-nightmare.

You are welcome.

:popcorn:

---

### Post by lalawawa on 2012-03-10
This thread was really helpful.  It never would have occurred to me to wave my mouse to the top of the screen to find the "File Edit ..." buttons for
firefox.:D

---

