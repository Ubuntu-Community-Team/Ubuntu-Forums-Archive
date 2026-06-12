---
title: "firefox broken"
date: 2009-10-30
forum: General Help
---

### Post by stans on 2009-10-30
After the last Karmic update - Firefox just ends... never does open. Should I just move over to Seamonkey ?

---

### Post by lovinglinux on 2009-10-30
Not necessary. It's probably a corrupted profile.

Open the Profile Manager:

```
firefox -P
```

It will allow you to create and start a clean profile.

---

### Post by stans on 2009-10-30
Excellent ! It worked... thank you very much !

I did lose the bookmarks, but those are easy to recreate.

---

### Post by lovinglinux on 2009-10-30
> **stans said:**
> Excellent ! It worked... thank you very much !

I did lose the bookmarks, but those are easy to recreate.

Close Firefox, then open the folder  ~/.mozilla/firefox and locate the default profile folder. Open it and copy the file **places.sqlite** then paste inside the new profile folder. This will restore your bookmarks.

---

### Post by stans on 2009-10-30
OK - there's one file with 'default user' as extension, the other one is 'default'. 

Kinda confusing.

One is empty, the other one had new bookmarks in it. 

When I created the new profile I let it use default as the user... so perhaps I overlaid what was there ?

---

### Post by lovinglinux on 2009-10-30
> **stans said:**
> OK - there's one file with 'default user' as extension, the other one is 'default'. 

Kinda confusing.

One is empty, the other one had new bookmarks in it. 

When I created the new profile I let it use default as the user... so perhaps I overlaid what was there ?

I guess you have copied from the new profile to the old one, overriding the bookmarks. You can still recover them. Open Firefox with the old profile, then go to "Bookmarks >> Organize Bookmarks" then click the "Import and Backup" and select the "Backup" option. Save the file in your desktop. Close Firefox. Open Firefox again, but this time using the new profile and go to "Organize Bookmarks" and restore your bookmarks using the backup saved on your desktop.

---

### Post by stans on 2009-10-31
I've read and reread the information you referred to but don't see how to actually select a profile when I load Firefox. 

I guess some things that are second nature to one person are a mystery to another...

I have been able to recreate my small list of bookmarks so we may as well consider this issue closed.

Thanks for your assistance.

---

### Post by lovinglinux on 2009-10-31
> **stans said:**
> I've read and reread the information you referred to but don't see how to actually select a profile when I load Firefox.

```
firefox -P
```

---

### Post by stans on 2009-11-02
So it is done with the profile manager. I thought it could be selected when Firefox is invoked.

---

### Post by lovinglinux on 2009-11-02
> **stans said:**
> So it is done with the profile manager. I thought it could be selected when Firefox is invoked.

You need to untick the option "Don't ask at startup" in the Profile Manager, then it will prompt for the desired profile whenever you launch Firefox.

---

