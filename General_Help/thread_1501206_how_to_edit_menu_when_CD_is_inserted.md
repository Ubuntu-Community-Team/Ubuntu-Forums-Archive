---
title: "how to edit menu when CD is inserted?"
date: 2010-06-04
forum: General Help
---

### Post by PGScooter on 2010-06-04
Hi, how can I remove options from the menu that automatically appears when a CD is inserted? I thought that these settings would be in the Preferred Applications but no luck.

Thanks

---

### Post by wilee-nilee on 2010-06-04
Could you be more vague about what your referring to. ;)

---

### Post by PGScooter on 2010-06-04
Hi wilee, thanks for the reply. I'll try to be more specific :)

When I insert an audio CD, a menu appears, notifying me that I inserted an audio CD and kindly asking me with which application I would like to open it. There is an option that says "custom command" or something of that sort. I have entered several custom commands, but I do not see how I can remove them. They stay on the menu and now it is cluttered.

Thanks

---

### Post by yetiman64 on 2010-06-04
To remove custom commands, look in your home folder, do CTRL + H to show hidden folders, then navigate to ~/.local/share/applications. The launchers you need to remove will have "userapp-" at the start of their name. Delete what you don't want to show.

---

### Post by wilee-nilee on 2010-06-04
> **PGScooter said:**
> Hi wilee, thanks for the reply. I'll try to be more specific :)

When I insert an audio CD, a menu appears, notifying me that I inserted an audio CD and kindly asking me with which application I would like to open it. There is an option that says "custom command" or something of that sort. I have entered several custom commands, but I do not see how I can remove them. They stay on the menu and now it is cluttered.

Thanks

If you right click on the cd and then properties then I think it's open with you will probably see the added custom commands. A screen shot of the cluttered menu would help me to understand.

---

### Post by PGScooter on 2010-06-04
Thank you yetiman, exactly what I was looking for. Do you happen to know how to remove the non-custom command options as well?

wilee-nilee,
ok, I'll post a screen shot. Let me run out to my car and get an audio CD. Be back in a sec :)

---

### Post by yetiman64 on 2010-06-04
You would have to edit /usr/share/applications/mimeinfo.cache as root for the specific type of cd (in your case -audio cd- search for x-content/audio-cdda)

eg.
```
gksudo gedit/usr/share/applications/mimeinfo.cache 
```then remove the unrequired entries on the x-content/audio-cdda line. Be carefull in here and ensure that semi-colons are left between the entries etc.

Edit: also if the entry in defaults.list for x-content/audio-cdda is in here as well, don't remove it. Check there 1st.

---

### Post by PGScooter on 2010-06-04
great! Thank you yetiman.

wilee-nilee,
Here are the screenshots.

---

### Post by wilee-nilee on 2010-06-04
> **PGScooter said:**
> great! Thank you yetiman.

wilee-nilee,
Here are the screenshots.

yetiman had the right solution. ;)

---

### Post by ryan858 on 2010-06-04
I would just right-click -> Properties -> Open With tab -> select unwanted entries -> click Remove/Delete

---

### Post by yetiman64 on 2010-06-04
> **ryan858 said:**
> I would just right-click -> Properties -> Open With tab -> select unwanted entries -> click Remove/Delete

For standard filetypes, yes that will work. But the OP was asking to remove entries for the open cd menu (a bit different situation).

Edit 2: have to check my first edit as it applies to .wav files and not open cd actions. Sorry for all the editing.

<Edit: there is actually a means to use ryan858s method. Via a nautilus window, right click on the audio cd, open in a new tab or window, then right click on a cdda file and use ryans method. Probably a much safer means to boot. Cheers ryan858 for the new info.>

---

### Post by yetiman64 on 2010-06-04
> **yetiman64 said:**
> .... Sorry for all the editing....

Also sorry to double post but wanted you to be aware of the edits, ryan858s suggestion will work for filetypes, including the .wav files on an audio cd.
But the properties options for the .wav files on the audio cd are different to the open cd options you asked about changing earlier and need to be done as previously suggested.

Cheers Nev. Oh, and if all is working ok for you could you mark your thread as solved, thanks.

---

### Post by PGScooter on 2010-06-04
great, thank you for the follow-ups and explanations!

---

