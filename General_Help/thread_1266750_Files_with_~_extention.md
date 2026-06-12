---
title: "Files with ~ extention"
date: 2009-09-15
forum: General Help
---

### Post by Chrus on 2009-09-15
Why do i have so many files ending with ~

Ive noticed every time i open a file to edit, i end up with a copy of the file with the same name but with a ~ at the end. Why?

Are these files important? Can I delete them? Or is there a way to stop them being created in the first place?

Cheers

Chrus

---

### Post by Woody1987 on 2009-09-15
Im not entirely sure what they are but i always delete them and have never had any bad consequences as a result.

---

### Post by jzacsh on 2009-09-15
> **Chrus said:**
> Why do i have so many files ending with ~

Ive noticed every time i open a file to edit, i end up with a copy of the file with the same name but with a ~ at the end. Why?

Are these files important? Can I delete them? Or is there a way to stop them being created in the first place?

Cheers

Chrus

i'm not sure, but it sounds like you're talking about when the application you're opening with locks the file (so if another app tries to use it, its made clear the file is already in use). does the new file have something like ".lock" in the name? does the file go away when you close the app?

---

### Post by Chrus on 2009-09-15
> **jzacsh said:**
> does the new file have something like ".lock" in the name? does the file go away when you close the app?

Nope, no .lock in the name. The name of the new file is exactly the same, just with ~ added to the end of the extension.

The file stays there after i close the app. Will stay there even after I delete the original file.

I should also point out they are hidden files.

---

### Post by oboedad55 on 2009-09-15
> **Chrus said:**
> Why do i have so many files ending with ~

Ive noticed every time i open a file to edit, i end up with a copy of the file with the same name but with a ~ at the end. Why?

Are these files important? Can I delete them? Or is there a way to stop them being created in the first place?

Cheers

Chrus

If you're using gedit these are backup files. They're created when you change a file you're working on then save it. You can delete them if you don't want them although they will typically take up little space since they're text files.

---

### Post by jzacsh on 2009-09-15
> **Chrus said:**
> Nope, no .lock in the name. The name of the new file is exactly the same, just with ~ added to the end of the extension.

The file stays there after i close the app. Will stay there even after I delete the original file.

I should also point out they are hidden files.

that really sounds exactly like the locking mechanism (or so I think that's what it is, i never looked it up to confirm) that I've seen. hmm...wish I could help more... maybe try opening the original file with another app, see if it lets you?

i just did a little googling, and read that they're temp files, so I guess you can delete them...

---

### Post by Chrus on 2009-09-15
Thanks for the info guys.

Is there an easy way to delete them all in one go? Havent really noticed them till now, and they are all over my HDD. Seems like every file I've opened in gedit in the last 6 months has one.

Can I stop gedit from creating them in the first place? Or delete them as soon as I close gedit?

---

### Post by amac777 on 2009-09-15
In Gedit, go to Edit->Preferences->Editor, and then uncheck the box labelled, "Create a backup copy of files before saving."

---

### Post by Chrus on 2009-09-15
> **amac777 said:**
> In Gedit, go to Edit->Preferences->Editor, and then uncheck the box labelled, "Create a backup copy of files before saving."

BRILLIANT!

Thanks mate.

---

### Post by P4man on 2009-09-15
actually, I happen to think that backup feature is brilliant. Unless you're extremely short on disk space, Id just leave it like that. Sooner or later you're gonna make a wrong edit and you're gonna wish you had a backup.

---

### Post by blackened on 2009-09-15
> **P4man said:**
> actually, I happen to think that backup feature is brilliant. Unless you're extremely short on disk space, Id just leave it like that. Sooner or later you're gonna make a wrong edit and you're gonna wish you had a backup.

Agreed. It's been a lifesaver for me in the past, and it's not like text files are so huge that you're going to notice the lost space. I would leave it on as well, they'll be useful now that you know what they are.

---

### Post by jzacsh on 2009-09-15
> **P4man said:**
> actually, I happen to think that backup feature is brilliant. Unless you're extremely short on disk space, Id just leave it like that. Sooner or later you're gonna make a wrong edit and you're gonna wish you had a backup.

i would agree, but doesn't it sound like Chrus's backups are not working properly (eg. going away eventually)? ...
> **Chrus said:**
> 
[...] they are all over my HDD. Seems like every file I've opened in gedit in the last 6 months has one.


---

### Post by amac777 on 2009-09-15
I don't think the backup files ending in ~ will ever go away (unless you delete them yourself). They just stay there in case you need them later.

---

