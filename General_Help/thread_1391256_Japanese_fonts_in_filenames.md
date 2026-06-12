---
title: "Japanese fonts in filenames"
date: 2010-01-26
forum: General Help
---

### Post by wmd on 2010-01-26
Hello,

I have a problem concerning japanese character support in both KDE and Gnome. I have some files with japanese characters in their name lying on my server, which also happens to be running Ubuntu, just the server flavor.

When I ssh to the server and list the files there (in mc e.g.) everything show just fine. But once I list the folders containing them on back on my pc (the files are shared via samba), be it in Gnome file manager or Dolphin, the ones with japanese characters don't show up at all. When I open bash and use mc, I at least can see them, but the names are totally garbled.

One thing to note is that I didn't do anything on the server to support these characters, but they show up fine there.

Long story short, I don't know where to begin to find out what's wrong. Could it be Samba doing this (not very likely, since another Windows machine can read them just fine)? What do I have to do to get it working on my pc? :confused:

---

### Post by lambengolmor on 2010-01-26
I'm not very sure of this... Could it be that samba changes the encoding from utf8 so some microsoft-ish one that isn't recognized in ubuntu?
I know it's not the best fitting solution, but... Have you tried to install the japanese language packages from System->Administration->Language Support?

---

### Post by wmd on 2010-01-26
> **lambengolmor said:**
> I'm not very sure of this... Could it be that samba changes the encoding from utf8 so some microsoft-ish one that isn't recognized in ubuntu?
I know it's not the best fitting solution, but... Have you tried to install the japanese language packages from System->Administration->Language Support?


Yup I tried this first but to no avail. I also installed some fonts (ms mincho and gothic). I didn't reboot though, just logged in and out, could that be the reason it didn't work?

---

### Post by lambengolmor on 2010-01-27
I don't think the reboot can affect that, but trying shouldn't hurt... If it still doesn't work can you try making a kanji-named directory on your client and see if it's correctly shown from terminal? If yes, can you try accessing the server folder through something else than samba (ssh, nfs...)? This way we can be sure if the problem is on samba, on the server or on the client...

---

### Post by wmd on 2010-02-02
Okay, ssh'd to the server and listed these files, they show up just fine. As well as making a new file and add Kanjis as name on my desktop. Didn't try the NFS mount, but what I'm wondering is why these files show up as expected on a windoze system, which also has the very same share mounted?! Wouldn't that mean that samba is innocent and it's something else?!

---

### Post by lambengolmor on 2010-02-02
Well. I'm not sure, but I think that:

1) the kanji-support on the client works fine (the folder on the desktop are created and read)
2) the client and the server uses the same encoding (or have a common encoding) since ssh worked fine
3) I know for sure win xp (don't know vista-7) by default don't use utf8 and have issues with utf8 files.

So my guess is:
samba (or someone else in the folder-sharing process) communicates in some micorsoft-ish encoding to keep compatibility with windows (that's the purpose of samba, for this I think it could be its fault).

I suggest to:
1) ask to someone that knows samba issues well (I don't)
2) do some research about how to install microsoft encodings on ubuntu (I like utf8 so i never cared about the problem)

Good luck!

---

### Post by wmd on 2010-02-02
> **lambengolmor said:**
> Well. I'm not sure, but I think that:

1) the kanji-support on the client works fine (the folder on the desktop are created and read)
2) the client and the server uses the same encoding (or have a common encoding) since ssh worked fine
3) I know for sure win xp (don't know vista-7) by default don't use utf8 and have issues with utf8 files.

So my guess is:
samba (or someone else in the folder-sharing process) communicates in some micorsoft-ish encoding to keep compatibility with windows (that's the purpose of samba, for this I think it could be its fault).

I suggest to:
1) ask to someone that knows samba issues well (I don't)
2) do some research about how to install microsoft encodings on ubuntu (I like utf8 so i never cared about the problem)

Good luck!

Your  hunch was right indeed, it was Samba playing with encodings. Mounting the same directory with NFS results in everything being readable, thank you for your input! =D>

Question is, did I forget something in my smb.conf/messed something up or is it Samba itself.....

---

