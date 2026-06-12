---
title: "installing non ubuntu applications"
date: 2010-07-04
forum: General Help
---

### Post by 3pinner on 2010-07-04
I have  linux based photo editing software that I want to install so that it can be accessed through the Applications menu.
Which system folder do I install it in?
Or what terminal commands do I use to install so it is part of the system?
Thanks

---

### Post by warfacegod on 2010-07-04
What kind of file is it?

---

### Post by 3pinner on 2010-07-05
Sorry - left out the most essential!
lightzone tar.gz

---

### Post by philinux on 2010-07-05
> **3pinner said:**
> Sorry - left out the most essential!
lightzone tar.gz

Move that file to your home folder then right click and choose extract here.

In the newly extracted folder you will find the app. All you need to do is then create a launcher either on your desktop or in the menus.

The other place you could put it is in the /opt directory. There might/should be a read me file when you extracted the archive.

---

### Post by warfacegod on 2010-07-05
If you double click it, it will open with the extraction tool. Extract it to somewhere easy like your Downloads folder, for example. Then go to that folder and open it up. There should be a Readme file or possibly an Installation file with instructions on how to install it. It will probably tell you to do something like:

```
cd ~/Downloads/lightzone-#.#.#
```

```
sudo make install
```

This may be useful: [http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

### Post by 3pinner on 2010-07-06
thank you and sorry about the long delays between posts..
I usually download it to my desktop, extract it to a folder on the desktop, and use it from there.

I guess I should have asked: can I put it in the /usr/lib folder,  creating a .lightzone folder? then create a launcher in the applications menu?
I really want to know how and where applications are placed when they are installed with synaptic or apt for instance. I realize there must be a shell script to put all the bits and pieces where they belong in the file system.
Any way I can do that with other applications I download (and know for CERTAIN are clean)?
Thanks

---

