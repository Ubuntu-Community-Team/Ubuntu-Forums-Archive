---
title: "Gaim2 install problem :("
date: 2006-03-18
forum: General Help
---

### Post by B3Nji on 2006-03-18
Hey, 

I have followed the great tutorial on this [this]("http://www.ubuntuforums.org/showthread.php?t=133179&highlight=gaim2") forum but I am getting a problem when I try to install gaim2 beta2 using synaptic. 

[IMG]http://www.trum4n.me.uk/Sigs/Screenshot.png[/IMG]

I am a n00b when it comes to linux, only transfered to ubuntu last week completely getting rid of the virus people call windows! Could someone please tell me what to do?

Thanks for your help.

---

### Post by eyebrowman92 on 2006-03-18
in a terminal:
```
sudo apt-get build-dep gaim
```
then try again

---

### Post by B3Nji on 2006-03-19
hey, 

Thanks for your help but I am still getting exacly the same problem, I wonder if its something to do with a bad repository i am using? Ill have to scout around and try and find a new one see if that works. 

Any other suggestions? 
THanks

---

### Post by eyebrowman92 on 2006-03-19
when you did "sudo apt-get build-dep gaim" in a terminal, did it list packages to install?  that should've worked.  in a terminal type 

```
cat /etc/apt/sources.list
```

and post the output here.

EDIT: your problem might have been using that repository on the howto you followed.  try removing it from your list, and building gaim2.0beta2 from source from [http://gaim.sf.net](http://gaim.sf.net)

---

### Post by public_void on 2006-03-19
I installed from [source](http://sourceforge.net/project/showfiles.php?group_id=235&package_id=253&release_id=378940) without any problems. You should use checkinstall to have it in Synaptic.

In the terminal type
```

cd /path/to/where/gaim2/
tar -xvzf gaim-2.0.0beta1.tar.gz
cd gaim-2.0.0beta1
./configure
make
sudo checkinstall
```

Two useful links
[https://wiki.ubuntu.com/CompilingSoftware]("https://wiki.ubuntu.com/CompilingSoftware")
[https://wiki.ubuntu.com/CheckInstall]("https://wiki.ubuntu.com/CheckInstall")

---

### Post by B3Nji on 2006-03-19
[QUOTE=public_void]I installed from [source](http://sourceforge.net/project/showfiles.php?group_id=235&package_id=253&release_id=378940) without any problems. You should use checkinstall to have it in Synaptic.

In the terminal type
```

cd /path/to/where/gaim2/
tar -xvzf gaim-2.0.0beta1.tar.gz
cd gaim-2.0.0beta1
./configure
make
sudo checkinstall
```

Two useful links
[https://wiki.ubuntu.com/CompilingSoftware]("https://wiki.ubuntu.com/CompilingSoftware")
[https://wiki.ubuntu.com/CheckInstall]("https://wiki.ubuntu.com/CheckInstall")[/QUOTE]

dude, you rule!

Did everything you said, all went through without a hitch. I love checkinstall will use it all the time now! 

Cheers for you help and the excellent links to tutorial sites.

---

