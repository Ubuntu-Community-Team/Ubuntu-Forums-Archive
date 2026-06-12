---
title: "Installing tar.gz files"
date: 2010-09-09
forum: General Help
---

### Post by polardude1983 on 2010-09-09
Ok so I thought installing tar.gz files was complicated. Where you have to extract then go into the terminal and cd to the directory then do ./make ./sudo install and other stuff. But I just watched a vid on all you need to do is extract the directory to your home folder. Go to edit applications and just select the program. I'm confused on does that actually work. How is it actually installing if all he did was extract? I'm using 10.04

---

### Post by apmcd47 on 2010-09-09
> **polardude1983 said:**
> Ok so I thought installing tar.gz files was complicated. Where you have to extract then go into the terminal and cd to the directory then do ./make ./sudo install and other stuff. But I just watched a vid on all you need to do is extract the directory to your home folder. Go to edit applications and just select the program. I'm confused on does that actually work. How is it actually installing if all he did was extract? I'm using 10.04

Point us to the video so we can all have a good laugh!

Seriously, there are applications which may not need the complicated makes;  perl, ruby, python and shell scripts come to mind. This could be one of those. Without a link to the video we can't judge.

Andrew

---

### Post by linuxfreeordie on 2010-09-09
tar.gz is just an archive format, it can contain anything from regular files like pictures or data, a binary, or source files.

When you are talking about installing something, it usually just has the binary files in it, which means you can simply unpack them to any directory you want and add them to your programs like you saw presumably saw in the video. If you have an options to download the source or binary, and you don't want any hassle, choose the binary (they will probably both be tar.gz).

If it does contain source files, you will need to cd into the directory and do ./configure, ./make, and ./make install, or something like that.

---

### Post by polardude1983 on 2010-09-09
Here is the vid

[http://www.youtube.com/watch?v=e1WpFBLTRD8&feature=youtube_gdata_player](http://www.youtube.com/watch?v=e1WpFBLTRD8&feature=youtube_gdata_player)

---

### Post by linuxfreeordie on 2010-09-09
Yeah that video is correct for probably 95% of the stuff you download. Like I said it's a little disingenuous saying that's how you install tar.gz files, because tar.gz is just an archive format like .zip or .rar - it can contain anything. That is how you "install" binary executable files, which is usually what is in a tar.gz if you get it from a website. More to the point, that's how you add executable files to your menu (in his example he also could have just run songbird by clicking on it from his home folder).

However you will have to do commands like ./make ./make install if you open of the tar.gz and find source files, such as MAKEFILE and a bunch of .cpp and .h files.

Also, I'm not sure you home folder is the best place to put all the programs you download, but it is up to you.

---

