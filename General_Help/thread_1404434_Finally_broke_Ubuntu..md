---
title: "Finally broke Ubuntu."
date: 2010-02-11
forum: General Help
---

### Post by artisan on 2010-02-11
I did it. I finally broke it!

It took me a couple of years to finally lock up Linux.

I was working with a jpg. in Inkscape.

Inkscape ?dropped the picture at one point. When closing the file the preview did not appear.
Since then I am locked out of my desktop where I was working.

I cannot delete the file.
I just tried using nautilus to delete the file the file locked Nautils and the whole pc.

Please. Can someone suggest how to delete the file?
Thank you.

---

### Post by audiomick on 2010-02-11
Hallo.
at a guess: this sounds like the sort of behaviour that might come from a full hard drive. Is that possible?
Try emptying your trash for starters, and go to the system monitor in system> administration and have a look at your drive usage.

---

### Post by artisan on 2010-02-11
Luckily Firefox still works.
Not much else. 
Can't open trash.
And at the moment, no file manager is working.
Will reboot and try.
But, should have 200 GB of memory left.

---

### Post by ushills on 2010-02-11
drop into terminal and sudo rm filename.

---

### Post by artisan on 2010-02-11
Tried a reboot.
Nothing on the desktop opens.
Trash will not open.


Luckily firefox still works. So I can ask for help....
Disk usage analyser still works and says there is over 200 GB free

---

### Post by artisan on 2010-02-11
> **ushills said:**
> drop into terminal and sudo rm filename.


Desktop$ sudo rm LOGO ELLE.jpg
rm: cannot remove `LOGO': No such file or directory
rm: cannot remove `ELLE.jpg': No such file or directory

---

### Post by audiomick on 2010-02-11
> **artisan said:**
> ...But, should have 200 GB of memory left.
Just to be sure: Is the whole system in one partition, or is /home seperate?
I ask because I have had to deal with a system where /home still had plenty of space, but / was full and causing odd behaviour.

---

### Post by artisan on 2010-02-11
> **audiomick said:**
> Just to be sure: Is the whole system in one partition, or is /home seperate?
I ask because I have had to deal with a system where /home still had plenty of space, but / was full and causing odd behaviour.

All one partition...
:confused:

---

### Post by Xog on 2010-02-11
> **artisan said:**
> Desktop$ sudo rm LOGO ELLE.jpg
rm: cannot remove `LOGO': No such file or directory
rm: cannot remove `ELLE.jpg': No such file or directory

you need to path it correctly

```
sudo rm /folder/folder/file
```

---

### Post by raffaele181188 on 2010-02-11
Sort of gnome bugs... I'm experiencing them, too :( Usually logout/in resolves my problems, you should try launching nautilus from terminal.
Press Alt + F2, type "Terminal" in menu doesn't work, and launch "nautilus"
Try doing what you are used to, then go reading console log ;) (and post it)

---

### Post by artisan on 2010-02-11
> **Xog said:**
> you need to path it correctly

```
sudo rm /folder/folder/file
```

Thank you but...

I am not sure I understand. The relevant jpg is just on the Desktop. Not in any folder.So if I    sudo rm   from Desktop is that not correct?

---

### Post by raffaele181188 on 2010-02-11
Also, quote if filename contains space
```

$ sudo rm "path/to/FILE LOGO.jpg"

```

---

### Post by raffaele181188 on 2010-02-11
Desktop is a directory, too
/home/artisan/Desktop/yourfilename.jpg

---

### Post by audiomick on 2010-02-11
> **Xog said:**
> you need to path it correctly

```
sudo rm /folder/folder/file
```
and the name looks like it has a space in it, which will confuse the terminal. Put the name in inverted commas "like this", and make sure the lower case/upper case in the name is right.

---

### Post by artisan on 2010-02-11
> **raffaele181188 said:**
> Sort of gnome bugs... I'm experiencing them, too :( Usually logout/in resolves my problems, you should try launching nautilus from terminal.
Press Alt + F2, type "Terminal" in menu doesn't work, and launch "nautilus"
Try doing what you are used to, then go reading console log ;) (and post it)

If I did 
Press Alt + F2, type "Terminal" correctly ..
I get:
No such file or directory


Applications>Accesories>Termial Sudo Nautilus gets:
(nautilus:2794): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:2794): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2794): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2794): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

But does launch Nautilus.

Once I use Nautilus and go to Desktop no problems.
As soon as I touch the jpg. The whole pc locks.
I just had to reboot.

---

### Post by artisan on 2010-02-11
> **audiomick said:**
> and the name looks like it has a space in it, which will confuse the terminal. Put the name in inverted commas "like this", and make sure the lower case/upper case in the name is right.

Like so?

sharon@sharon-desktop:~$ sudo rm "LOGO ELLE".jpg
[sudo] password: 
rm: cannot remove `LOGO ELLE.jpg': No such file or directory

---

### Post by ElSlunko on 2010-02-11
Where is the file located?

---

### Post by artisan on 2010-02-11
On the Desktop.

---

### Post by audiomick on 2010-02-11
Hi.
Sorry, not quite sure. You could try that commas outside the extensioln "LOGO ELLE.jpg"
or leaving the extension off "LOGO ELLE"...

By the way, when you start nautilus with root privileges, you should use
```
gksu nautilus
``` which is a "sudo" variation for graphical applications. The errors you report on starting nautilus with root privileges are "normal" in as much as everyone seems to get them. I don't know exactly what they mean, but as you say, nautlius works.

---

### Post by raffaele181188 on 2010-02-11
Please, read more carefully :/
You could try this from terminal
```

$ rm -f "~/Desktop/LOGO ELLE.jpg"

```
but I'd **STRONGLY** suggest more patience...
Try using another filemanager..
```

sudo apt-get install pcmanfm

```
Then Application > System Tools > PCManFM, then experiment...

---

### Post by ElSlunko on 2010-02-11
> **artisan said:**
> On the Desktop.

In terminal you have to move to your Desktop like so :

```
cd Desktop
```

them do the rm "filename" with the quotation marks so

```
sudo rm "LOGO ELLE.jpg" 
```

make sure you have .jpg inside the quotation marks. I noticed you left it outside in your last post.

Alternatively you can be anywhere in terminal and type out the entire filepath to your file. In your case it would likely be :

```
sudo rm "/home/sharon/Desktop/LOGO ELLE.jpg"
```

---

### Post by ElSlunko on 2010-02-11
Bah too slow! The other posters mentioned it.

---

### Post by artisan on 2010-02-11
> **raffaele181188 said:**
> Please, read more carefully :/
You could try this from terminal
```

$ rm -f "~/Desktop/LOGO ELLE.jpg"

```
but I'd **STRONGLY** suggest more patience...
Try using another filemanager..
```

sudo apt-get install pcmanfm

```
Then Application > System Tools > PCManFM, then experiment...

$ rm -f "~/Desktop/LOGO ELLE.jpg"
Got nothing.
Curser just moved down a line.]

And patience I have. Time I have right now, and gratitude for the help.
:D

Will try PCManFM

---

### Post by artisan on 2010-02-11
OK my bad.

But..
rm: cannot remove `LOGO ELLE.jpg': No such file or directory

---

### Post by mprokolo on 2010-02-11
cd to desktop 
then write sudo rm -f L 
and then press the tab button

or give an ls ~/Desktop

---

### Post by artisan on 2010-02-11
OK PCManFM.

Gave me the option to delete the file.

Are you sure?
Yes.

File deleted.


Nope. Sorry file still there on Desktop.

---

### Post by raffaele181188 on 2010-02-11
You misunderstood me :) I suggested patience 'cause I didn't want you to remove your jpeg! I think you knew basic shell commands ;)
"rm" deletes a file, and as far as I know, it doesn't move it to Trash, so now your logo is not easily recoverable :(

---

### Post by artisan on 2010-02-11
> **mprokolo said:**
> cd to desktop 
then write sudo rm -f L 
and then press the tab button

or give an ls ~/Desktop

desktop:~$ sudo rm -f L 
.adobe/                       movie/
.bash_history                 .mozilla/
.bash_logout                  .mplayer/
.bashrc                       Music/
.bogofilter/                  .nautilus/
.cache/                       .navicat/
.camel_certs/                 .nvidia-settings-rc
.compiz/                      .openoffice.org/
.config/                      Pictures/
.dbus/                        .profile
Desktop/                      Public/
.devede                       .pulse/
Documents/                    .pulse-cookie
Downloads/                    .recently-used
.esd_auth                     .recently-used.xbel
.evolution/                   .recently-used.xbel.J13K6U
examples.desktop              .sane/
.filezilla/                   .Skype/
Firefox_wallpaper.png         .spumux/
.fontconfig/                  .ssh/
.gconf/                       .sudo_as_admin_successful
.gconfd/                      Templates/
.gegl-0.0/                    .themes/
.gimp-2.6/                    .thumbnails/

---

### Post by Xog on 2010-02-11
a neat little trick

type sudo rm (don't press enter yet)

then click and drag the file into the terminal

press enter

---

### Post by raffaele181188 on 2010-02-11
Please, post output of
```

ls -l ~/Desktop

```
if that list does NOT contain your file, maybe it's only a gnome desktop bug. You should be able to adjust it simply loggin out and then in.

---

### Post by MooPi on 2010-02-11
Just open terminal and type ```
ls
```Locate the offending file  ```
rm filename
```I'm only suggesting this because no one has mentioned that you may be misspelling the file name.

---

### Post by artisan on 2010-02-11
> **raffaele181188 said:**
> You misunderstood me :) I suggested patience 'cause I didn't want you to remove your jpeg! I think you knew basic shell commands ;)
"rm" deletes a file, and as far as I know, it doesn't move it to Trash, so now your logo is not easily recoverable :(

The jpg can go and ...

I am not worried about the logo. I can get another original from source.
The largest issue is that it has "taken over" the Desktop.

I am effectively locked out of the Desktop and most of the file manager system right now...

---

### Post by mprokolo on 2010-02-11
plz post 
ls ~/Desktop
first

---

### Post by artisan on 2010-02-11
> **mprokolo said:**
> plz post 
ls ~/Desktop
first

ads          index.html   menu.php~         orange          Where.html~
Documents    index.html~  new file~         Screenshot.png
drawing.svg  menu2.php~   new file (copy)~  tax2010.xls

---

### Post by raffaele181188 on 2010-02-11
It seems that your file is gone :D
If you see it on your Desktop, LogOut and then LogIn (you don't need to reboot)

---

### Post by artisan on 2010-02-11
That has got it.

Thank you to all those that helped. It seems that pcmanfm managed to delete the file. And then all that was required was a logout/login.

Thank you people for your time and help!

Next is how to mark the thread solved?  :D

---

### Post by raffaele181188 on 2010-02-11
Edit first post' ;)
Change title should do the trick

---

### Post by Xog on 2010-02-11
Also on the top right you can click Thread Tools (underneath the page navigation) and select SOLVED. =)

---

