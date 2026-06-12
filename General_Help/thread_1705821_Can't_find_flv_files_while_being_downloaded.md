---
title: "Can't find flv files while being downloaded"
date: 2011-03-12
forum: General Help
---

### Post by rva1945 on 2011-03-12
I switched from 9.10 to 10.10. In 9.10 there was a folder where the temporary flv youtube video files were downloaded, so I could capture them before being deleted.

Now with 10.10, which is the folder? /tmp isn't, I'm watching videos but no flashxxxxx files there.

---

### Post by Tamlynmac on 2011-03-12
Have you tried looking here:

1.Open the Nautilus file browser
2. Turn on "View/Show Hidden Files"
3. Look in "Home Folder/mozilla/firefox/alphanumerical.default folder/cache"

I think you will find the flash videos your seeking.

Good Luck & hope this helps

---

### Post by rva1945 on 2011-03-13
> **Tamlynmac said:**
> Have you tried looking here:

1.Open the Nautilus file browser
2. Turn on "View/Show Hidden Files"
3. Look in "Home Folder/mozilla/firefox/alphanumerical.default folder/cache"

I think you will find the flash videos your seeking.

Good Luck & hope this helps

Ok, but can I add that folder to Bookmarks in Nautilus? or will the (in this case) araldkl7.default change its name?

---

### Post by WorMzy on 2011-03-13
Don't worry, the name won't change. If you create a new profile, then the new profile will have a different random folder name.

---

### Post by TheOmegaCrisis on 2011-07-25
i'm not able to find the flv in cache...there are numerous folders.
i tried "locate *.flv" in terminal, but it didnt find any file in cache.
how can i find it??

i'm new to ubuntu. using ubuntu 11.04

---

### Post by androssofer on 2011-07-25
i noticed this aswell, i used to like making copies of flv files once they streamed... but they aint in /tmp anymore :-(

---

### Post by mcduck on 2011-07-25
> **TheOmegaCrisis said:**
> i'm not able to find the flv in cache...there are numerous folders.
i tried "locate *.flv" in terminal, but it didnt find any file in cache.
how can i find it??

i'm new to ubuntu. using ubuntu 11.04

The file doesn't have a proper file name, or any extension, so searching based on name won't help.

If you use a graphical file browser you should be able to detect the file based on it's icon, though. And if you want to find it from command line you could probably use the "file" command to find a file with correct MIME type ("application/x-shockwave-flash").

---

