---
title: "Need to backup a large Hard Drive, and stop a weird deletion error"
date: 2009-08-09
forum: General Help
---

### Post by sexualpotatoes on 2009-08-09
1) I need an easy to use program that will sync two 750GB hard drives or can do incremental back ups. It needs to be easy to use and it needs to have a GUI. I searched this for a while but I have yet to find a good program for backing up my drives

2) When I delete from my 2 750GB NTFS drives ubuntu decides to move it to my trash on my 80GB HDD which takes forever how to I delete large files without sending it to the trash?

---

### Post by AmerNewbieInDE on 2009-08-09
are you using these drives as a mirror? are they the same make?

---

### Post by phillw on 2009-08-09
If your 2 drives are in a mirror raid setting, they are already backing each-other up.

Do you want to seperate them into 2 single drives, with a primary & backup? - not too sure what you're trying to do.


Phill.

---

### Post by jerrrys on 2009-08-09
don't know if you call it easy, but rsync is first thing that comes to mind.  you want a GUI, grsync

[http://en.wikipedia.org/wiki/Grsync](http://en.wikipedia.org/wiki/Grsync)

---

### Post by sexualpotatoes on 2009-08-09
grsync seems good I'll give it a try.

The two HDDs are identical but not setup in RAID or any other similar formats

---

### Post by scouser73 on 2009-08-10
Have a look at [[COLOR="Red"]**Pybackpack**[/COLOR]]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html"), it should suit your needs, and it has a GUI.

---

### Post by callumacrae on 2009-08-10
File manager -> Edit -> Preferences -> Behaviour -> Include a delete command that...

~Callum

---

### Post by sexualpotatoes on 2009-08-12
> **callumacrae said:**
> File manager -> Edit -> Preferences -> Behaviour -> Include a delete command that...

~Callum
That doesn't help, I don't see any relevant options. You are probably using ubuntu...

Anyone have any thoughts on how to fix my deletion problem?

---

### Post by amac777 on 2009-08-12
If you highlight a file in nautilis and then press Shift-Delete, it should delete the file directly without putting it in the trash first.

edit: and I just confirmed what Callum wrote, I have the option to include a delete command that bypasses the trash so you might want to check again. And I think we can all assume we are using ubuntu since this is a ubuntu help forum! :)

---

### Post by sexualpotatoes on 2009-08-12
> **amac777 said:**
> If you highlight a file in nautilis and then press Shift-Delete, it should delete the file directly without putting it in the trash first.

edit: and I just confirmed what Callum wrote, I have the option to include a delete command that bypasses the trash so you might want to check again. And I think we can all assume we are using ubuntu since this is a ubuntu help forum! :)
Again I do not have ubuntu. If you have xubuntu and nautilus then you installed nautilus because thunar is the default file manager in xubuntu.

The shift+delete does work though thanks (it's good enough for my uses)

---

### Post by amac777 on 2009-08-13
Oh, my bad. I didn't see you had [xubuntu] in the title. Glad the shift-delete thing worked in thunar though.

---

