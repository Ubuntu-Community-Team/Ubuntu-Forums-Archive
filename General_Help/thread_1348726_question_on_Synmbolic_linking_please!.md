---
title: "question on Synmbolic linking please!"
date: 2009-12-07
forum: General Help
---

### Post by listerdl on 2009-12-07
Hi - what I am trying to do is sync dropbox, (a folder and file syncing app) on a shared partition on my dual boot Windows 7 and Ubuntu.

When you install the program on windows it forces you to call the folder (to be syncd) "My Dropbox." In Ubuntu, the folder on the same partition is called "Dropbox" - i.e. no "My"

I have been on the very helpful forums at dropbox but just to understand the advice I was given:


> Just boot in linux, rename ~/Dropbox to ~/Dropbox_old (this is for a backup, not for be used, you can delete if thereafter), then link the mounted DB folder to this location: - Do they mean by ~ the Home Folder, i.e. Places > Home Folder?

The I am told to do this:

```
/home/elipas$ mv Dropbox Dropbox-not-used-anymore
/home/elipas$ ln -s "/media/WinData/My Dropbox" Dropboxx

And you should be set.

("/home/eliphas" is my home folder, where the Dropbox folder would be, and /media/WinData would be the current location of the windows My Dropbox folder) Definitely will work :)
```

Does /home/elipas$ in the above example mean that that is exactly what I need to start writing in the terminal?

All help appreciated!!

---

### Post by CaKiwi on 2009-12-07
Yes, ~ is shorthand for your home folder.

/home/eliphas$ is the terminal prompt for the poster who helped you. 

So open a terminal and type > 
mv Dropbox Dropbox-not-used-anymore

Then type
> ln -s "/media/WinData/My Dropbox" Dropbox

This assumes that your windows files are mounted under /media/WinData
You can find out if this is true by entering
> ls -l "/media/WinData/My Dropbox"
and looking to see if the files listed are the same as the files you see in the "My Dropbox" folder when booted into windows.

---

