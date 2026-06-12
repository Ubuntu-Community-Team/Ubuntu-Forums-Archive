---
title: "How do I make a multi-part archive of a single .ISO file?"
date: 2009-07-02
forum: General Help
---

### Post by Donalb on 2009-07-02
Hey all,

(I'm still on Intrepid btw, planning to jumpy Jaunty to go to Karmic).

Anyway I have a 4.1 GB ISO file. I want to make a multi-part rar of it.

Normally for a file I'd just choose a right click in Nautilus, select the desired file size and let it off.

However because it's an .ISO I don't have a right click option.

If I open Archive Manager it'll make it into a tarball but no multipart options seem to be available to me in Archive Manager. And I still don't then have the option to make the tarball into a .rar archive.

Any suggestions?

---

### Post by Subban on 2009-07-02
If you have rar installed skip this command, if it isn't installed yet use it:
```
sudo apt-get install rar
```

Open a terminal at the location where the files to encode are (your ISO files I guess), can be donee by right click in the folder window in nautilus and choose "Open in Terminal" (I think that is installed by default). If not open a terminal and cd to the folder.

then you can use:

rar a -v15m archivename filename

Swapping out archivename for whatever you want the archive to be called, and filename for what the ISO file is called or using wildcards etc.

For example:
```
rar a -v15m JauntyISO *
```

---

### Post by moster on 2009-07-02
There is two easy GUI solutions. 

1. First install 7zip from menu add/remove. Then right click on file, choose create archive, choose 7zip and bellow you have a split archive option :)

2. Install winrar for windows right into ubuntu. It will even put in menu shortcut for you. Look in wine submenu. (wine install first if you already do not have it). Then manually create archive from his window because right click do not work in ubuntu.

With 7zip it cannot be easier even in winodows :D

edit:
pardon, you do not have option "create archive" on ISO files. You will have to open manually file roller (archive manager) and there click "new" then "add files"... well you will get it :)

---

### Post by Donalb on 2009-07-03
Thanks very much guys. I just did the terminal option since it was the quickest. Sorted.

Regards

---

