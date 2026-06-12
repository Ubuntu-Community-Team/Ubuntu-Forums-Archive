---
title: "Thunderbird was reseted"
date: 2012-01-09
forum: General Help
---

### Post by Molech on 2012-01-09
Hi.
I'm a new user of Linux Ubuntu Oneiric AMD64.
I had a fully configured Thunderbird 8.0 with RSS and several e-mail accounts.
Then I noticed my personal contact (in catalog) was incomplete and want to add more data to it. Because the contact could not get updated (it was possible to add data but not to save it), I ran thunderbird from the console, as administrator (sudo thunderbird).
For my surprise, all my data were wiped out. Now I open Thunderbird (wheter be as normal user or root) and all my accounts were gone, like the first time init of thunderbird.
Can anybody help?

---

### Post by imachavel on 2012-01-09
well you'd have to find them. You set up thunderbird with RSS? I'm not sure what rss has to do with pop(incoming) and smtp(outgoing)

I thought rss was configured with html or http, what is your Thunderbird client synced with?? Sorry I can't help you but I don't want you to feel as though you are being ignored, read this please:

[http://www.ehow.com/how_8197142_files-email-stored-linux-ubuntu.html](http://www.ehow.com/how_8197142_files-email-stored-linux-ubuntu.html)

if that doesn't help you(didn't help me at all), then read this:

[http://lifehacker.com/5805828/how-to-sync-your-desktop-email-client-outlook-or-thunderbird-across-multiple-computers](http://lifehacker.com/5805828/how-to-sync-your-desktop-email-client-outlook-or-thunderbird-across-multiple-computers)

it's going to be in a directory, maybe in home, maybe not(if you permanently deleted your contacts somehow, then the only way to find those files is to recover 'unaddressed' files from the hard drive. Well with windows it works that way, maybe with linux they are gone completely. Also with windows that rarely works as windows can't recognize the file when you try to open it)

---

### Post by Molech on 2012-01-09
That is the strange part.
All my contacts are synced with Google and remains intact.
All my accounts (email and rss) are gone.
I found the .thunderbird with the files stored in it, but thunderbird apparently ignore it and when I add an account, it puts an "-1" in the front of the folder, like "imap.gmail-1".
Looks like I have to configure it all over again.

---

### Post by Molech on 2012-01-10
Hi.
Looks like those settings are in the "prefs.js" located inside the user profile folder. I think that since I ran thunderbird as administrator, the system treated me (admin) as new user and get rid of my prefs (prefs, e-mail and rss accounts).
Lucky me I just erased my deja backup data and had to config it all over again =D> (ironic).
I suggest Thunderbird developers to modify that so a new profile is created instead of overwritting the current.

---

### Post by Molech on 2012-01-10
And by the way, how can I edit my personal contact?
I want to add my personal info and photo.
Thunderbird catalog modifies it but not save it.

---

### Post by Krytarik on 2012-01-10
> **Molech said:**
> I suggest Thunderbird developers to modify that so a new profile is created instead of overwritting the current.
This all has happened because you've run a graphical app with "sudo"; if you need (or feel you need, like in this case) to run an app with admin rights, use "gksudo" instead:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

What can happen if you use "sudo" in those cases is that the ownerships of the files the respective process touches are changed to "root", thus leaving you unable to edit those files as the regular user after that. This would explain the issue you had in the first place and still have (see below), if you used "sudo" like that before. But I don't quite get why Thunderbird apparently created a new "prefs.js" instead of 'just' changing the ownership of it, possibly. Anyway.

> **Molech said:**
> And by the way, how can I edit my personal contact?
I want to add my personal info and photo.
Thunderbird catalog modifies it but not save it.
To fix your initial issue, make sure the ownerships of all files/dirs under ".thunderbird" are set to your regular user:
```
sudo chown USERNAME:USERNAME -R ~/.thunderbird
```Where USERNAME is the name of your regular user, obviously.

Regards.

---

### Post by Molech on 2012-01-11
Thanks a lot for the explanation.
I don't even know about the "gksudo" command.
Well, we can add Thunderbird to the list of "things that gone bad" when "sudo" is used to launch a graphical interface.
About the catalog, Ill try it (I'm in Windows ambient right now), then I'll mark the thread as solved (if it works).

---

