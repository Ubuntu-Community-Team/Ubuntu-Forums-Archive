---
title: "Itunes hiding my music files from Ubuntu with a Black hole Folder"
date: 2011-02-09
forum: General Help
---

### Post by BlackRat90 on 2011-02-09
greetings,

I have my music all stored on a partition so that if windows is to crash I dont lose my music. I created the partition in window so it is ntfs drive E:/ Named Data Files

Anyhow on to the problem. When I used to use windows full time I used itunes to interface with my ipod, but now im using ubuntu on top of windows and all my files in the Music folder in the Data Files partition seems to be hidden. I uninstalled itunes, and started poking around in the folders config (while on windows) and it appeared that itunes had changed the ownership of the folder to (what i guessed to be) itunes.

All the music files are a MP3 format, and where not bought from itunes, and if i transfer the mp3s to another folder I can see the files in ubuntu, but i dont have enough space to move all my music this way. Either way I dont want to do that because itunes just made this personal.

The Folder its self seems to be some kind of black hole hiding anything I put into it, when i tried running ls on it i got this:
```
ls: reading directory .: Invalid or incomplete multibyte or wide character
```

Ive done everything i can to the folders config and nothing seems to fix it. I believe it is some kind of encryption hiding the files in the folder, and i was wondering if anyone has had any success in cracking this type of problem.

Thanks!
Nate

---

