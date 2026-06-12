---
title: "Delete Photorec Files on Desktop"
date: 2012-08-11
forum: General Help
---

### Post by hortonjohnny10101 on 2012-08-11
This might be a standard issue, but all the posts on this website and all around the website that have somehow resolved it do not work for me. Right now, I have over 100 recup_dir files on my desktop, and I have successfully avoided them troubling me, until now. I have about 4 MB of space left on my hard drive. I need help getting rid of them. Here is a screenshot. [http://i713.photobucket.com/albums/ww136/JZPtown/Ubuntu/Screenshot.png](http://i713.photobucket.com/albums/ww136/JZPtown/Ubuntu/Screenshot.png)
Please help me. I am in desperate need to clear this up in time for the school year. I am willing to restore Linux to when I last backed it up, but I again have no idea how to get there. Thank you so much!

---

### Post by GreatDanton on 2012-08-11
What happened if you right click on icons and click move to trash? Do you get permission denied message?

Regards.

---

### Post by cryptotheslow on 2012-08-11
Open a Terminal and enter:

```
gksu nautilus
```

That will open your file manager with admin privileges (so be careful!).

Then navigate to /home/your-username/Desktop and delete the files.

---

### Post by hortonjohnny10101 on 2012-08-26
Thanks for the response you guys! I'm sorry for not being prompt. When I try to delete the files, I get a warning like "cannot delete f20123.txt' and such. But when I go into root and desktop, my files are gone. I cant see any of them. What else can I do from here?

---

### Post by squenson on 2012-08-26
I guess you are in the wrong folder. You must first click in Nautilus in the "File System" (on the left column), then the folder "home", then "yourname", then "Desktop". Now you should see all you PhotoRec files.

---

