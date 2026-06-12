---
title: "Help with dual boot Ubunto - disk space provblem."
date: 2010-09-20
forum: General Help
---

### Post by xieon on 2010-09-20
First off, sorry if this is in the wrong forum, I missed it in search, or anything like that. I'm really new, and this is my first time on an Ubuntu forum, or using this OS.

*I will try to post as many links/pictures as I can to make this easy. Problem is I'm on windows now, so it's hard to post what I see in Ubuntu.

My main OS is Windows XP. I went to Ubuntu and downloaded the side by side installer, where its a .msi and installs Ubuntu, then after a restart you can choose an OS. 

During installation it asked where I wanted to install it (what drive) and how much space. I choose to give it 25gigs. It didn't create a new partition, it just made a 25gig folder called Ubuntu on that drive. When I open it from windows, theres basically nothing there, just files with weird Linux extensions.

So I open Linux and it runs perfectly, however, when I go into the "my computer" thing for Ubuntu (forgot the name) there is no 25gig space. Instead there is a random 40 gig drive (maybe my window's C drive) and a 250 gig drive. (On windows I have a E and F drive that are the same, but I partitioned them, together they equal 250 gig.) Also, when I open the drive from Ubuntu it shows only some of the files. So the space reflects the whole drive, but viewing it only shows the files that were in the partition I install Ubuntu in.

Can someone help me with this. I want to be able to run windows and Ubuntu on the same computer, and I want to set aside a space for Ubuntu, and that only.

Should I uninstall Ubuntu. Then create a new small partition, and install it there? I'm almost positive that will work, but is there and easier way?

[I]
*One last thing, sorry. I'm alright at programming and stuff (Java, c++, etc) and I know Linux is good for stuff like that, but I want just a nice desktop to use along side windows. Ubuntu is free, and I like that, and it has great help and a nice easy installer that didn't mess up my computer. Should I stay with this, or if I have to partition/reinstall top fix the problem should I use a different version, if so what one, theres so many xbunto, kubunto, ugh. Please help, I feel like such a newb.[/I]

---

### Post by nothingspecial on 2010-09-20
I`m not sure if you even have a problem. Both Windows and Ubuntu work, yes?

From Ubuntu, open a terminal and post the output of

```
df -h
```

and ```
sudo fdisk -l
```

Into a reply here. If Ubuntu is running fine then stick with it. Xubuntu and Kubuntu are the same under the hood. Just a different set of default applications. Most noticably the desktop environments.

---

