---
title: "Moving multiple files via command line"
date: 2010-09-15
forum: General Help
---

### Post by Zeenomorph on 2010-09-15
I liked the idea of the "cosmos" screensaver/desktop, but wanted to add my own pictures to the application.  I navigated to /usr/share/backgrounds/cosmos and tried to drag and drop.  I quickly found that I did not have permission to do this.

I googled my problem and found some command line tutorials telling me to sudo cp.  My problem is that I have about 30 pics that I want to move in there, and I don't think I can just move the directory, they have to be in that folder as the pictures themselves.

I don't really feel like typing the cp line multiple times with multiple randomly named image files.

Is there a way to have the command line cp all of my files from one directory to another?

---

### Post by cgroza on 2010-09-15
This is the general way to use it:

```
cp  -r (file to copy) (where to copy)
```
Substitute the brackets with the necessary path.
The 'r' option allows you to go recursively into the folder.

---

### Post by Zeenomorph on 2010-09-15
I'm not sure I understand.  (file to copy) seems to imply copying 1 file.

Would I just pick a random file in the folder, and all the files would be copied?  What if I just want the file in that folder, and not files further into the file tree?

Is this possible?

---

### Post by 3rdalbum on 2010-09-15
You need to copy files into a folder as root. There's two ways of going about it: Run the 'cp' command as root, or run a file browser as root so you can just drag and drop the files.

For cp, you'd use the * (wildcard or "everything") operator to "Copy all files from /home/username/Pictures/ into /usr/share/backgrounds/cosmos/":

```
sudo cp /home/username/Pictures/* /usr/share/backgrounds/cosmos/
```

Or to just run the file browser as root (which is what I'd do in your situation):

```
gksudo nautilus
```

You might find it more convenient to install the 'nautilus-gksu' package from Software Center. With this installed, on all subsequent times you log in, you can choose a file or folder and right-click to access an "Open as Administrator" item.

---

### Post by Zeenomorph on 2010-09-16
That worked brilliantly.  Exactly what I needed.  Thank You.

---

