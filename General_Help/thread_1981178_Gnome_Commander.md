---
title: "Gnome Commander"
date: 2012-05-16
forum: General Help
---

### Post by deBachin on 2012-05-16
I have not been able to find a filter in Gnome Commander that copies or moves only the latest version.

Can anyone recommend a file manager for Ubuntu 12.04 that combines two folders updating new files and deleting duplicates.

---

### Post by sudodus on 2012-05-16
You can synchronize directories (or drives) using Unison, which can be installed with
```
sudo apt-get install unison
```
It is a bit advanced to set up, but after that is is straight-forward to use. Unison also looks into the files, not only at the date and size of the files.

On a lower level you can probably use midnight commander
```
sudo apt-get install mc
```

---

### Post by LewisTM on 2012-05-16
Krusader is a two-pane file manager that can easily synchronize two directories, you could use it as a merge tool. It will find duplicates and can copy the most recent. It provides lots of point-and-click options. I prefer Unison for repeated tasks; it's faster but harder to setup.

Cheers!

---

### Post by deBachin on 2012-05-16
Thanks guys.


 First I must tell you that I am try to clean up local Ubuntu folders and Windows network folders, being my file server.  
 

 The objective is to split the server client documents into folders A to F; G to M and N to Z. From an Ubuntu local machine. 



 Then collect the latest files from everywhere including the server.
 

 I must end up with all the latest files, neatly split into smaller groups. There are hundreds of folder.

---

### Post by deBachin on 2012-05-16
Ubuntu apps don't appear to treat Windows networks consistently unless I am doing something wrong. In any event the "Places" facility sometimes appears and sometimes not. The Ubuntu &#8220;Home Browser&#8221; is a typical example. Dolphin has &#8220;places&#8221;. Ubuntu Home Browser doesn't? Version 12.04
 

 Unison doesn't seem to see the Smb windows network.  
 

 Midnight Commander doesn&#8217;t seem to see the network.
 

 FreeFileSyns is great for local folder comparisons but its doesn&#8217;t see the network.  
 

 Krusader sees the network but it moves folders to some unknown destination. I see a folder disappearing on the left pane and its gone even after refresh (reload). I hope I will find them somewhere but right now they are gone! I am a but nervous about that at the moment.
 

 I probably don't know enough about Samba but I am not winning.

---

### Post by sudodus on 2012-05-16
I suggest that you mount your partitions separately before using programs like Unison or Midnight Commander. You can either do that with the Ubuntu file browser, Nautilus, or with terminal commands or scripts.

There is a special file, /etc/fstab, where you can add instructions to mount your drives, particularly if you want to mount them always, or always in the same way.

---

### Post by LewisTM on 2012-05-16
What Krusader does to your folders is weird and deserves its own thread with lots more information.

You definitely need to mount your Samba shares somewhere before using most Linux sync programs, which are not Windows-aware.
A shortcut would be to use Nautilus or Gigolo to first access your share, then point other software (e.g. mc) to the ~/.gvfs folder which contains all shares as mounted subfolders. You can create a symlink to .gvfs for easy access, for example
```
ln -s ~/.gvfs ~/shares
```

I'm not sure what would be the best strategy to consolidate all your files as you describe, syncing might not be the final answer. Will get back if something comes to mind.

---

### Post by deBachin on 2012-05-17
> **LewisTM said:**
> What Krusader does to your folders is weird and deserves its own thread with lots more information.....

Thank you. That makes sense. I will set up as you suggest and get back to you at least on the recognition of shares for moment. 

I will give Krusader a miss right now. On boot up this morning my machine ran a Windows *Chkdsk and  *took 2 hours to check a 2nd 1Tb BU drive of mostly unfragmented files.

---

### Post by deBachin on 2012-05-17
> **sudodus said:**
> I suggest that you mount your partitions separately before using programs like Unison or Midnight Commander. You can either do that with the Ubuntu file browser, Nautilus, or with terminal commands or scripts.

There is a special file, /etc/fstab, where you can add instructions to mount your drives, particularly if you want to mount them always, or always in the same way.

Thanks I saw that on the forum. It looked like a lot of PT and I set it aside, perhaps to my detriment. I will look again.

---

### Post by deBachin on 2012-06-14
I installed a GeForce GTS 250 graphics card and it runs under Ubuntu 12.04 but gives me a distorted screen. The only option under Systems Settings > Display is "Laptop" and 1024 x 768 but I am running a desktop with a Samsung B2330 flat screen and not a laptop. It wont give me any other option.

I would like to have a resolution of 1600 or something and 4:3 doesn't work for this screen. Also the colour on graphics is not wroking properly. The card work on the dual boot Windows.

Also I would like to add my second screen being an LG but Ubuntu does not see the second screen. 

My Nivida driver is up to date. 

Any suggestions?

---

### Post by sudodus on 2012-06-15
> **deBachin said:**
> I installed a GeForce GTS 250 graphics card and it runs under Ubuntu 12.04 but gives me a distorted screen. The only option under Systems Settings > Display is "Laptop" and 1024 x 768 but I am running a desktop with a Samsung B2330 flat screen and not a laptop. It wont give me any other option.

I would like to have a resolution of 1600 or something and 4:3 doesn't work for this screen. Also the colour on graphics is not wroking properly. The card work on the dual boot Windows.

Also I would like to add my second screen being an LG but Ubuntu does not see the second screen. 

My Nivida driver is up to date. 

Any suggestions?

Are you using the built-in proprietary nvidia driver? Or have you installed a driver from Nvidia's own web pages? That might make a difference.

Also, to control the settings, I think you should use Nvidia's control program ***nvidia-settings***

---

