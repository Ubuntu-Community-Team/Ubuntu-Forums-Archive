---
title: "Moving Pendrive Files to Trash"
date: 2012-01-02
forum: General Help
---

### Post by whatthefunk on 2012-01-02
This has been driving me crazy for a long, long time.  This has happened on every Ubuntu spin-off Ive used.  If I delete a file on my pendrive, it doesnt actually delete it, it sends it to the pendrive trash file which is pointless.  If I try to delete the files in the pendrive trash folder, it either gives me an error message or deletes them and puts them back in the trash file.  This is ridiculous.  If I want to delete the files I have to do so through a terminal.  How can I correct this situation?

---

### Post by whatthefunk on 2012-01-02
Let me answer my own question....press SHIFT+DELETE.

---

### Post by dozdozez on 2012-01-02
The delete key just moves files into trash, if you want to delete them press shift+del.

---

### Post by pretty_whistle on 2012-01-02
> **whatthefunk said:**
> Let me answer my own question....press SHIFT+DELETE.
I agree with you.  What a dumb setup.

Whenever I'm on a pen drive I just use SHIFT+DELETE so you're correct that rids the trash once and for all.

What a weird setup though.  Annoying too.

---

### Post by whatthefunk on 2012-01-02
I wonder what the logic behind this is.  Wouldnt it be better to send it to the computer trash file?

---

### Post by pretty_whistle on 2012-01-02
> **whatthefunk said:**
> I wonder what the logic behind this is.  Wouldnt it be better to send it to the computer trash file?
It would make more sense.

Apparently they didn't want to make sense.

---

### Post by jefelex on 2012-01-02
> **pretty_whistle said:**
> It would make more sense.

Apparently they didn't want to make sense.

Makes perfect sense to me - the deleted files are stored in the .Trash folder in the / directory for separate devices. If they were stored in your home directory .Trash file, then the OS would have to copy them to your home directory, and could take a significant length of time depending on the file size. Take a usb stick - if you delete a 1gb file on the USB device, do you think it would be more effective to copy the entire file to your home directory, or simply move it to the / directory on the USB? - also, if the OS cannot delete the file to trash, it will ask if you are sure you want to delete, since it has no access to / on the device (a network device or such)

---

### Post by audiomick on 2012-01-02
In my experience, if you unmount the USB drive correctly before you pull it out, you get asked if you want to empty the trash beforehand. To unmount, right click on it in the file manager and select "unmount",  or click on the symbol that looks like the "eject" button of a CD player.

---

### Post by pretty_whistle on 2012-01-02
No wonder it doesn't make sense.  I recall deleting something off the USB stick and seeing it land in the trash on the computer.  I unplugged the USB stick and then deleted said trash.  Then later I plugged in that same USB stick and viola!  there's the deleted file in the sticks .trash.  Mind you I already deleted the thing.  Ugg. 

 If a person doesn't shift+delete their trash they have to delete it more than once.  Ridiculous to have to delete something more than once.  To top it off, when I looked in the .trash folder I found files I had deleted *days ago - *that would be about 6 deletes ago, little did I know.  That meant a person *couldn't* assume a deleted file was just that, deleted.

---

### Post by whatthefunk on 2012-01-02
> **audiomick said:**
> In my experience, if you unmount the USB drive correctly before you pull it out, you get asked if you want to empty the trash beforehand. To unmount, right click on it in the file manager and select "unmount",  or click on the symbol that looks like the "eject" button of a CD player.

That doesnt happen to me.  I just have to delete everything twice, which is insane.  Whjy doesnt it just hard delete to begin with?

---

