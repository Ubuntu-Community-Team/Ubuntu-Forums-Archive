---
title: "Hard to solve ipod problem in ubuntu 9.1!"
date: 2009-11-30
forum: General Help
---

### Post by masksalesman on 2009-11-30
Hello there! i'm having a problem that i didnt find any one who had it too in any forums, including this one. The problem is that, when i plug in my ipod nano, ubuntu recognizes him and opens an nautilus window of the ipod. Ok. But when i try to use any programs to manage my ipod, the programs cant find the ipod. They doesnt show any ipod icon, if i try hitting "load ipods" in gtkpod for exemple, nothing happens! i've already tryed gtkpod, songbird, amarok and rhythmbox... none of them even recognized the plugged ipod! please help me, cuz i cant find answers to this problem anywhere!!

---

### Post by masksalesman on 2009-11-30
no one can help? (once more...)

---

### Post by Sicadastra on 2009-11-30
Hi,

I'm no big techie person but maybe you can try rebooting your PC? I also use an iPod with Ubuntu but so far I have yet to have that kind of problem. Maybe you can also add the disk mounter on the panel and see if it can be detected from there.

Good luck :)

---

### Post by masksalesman on 2009-11-30
Sicadastra, i didnt actually got what you meant with "mount from the panel", but anyways, your ipod detection turns to work when you reboot? because it doesnt work in my case! actually i was using opensuse 11.2 and, as long as i couldnt make ipod work, i came back to ubuntu. The strange part of it is that he was working ok with my old ubuntu (8.1 i guess). But not with this new one... but i'm "happy' to know that i'm not the only unlucky one with this problem...lol. If you could explain with more details to me how you made it work i'd appreciate!

---

### Post by ooolongT on 2009-11-30
Mask, I am having a similar problem, and I too am getting no help.  If you want to watch my thread 

[http://ubuntuforums.org/showthread.php?p=8408065#post8408065](http://ubuntuforums.org/showthread.php?p=8408065#post8408065)

You can but I will let you know if I get any help.  I think this is not an uncommon problem, but I can not find a solution to my particular problem in any of the threads I have found.

Good luck to you!

---

### Post by chrisinspace on 2009-11-30
I have never owned an iPod, but I'm a big fan of Songbird and I know they have support for most models other than the Touch or iPhone.

You might want to try installing [Songbird]("http://getsongbird.com/") and then the [iPod Device Support addon]("http://addons.songbirdnest.com/addon/12").

---

### Post by amsum on 2009-11-30
Here is the solution if you are using Amarok.
You will not see amarok detecting iPod in the first instance. Now click the Folder icon just below the Play, Pause,Stop icons. You will find 4 options there - Local Music, Internet, Playlist, Files.
Click the "Files" and you will see your iPod there. Click it. Now go back to Local Music and you have your iPod there.:)

---

### Post by ooolongT on 2009-11-30
Amsum, thanks for your response.  When I click "Files" nothing happens.  I think my problem may be more deeply rooted than that, the ipod does not seem to be mounting correctly.  I have added additional information to my earlier post.

---

### Post by amsum on 2009-11-30
Well, my nautilus doesn't recognize iPod and so too amarok.
When you click "Files", did you see iPod there?

If yes, then click the iPod and then go back to Local Music where you will see both iPod and your music in your local folders.

If NO, then the problem is somewhere else.

---

### Post by ooolongT on 2009-11-30
No nothing shows up when I click "files"

---

### Post by t0p on 2009-11-30
Sorry, slightly off-topic reply:

OP, there is no Ubuntu 9.1.  Version numbers consist of the year and the month in which the version was released.  Hardy was released in April 2008, so is Ubuntu 8.04.  The latest version (Karmic) came out in October 2009, so it's called 9.10.

---

### Post by OpSecShellshock on 2009-11-30
Following this post worked for me with an iPod classic:

[http://ubuntuforums.org/showthread.php?t=619615](http://ubuntuforums.org/showthread.php?t=619615)

Some of the trouble apparently has to do with how Apple has restructured the database in the firmware. Another thing you might want to do is check the permissions on the iPod and either change them or use sudo to run gtkpod (the riskier but less tedious option). Best of luck.

---

### Post by masksalesman on 2009-11-30
Yep, same here... amarok didnt work. I follow your steps, but the ipod is not there. Too strange... probably is really a deeper problem :( 
I'm thinking about creating an anonymous helping group for those who cant use the ipod with gnome anymore! lol thats really sad... any new tip is welcome! i'll be glad to try!

---

### Post by masksalesman on 2009-11-30
[OpSecShellshock]("http://ubuntuforums.org/member.php?u=946893"), i tryed the whole tutorial... things got more strange, cuz now the ipod icon appears on the amarok menu, but clicking doesnt take any effect....i didnt have any errors during the process!

---

### Post by masksalesman on 2009-11-30
GOOD NEWS! FOLLOW THE  __[OpSecShellshock]("http://ubuntuforums.org/member.php?u=946893") TUTORIAL!
i did that, but it didnt work with amarok. BUT, then i tryed again with RHYTHMBOX box and its working perfectly!!! finally fixed problem! i hope you all can make it work too now!! thanks alot!!

---

### Post by cosborn72 on 2009-12-01
I am having the same problem, which started with the upgrade to Ubuntu 9.10.  The ipod mounts normally, but gtkpod does not recognize it.

The problem seems to be with the interface of gtk and Hal.

Here is the reported bug.

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/450465](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/450465)

---

### Post by gmalac on 2009-12-05
I am not sure but could it be a problem of rights? I can see/open the ipod (Nano 8GB) on the desktop but no application sees it (Songbird, Banshee).
Amarok can see it but no way to sync or edit metadata.
Going to /media/ I see that permissions are drwx------ (700)
All the other media in the directory have permission 755
There is no way I can change neither owner nor permissions (as root)
Properties show the device is /dev/sdg1
But what to do from there?
Guy

---

