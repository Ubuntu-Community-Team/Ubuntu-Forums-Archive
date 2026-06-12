---
title: "Help mapping Windows My Documents folder to Ubuntu My Documents folders"
date: 2010-12-18
forum: General Help
---

### Post by sk4tec on 2010-12-18
I can access my windows my documents\music by mounting my windows drive and browsing to it. I can then play\watch my movies and pics in Ubuntu.

But what I *really* want to be able to do is re-map the Ubunbu docs folder like so:

Ubuntu Pics = Windows My Documents pics.
Ubuntu Videos = Windows My Documents Videos.

I'm not very unix savy so I've been using Ubuntu tweak Personal\Default Folder Locations setting and browsing to my Windows folders. But it doesn't work.

I have managed to make a desktop 'short cut' and that works but I'd rather set the system wide default document folders.

Can someone point out to me how I can achieve this?

---

### Post by veggen on 2010-12-18
Put this:
mount -o bind /path/to/Music ~/Music
at the end of /etc/rc.local

It will take effect on next restart. You can just execute it yourself once with sudo so it will work for the current session.

---

### Post by sk4tec on 2010-12-18
Thank you for the reply. 

I need a little more detail to implement this. I presume you mean to put the mount commands in a "boot.ini" type file. (Ubuntu tweak only lets me browse for folders).

---

### Post by veggen on 2010-12-19
I haven't really used Ubuntu Tweak, so I can't help much with that, but regarding my suggestion, this is exactly what you need to do:

* open terminal
* type "gksudo gedit /etc/rc.local" (yes, this is the "boot.ini" type file, you need privileges to edit it (hence gksudo) and it will probably only contain a comment and "exit 0")
* add "mount -o bind /path/to/Music ~/Music" (and all others you want mounted) just before "exit 0"
* save & exit
* [optional] since this will take effect on th next restart, you can also execute all commands manually with sudo, like "sudo mount -o bind /path/to/Music ~/Music" to have everything mounted during the current session as well

---

### Post by johnproyal on 2011-01-04
How do you make set it up so multiple folders are binded at the beginning?

I can set it each session using sudo /path/to/Music ~/Music, but every time I restart it erases what I've binded, and I have to do it again. I've got gksudo gedit /etc/rc.local open, and I know where to add it and which directories work, but it doesn't set them when I restart. I have the feeling its because they're not separated or maybe it's too many.

Thanks for the help, again.

---

### Post by Jixop on 2011-03-09
I found this solutions and it works perfectly!

[B]Changing Paths of Places Menu Items Whilst Retaining Default Icons
[http://www.rosslug.org.uk/node/26](http://www.rosslug.org.uk/node/26)[/B]

---

### Post by dkathrens77 on 2012-02-06
Even more detail requested!

I have a dual boot machine, and want to store all my documents on the NTFS partition to prevent duplications, save space and make switching from W$ (aka Windows) to Ubuntu less of a headache.

Of course, W$ has spaces in folder names, which linux doesn't like. I think I understand you can enclose such a folder name in quotes, e.g. "My Documents". Is this correct? W$ won't let me change the name to something linux would grok, like "My-Documents".

In the case of my W$ My Documents folder:

/path-to-desired-location? 

do I use 

/dev/sda?/Users/[ME]/"My Documents"?

or 

/media/NTFS-Documents/Users/[ME]/"My Documents"?

I've tried it the way I thought it should work, but both the statements in rc.local and the same statements sudo-ed from the terminal do nothing...not even throw an error.

Please advise--and be very specific! Don't assume I know anything.

---

### Post by WorMzy on 2012-02-06
Assuming you're talking about your fstab entry, neither.

Use \040 in place of a space instead.

e.g.

/media/NTFS-Documents/Users/[ME]/My\040Documents

---

### Post by nothingspecial on 2012-02-06
I would put some entries in /etc/fstab like this. For the ntfs partition

```
UUID=fe3c8388-d051-4900-8f5a-835133c72482 /media/Stuff ntfs-3g defaults,en_GB.utf8 0 0
```

You can find the uuid bt typing ```
sudo blkid
``` and your available locales by typing ```
locale -a
```

Then add entries for specific folders like this


```
/media/Stuff/path/to/Music/ /home/suzie/Music  none  bind
```

for example.

Spaces in folders are escaped in fstab with \040 so a folder named "folder with spaces" would be

folder\040with\040spaces

---

### Post by dkathrens77 on 2012-02-06
What's this? a THIRD way to implement? 

Veggen proposed one method, Jixop posted a link to a second method,
and nothingspecial proposes yet another.

And none of these methods are presented completely, in detail! 
I wonder if you linux-heads are just TRYING to confuse-a-noob...

Thanks WorzMy for a very succinct, useful and very atomic! piece of information.

---

### Post by Morbius1 on 2012-02-06
> **dkathrens77 said:**
> What's this? a THIRD way to implement? 

Veggen proposed one method, Jixop posted a link to a second method,
and nothingspecial proposes yet another.

And none of these methods are presented completely, in detail! 
I wonder if you linux-heads are just TRYING to confuse-a-noob...
While it's true that there are 2 diferrent methods to implement this ( rc.local vs fstab ), [COLOR=Blue]nothingspecial[/COLOR] has the only description from start to finish that will actually work as desired.

Adding a line in rc.local without having the ntfs partition mounted at boot will do absolutely nothing because there is nothing to "bind" to. So automount the ntfs partition at boot then use either the rc.local method or the fstab method.

*To be honest I prefer a 3rd method and that is to create an upstart job but that might just push you over the edge.*

---

### Post by nothingspecial on 2012-02-06
Ok, I'll do this step by step.

First, your Music, Pictures and Videos folder in Ubuntu have to be empty.

Here are some assumptions

1. You user name is bob on both systems.

2. As your location is listed as Denver your locale would be en_US.utf8

3. Please bear in mind that I do not use windows but I will assume the paths to your folders on the mounted windows partition would be

Users/bob/My\ Documents/My\ Music
Users/bob/My\ Documents/My\ Pictures
Users/bob/My\ Documents/My\ Videos

Ok. First unmount your Windows Partition using the gui.

Then open a terminal and back up your /etc/fstab file

```
sudo cp /etc/fstab /etc/fstab_bak
```

Now create a mountpoint for windows and own it

```
sudo mkdir /mnt/windows
sudo chown -R $USER:$USER /mnt/windows
```

Now type ```
sudo blkid
```

Look for a line like this that has TYPE="ntfs" at the end, this will be your windows partition.

```
/dev/sda2: UUID="5B7CA25109F18FB8" TYPE="ntfs"
```

Now open up fstab

```
sudo nano /etc/fstab
```

Put this at the end (changing my assumptions and the correct uuid)
```

UUID=fe3c8388-d051-4900-8f5a-835133c72482 /mnt/windows ntfs-3g defaults,en_US.utf8 0 0

/mnt/windows/Users/bob/My\040Documents/My\040Music /home/bob/Music  none  bind
/mnt/windows/Users/bob/My\040Documents/My\040Pictures /home/bob/Pictures  none  bind
/mnt/windows/Users/bob/My\040Documents/My\040Videos /home/bob/Videos  none  bind
```

Then test it by typing ```
sudo mount -a
```

If all your stuff appears in the correct folders then I have not made a mistake/typo :p

Bear in mind that your user now has full permissions to go to the /mnt/windows folder and delete critical system files rendering your windows system useless but as I don't use windows I don't know the best way to go about this.

Hope all is clear now :)

---

### Post by dkathrens77 on 2012-02-06
Thanks **nothingspecial**, for taking the time to walk me through this. 

I don't think I need to worry about having W$ system files deleted unintentionally or otherwise, because all my documents are on a separate partition from my W$ system.

And I'm the only user of this machine. If it gets screwed up, I have only myself to blame.

I get a little cranky every time I step into the "unknown zone", because it seems I am always forced to learn MUCH more than I thought I'd need to.

Two or more methods...I'm always telling people that's how W$ is...but linux? A truly amazing (e.g. lost in a maze) number of  options for everything--but the learning curve! 

I suppose it's good for me, annoying as it can be, to try and color outside the lines. Maybe one fine day I can ditch W$ altogether.

---

### Post by forrestcupp on 2012-02-06
And here is yet another way to do it. You could make a symlink to your Windows folders. I just did it, and it works.

Open up Nautilus, and navigate to your Windows folders. I'll use **My Pictures** as an example. In Nautilus, right-click on **My Pictures** and choose **Make Link**. It will show up as a link called **Link to My Pictures**. Right click on that link and choose **Cut**. Now go back to your "Home" directory in Nautilus and go to **Edit/Paste** to paste the link there. Assuming there are no files in your Ubuntu Pictures folder, right-click your Pictures folder and **Move to Trash**. Then right click your link to My Pictures, and rename it to Pictures.

Now your Ubuntu Pictures folder will be linked to your Windows My Pictures folder, and you won't even be able to tell it. You can do the same for your Documents, Downloads, Videos, or whatever you want. The symlink even has the default icons, so you can't really even tell that it's not the original folder.

---

### Post by Morbius1 on 2012-02-07
The only problem with a symlink is that Samba ( actually I believe it's a problem with NFS as well ) will not follow a symlink. If you don't use Samba to share folders then it doesn't matter. There are ways around the Samba impediment but it's considered a security risk. Bind doesn't have this problem.

---

### Post by Mosome on 2012-02-07
Maybe simply try an alias instead.

---

### Post by forrestcupp on 2012-02-07
> **Morbius1 said:**
> The only problem with a symlink is that Samba ( actually I believe it's a problem with NFS as well ) will not follow a symlink. If you don't use Samba to share folders then it doesn't matter. There are ways around the Samba impediment but it's considered a security risk. Bind doesn't have this problem.

Good to know. Thanks.

---

### Post by dkathrens77 on 2012-02-07
That's kind of what I have been doing. I have my /etc/fstab set up to automatically mount my NTFS Data partition (my W$ system is on its own partition, separate from the W$ OS partition).

I have **links** aka *aliases* in my ~/Documents folder to both my private and public file directories (located on the NTFS Data partition) . Of course in my Home folder are all the other default Ubuntu folders. 

I was thinking about mapping all of those default folders to their W$ counterparts, so that all my data files would be in one place, regardless of which OS I have booted.

While I'm not a rank linux noob, I know "just enough to be dangerous". It's still stressful to consider attempting the sort of radical changes described here--deleting the default Ubuntu folders and replacing them with "symlinks" or "shortcuts" or "aliases" or whatever. 

I've tried blindly following "all ya gotta do" advice before, and gotten stuck 90% of the way through, with no strategy for getting back to where I started. I've had to fall back and punt--hoping I could copy all my files to an external drive and then re-install Ubuntu (losing all the applications, and hard-won customizations accumulated up to that point). That's never fun.

For instance, I haven't yet discovered a rule of thumb for manually installing applications in Ubuntu. Synaptic Package Manager does a super job of installing stuff in the repositories, but I have other apps, like the Arduino IDE, Firestorm Viewer for Second Life, etc. that I've downloaded, unpacked, and placed in the Ubuntu ~/Public folder.

I placed them there so they wouldn't clog up my ~/Home folder, or my ~/Downloads folder. 

I still haven't any idea of where these non-repository apps **should** be installed. They seem to run happily from ~/Public. 

If I remap my NTFS "Shared Documents" folder to ~/Public, I'd have to either move these rogue apps to that new location (and hope they run) or undertake another steep learning curve to find out how to move them so some preferable location on the Ubuntu partition (and hope they still run).    


> **forrestcupp said:**
> And here is yet another way to do it. You could make a symlink to your Windows folders. I just did it, and it works.

Open up Nautilus, and navigate to your Windows folders. I'll use **My Pictures** as an example. In Nautilus, right-click on **My Pictures** and choose **Make Link**. It will show up as a link called **Link to My Pictures**. Right click on that link and choose **Cut**. Now go back to your "Home" directory in Nautilus and go to **Edit/Paste** to paste the link there. Assuming there are no files in your Ubuntu Pictures folder, right-click your Pictures folder and **Move to Trash**. Then right click your link to My Pictures, and rename it to Pictures.

Now your Ubuntu Pictures folder will be linked to your Windows My Pictures folder, and you won't even be able to tell it. You can do the same for your Documents, Downloads, Videos, or whatever you want. The symlink even has the default icons, so you can't really even tell that it's not the original folder.

---

### Post by forrestcupp on 2012-02-07
> **dkathrens77 said:**
> 
For instance, I haven't yet discovered a rule of thumb for manually installing applications in Ubuntu. Synaptic Package Manager does a super job of installing stuff in the repositories, but I have other apps, like the Arduino IDE, Firestorm Viewer for Second Life, etc. that I've downloaded, unpacked, and placed in the Ubuntu ~/Public folder.

I placed them there so they wouldn't clog up my ~/Home folder, or my ~/Downloads folder. 

I still haven't any idea of where these non-repository apps **should** be installed. They seem to run happily from ~/Public.
A lot of times, apps that can be installed to your /home directory are self contained. They have all of the dependencies they need included in their directory, and it doesn't matter where you install them. You can even take the program's directory and move it if you want. They only thing you would have to change would be if you created a launcher or menu item, you would have to change where it points to.

Installing a 3rd party .deb file is a different story, though. Those install to specific places in your file system.

---

### Post by Crimbo on 2013-01-04
To firstly automatically mount the Windows partition on each boot, read this...
[http://askubuntu.com/questions/123234/how-to-automount-my-windows-partition-at-boot/236222]("http://askubuntu.com/questions/123234/how-to-automount-my-windows-partition-at-boot/236222")

Then to map each Ubuntu home folder to each corresponding folder using this guide...
[http://askubuntu.com/questions/152326/how-do-i-share-my-files-from-windows-7-to-ubuntu/236324#236324]("http://askubuntu.com/questions/152326/how-do-i-share-my-files-from-windows-7-to-ubuntu/236324#236324")

Enjoy!

---

