---
title: "OSMO backup and restore"
date: 2011-11-02
forum: General Help
---

### Post by jereece on 2011-11-02
I have been using Osmo 0.2.8 as a task reminder for about a year and love it...well except for the popups.  Anyway, I am building a new computer and want to transfer my Osmo task data to my new computer.  Osmo provides an "Export Tasks" button which exports to an .ics file.  However there is no "Import Tasks" button.  Osmo is advertised to maintain it's data in a simple XML file so I thought I may be able to simply copy it and move it to my new computer.  However searched for it on my hard drive and was unable to find it. I searched Google and this forum for help but found nothing useful.

Any suggestions on how to backup and restore Osmo task data?

Thanks,
Jim

---

### Post by notgary on 2011-11-10
The way most applications work is that they store their confiuration data in a hidden directory in your home directory called ~/.config/<app name here>. If you want to copy your data to a new computer, then all you have to do is copy that directory over before you install the application on the new system. Once you do install it, it should detect the existing data and load it automatically.

One thing you could consider is just copying your entire home directory, taking care to copy the hidden directory and files as well. That'll make the migration process a whole lot easier.

---

### Post by Bramkaandorp on 2012-01-08
BUMP

Osmo has the ability to export an .ics file, and I can import it via the calendar end other the application, but I see no way of importing those tasks to the task list short of retyping it all.

Has anyone found a workaround for this?

Not that it's crucially important, but it could save me a day of retyping (yes, it's that much, considering that I don't want to get rid of the history).

Oh, and I only have the ics file, no other folders or anything.

---

### Post by jereece on 2012-01-08
Notgary's solution worked for me.


> **Bramkaandorp said:**
> BUMP

Osmo has the ability to export an .ics file, and I can import it via the calendar end other the application, but I see no way of importing those tasks to the task list short of retyping it all.

Has anyone found a workaround for this?

Not that it's crucially important, but it could save me a day of retyping (yes, it's that much, considering that I don't want to get rid of the history).

Oh, and I only have the ics file, no other folders or anything.

---

### Post by Bramkaandorp on 2012-01-08
> **jereece said:**
> Notgary's solution worked for me.

That's great. Sadly, I don't have the folder any more. That's why I posted here, in stead of trying the solution given by Notgary.

---

### Post by jereece on 2012-01-08
If you have Osmo still installed and it's working, you have the folder.  You have to show hidden folders to see it.

---

### Post by Bramkaandorp on 2012-01-08
> **jereece said:**
> If you have Osmo still installed and it's working, you have the folder.  You have to show hidden folders to see it.

Alas, not on a clean install.

That's my problem. I did a clean install, but I only have the ics file. I don't have the folder any more, because I forgot to take it with me.

---

### Post by Bramkaandorp on 2012-02-15
Bump

---

