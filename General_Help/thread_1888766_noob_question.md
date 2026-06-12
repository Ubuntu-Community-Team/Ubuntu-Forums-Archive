---
title: "noob question"
date: 2011-11-30
forum: General Help
---

### Post by aphung2 on 2011-11-30
I'm following this guide [http://automate-everything.com/2009/08/gnome-and-autospec-notifications/](http://automate-everything.com/2009/08/gnome-and-autospec-notifications/)

I'm on the step

"
As you can see I use the fail.png and pass.png images  to show those cheesy smileys : ). You can download them here and copy  them to *~/.autotest_images/*.
  [autotest_images.zip]("http://automate-everything.com/wp-content/uploads/2009/08/autotest_images.zip")"


how exactly do I copy files to ~/.autotest images/. I don't understand. 

I also extracted the file and it gave me a home folder with an Eduardo folder, and nothing else after that.

When I open with ArchiveManager I can finally see the image files.

---

### Post by stinkeye on 2011-11-30
When viewing the extracted files press ctl+h to see any hidden files.
The preceding dot makes files/folders hidden.

You will see a folder named **.autotest_images** in /home/eduard
Just copy the folder **.autotest_images** to **your** home folder.
It will now be a hidden folder in your home directory.

---

### Post by galvatron408 on 2011-11-30
how exactly do I copy files to ~/.autotest images/. I don't understand. 

~/ is your user's home directory. go ahead.... try it.... type "cd ~" or "cd ~/" and voila.... you got back in to your home directory... although, an easier way of getting back in to your directory would be to simply "cd".

so, to copy a file in to your home directory, you could....

"cp filename /home/user/."

or you could....

"cp filename ~/."

---

### Post by bluexrider on 2011-11-30
@stinkeye

you opened this, its time to close it.

---

### Post by stinkeye on 2011-12-01
> **galvatron408 said:**
> how exactly do I copy files to ~/.autotest images/. I don't understand. 

~/ is your user's home directory. go ahead.... try it.... type "cd ~" or "cd ~/" and voila.... you got back in to your home directory... although, an easier way of getting back in to your directory would be to simply "cd".

so, to copy a file in to your home directory, you could....

"cp filename /home/user/."

or you could....

"cp filename ~/."
In the OP's problem
you will see that the zip archive(which I downloaded) contains the directory structure
**/home/eduard/.autotest_images/** but he didn't know about hidden files so once extracted couldn't find the .autotest_images folder.


So all he had to do was extract the archive and use ctrl+h to 
show the hidden **folder** .autotest_images.
Then copy that folder to his home folder.
So now he will have  **~/.autotest_images** directory containing the images.
```
glen@Oneiric:~$ cd ~/.autotest_images
glen@Oneiric:~/.autotest_images$ ls
fail.png  pass.png  pending.png
```


If a **~/.autotest_images** directory exists, to copy a file there you would use
```
cp */path/to/file* ~/.autotest_images
```
or just use nautilus showing hidden files.

---

### Post by galvatron408 on 2011-12-01
well, he asked how he was going to copy in to ~/.file, so I explained it to him... with a title like "noob question", I figure he didn't have a clue what ~ meant.

---

