---
title: "Whre would your recommend downloaded source files from the web be placed?"
date: 2010-06-26
forum: General Help
---

### Post by shabazzk on 2010-06-26
I'm exhausting my search for a simple question, so I now feel it's time to ask. 

**[SIZE="4"]Where would you recommend to extract source code from downloaded tar-balls?[/SIZE]**

Would you place them in /usr/src or /usr/local/src

I am not new Ubuntu (3 years), but I'm just starting to understand the file system. Lately I've made much effort to getting used to installing software from tar-balls, instead of waiting for someone else to provide me with the latest. I plan to test the latest software to help in the effort to make Ubuntu/Linux more user friendly and I want to learn to program interfaces for some very complex software I use. But I would like some suggestions so I can skip some unwarranted trial and error.

Also can someone point me to a place where I can read about the file/folder structure of Linux to gain insight? 
NVM, I did a search and got loads of stuff like this: [http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

---

### Post by warfacegod on 2010-06-26
I just keep my extracted tarballs in a folder with all my other .debs and what not, inside my /home partition. I do the same thing with folders for apps that I have compiled myself so that don't have to go through the hassle of doing it again.

---

### Post by jerome1232 on 2010-06-26
Sort of the same answer I have ~/src, that's where I put my source code.

Personal preference, just keep it consistent and your fine.

---

### Post by SaintDanBert on 2010-06-26
Within $HOME I have a ~/Downloads folder that catches whatever I grab
from the net -- typically tar balls, iso's and deb's.

I also have a ~/Prj folder. Inside there, I have separate folders for each thingy I'm working on or tinkering with.

After I fetch something, I'll move files from ~/Download to ~/Prj/something.
If I have a tar-ball, I'll unpack it there.  I might also loop-mount an iso and put its contents there as well.

When I'm happy with things, I'll put them into /usr/local/* -- 'src' for the source files, 'bin' for executables and scripts, 'lib' for libraries and so on. I also create a sym-link '~/Prj/local' that points to /usr/local.  That way, my $HOME backup grabs all of my tinker artifacts.

Here is an example, I download the ZIP archive for 'woof' into ~/Download.
I'll make ~/Prj/woof and move the archive into there.  Next I'll unpack the archive inside ~/Prj/woof. I'll play with this utility from ~/Prj until I'm happy. At that point, I'll move things to /usr/local/*.

NOTE -- There is debate about whether to use /usr/local or /opt.
As the saying goes, "... your mileage may vary ..."

Enjoy,
~~~ 0;-Dan

---

### Post by shabazzk on 2010-06-28
After looking here: [http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

I decided to download source tar/bz2 files to my ~/Downloads folder, extract them there, then move, build and install them from "/usr/local/src" directory. From there, using the default install directories, they will usually install into "/usr/local/lib" and "/usr/local/bin", and of course other places where the install sees fit. After the install I usually run "sudo ldconfig" to pick up the new libs made from the install.

The only problem I have now, is that I have duplicate, yet different versions of some apps. So I need to find a way to update ones that are already installed, instead of adding a second one.

Since I'm normally a windows user I guess I never really thought about where I should put applications, since you usually just download them and they install where ever they want. But in Linux you can not just download apps, but you can also rebuild them and modify them. So more thought is needed.

---

