---
title: "Changing Permissions"
date: 2012-01-28
forum: General Help
---

### Post by MrBandicootKid on 2012-01-28
Hello. I'm new here, so i have no clue if this is where im supposed to put this....

Anyway, I just got this awesome program: Anime Studio 6, and i tried to change permissions on the disc and I get an error sayin' I can't.
I tried wine. Nothing. I tried playonlinux. Nothing.
I don't know why, because this worked on an earlier version of Ubuntu and also Linux Mint. Is there any possible way to install windows stuff from a disc onto ubuntu? How do I do it?? Thanks.

---

### Post by mcduck on 2012-01-28
You can't change permissions on an optical disc, as there's no way the new permissions could be written to the disc. All optical media (with the exemption of DVD-RAM) are read-only filesystems by design. You need to move the fie(s) to a Linux filesystem if you want to change their permissions.

Anyway, to run the program with Wine you shouldn't even need execute permissions, as from the operating system's point of view it's Wine that you are executing, not the file on the disc. At least as long as you actually try doing it the correct way, by running "wine /path/to/somefile.exe" instead of trying to doubleclick the .exe file.

---

### Post by MrBandicootKid on 2012-01-28
so, if i just copy and paste the files into another folder on the desktop, the permissions should work?

---

### Post by mcduck on 2012-01-28
> **MrBandicootKid said:**
> so, if i just copy and paste the files into another folder on the desktop, the permissions should work?

Sure. Anywhere on your Linux system, and you should be able to set the permissions.  But like I said, you shouldn't need to. You aren't executing the .exe file, you are opening it with Wine just like you'd open a photo with Image Viewer or mp3 file with Banshee or Totem.

---

### Post by spenniecash on 2012-02-24
Hi Guys.

I have copied the files to my home folder, but it still wont open with wine.

Regards
Spencer

---

