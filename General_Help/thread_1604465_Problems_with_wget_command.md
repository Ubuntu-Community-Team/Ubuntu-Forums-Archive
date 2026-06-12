---
title: "Problems with wget command"
date: 2010-10-24
forum: General Help
---

### Post by imotox on 2010-10-24
I want to download a bunch of images from a site so I tried using wget. However it only downloads the thumbnails of those images and I can't get it to work better. Could one of you help me please and explain what I did wrong/needed to change so I can learn? This is what I have.

```
wget -P pics -p -nd -l2 -H -A.jpg -erobots=off http://boards.4chan.org/p/res/1044003
```


*FYI: If you know about 4chan and are scared of the link, this link is safe as it is to the photography board. These are artistically oriented pictures of a storm that was going on.*

I figured it out how to restrict it to the link that the pictures were on so I've got it now. If anyone is curious, the wget command that I used is

```
wget -P pics -H -nd -r -Dimages.4chan.org -A.jpg -erobots=off http://boards.4chan.org/p/res/1044003
```

Where:
'-P [name]' gives it the directory name of the folder in your home folder
'-H' Goes to outside links
'-nd' is no-directory which won't put the images in separate folders.
'-r' is recursive
'-A[.extension]' tells it what extensions to download
'-D[location]' is the server location you're restricting it to
'-erobots=off' makes it so you don't get bot files

---

### Post by imotox on 2010-10-24
bump. someone please help me?

---

### Post by Ahava591 on 2010-10-24
Please wait 24 hours to bump your thread. It is absolutely unreasonable to expect an answer to your problem within ten minutes. This is not a call center; we will help you as soon and as thoroughly as we can but it can take a little while.

I'm sorry I don't have your solution; but I hope your problem is solved soon and I wish you the best of luck.

---

### Post by imotox on 2010-10-24
> **Ahava591 said:**
> Please wait 24 hours to bump your thread. It is absolutely unreasonable to expect an answer to your problem within ten minutes. This is not a call center; we will help you as soon and as thoroughly as we can but it can take a little while.

I'm sorry I don't have your solution; but I hope your problem is solved soon and I wish you the best of luck.

All right, I understand. Sorry about that, I'm a little sleep deprived, intoxicated, and agitated. O:)

---

