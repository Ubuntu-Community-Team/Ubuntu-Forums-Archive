---
title: "So i installed ubuntu12.4 LTS........"
date: 2012-10-11
forum: General Help
---

### Post by CCgirl6690 on 2012-10-11
Hello everyone 
iv got rid of backtrack 5 and installed ubuntu 12.4  but it is to slow compared to backtrack 5 and  doesnt look like what i have seen before and there's an annoying luncher on the left side and i dont see any applications ,system ,places  like iv seen on backtrack before  ,......................
so my question is are there anyways to change the theme to make it look like ubuntu 10 or 11 which is used on backtrack  where there is a bar upside with applications  , system and... buttons and each application has its things in it not in the upper bas like mac os . and if not where can i download one older ubuntu version ?  in download page it only offers 12.4 
thank you so much

---

### Post by AndyOpie150 on 2012-10-11
You can look at this: [http://www.techdrivein.com/2012/06/25-things-i-did-after-installing-ubuntu.html](http://www.techdrivein.com/2012/06/25-things-i-did-after-installing-ubuntu.html)
or this: [http://www.unixmen.com/201204-top-things-to-do-after-installing-ubuntu-2/](http://www.unixmen.com/201204-top-things-to-do-after-installing-ubuntu-2/)
The last link having the best info for what you seek to do.
 
I can't remember which one I used but one of those links gave me the info that allowed me to install the Gnome classic, 2D, and KDE desktop enviroments.
Then when I booted into the distro all I had to do is click on the icon in the login box (upper right side). This gave me the choice to boot into Unity, Gnome classic, 2D, or the KDE. I could choose to do this at every boot up.
I think it was the last the last link.

---

### Post by 0011235813 on 2012-10-11
What you're noticing is the new Unity interface. You're probably used to the old Gnome 2-y style interface.

You could learn how to use Unity- it's a pretty decent interface in my opinion. See: [http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity) for information.

If you still don't like it and want to use the old interface, you should install MATE:
[http://ubuntuportal.com/2012/04/how-to-install-mate-desktop-in-ubuntu-12-04ubuntu-11-10.html](http://ubuntuportal.com/2012/04/how-to-install-mate-desktop-in-ubuntu-12-04ubuntu-11-10.html)
and follow the terminal instructions (you do know you can quickly open a terminal with Ctrl+Alt+T?).

---

### Post by clay7 on 2012-10-11
> or this: [http://www.unixmen.com/201204-top-things-to-do-after-installing-ubuntu-2/](http://www.unixmen.com/201204-top-things-to-do-after-installing-ubuntu-2/)
The last link having the best info for what you seek to do.

That's what I did. Specifically, 

```
sudo apt-get install gnome-panel
```

Then log out, and when you log back in, click on the Ubuntu logo next to where you enter your password and select Gnome Classic. Just be aware that some video card drivers need to be adjusted for Gnome Classic.

When Unity was introduced, I really, REALLY didn't like it and switched back to Gnome. However, Unity has grown on me and I use it on some desktops, but I still switch the minimize, maximize, and close buttons back to the right side. You can do this by entering this in Terminal:

```
gconftool -s /apps/metacity/general/button_layout -t string menu:minimize,maximize,close
```

Or, if you like the MS Windows style menu, you can install the Cinnamon desktop. It looks nice and I have it on some workstations. The link above has instructions for this.

---

### Post by CCgirl6690 on 2012-10-11
thank you 
one more  quick question while im at it .
when i wanted to install ubuntu 12 i deleted both  win7 and backtrack , i have 2 partitions c and d , i only deleted drive c , but now when im booting up ubuntu it still gives me a boot menu choose between win 7 and ubuntu while there is no win 7 on my computer anymore  . so i am goign to reinstall ubuntu  can i this time delete all partitions including system reserved and everything else except my drive d, i mean it wont damage my files on D? 
thak you

---

### Post by 0011235813 on 2012-10-11
> **CCgirl6690 said:**
> thank you 
one more  quick question while im at it .
when i wanted to install ubuntu 12 i deleted both  win7 and backtrack , i have 2 partitions c and d , i only deleted drive c , but now when im booting up ubuntu it still gives me a boot menu choose between win 7 and ubuntu while there is no win 7 on my computer anymore  . so i am goign to reinstall ubuntu  can i this time delete all partitions including system reserved and everything else except my drive d, i mean it wont damage my files on D? 
thak you
Should not damage D: or whatever the partition is in Linux (/dev/sdba2 most likely).

I would still backup all your files on to an external drive just for good measure though.

PS: Next time, try and use Libreoffice Writer to write your comments in, that way you can easily proofread your posts and they'll be easier for us to understand.

---

### Post by CCgirl6690 on 2012-10-11
thank you 001123 . 
i just ran the command and installed  gnome classic it feels much better  .  about liberoffice  i dont know what that is but i will look it up . thanks for teh hint 
my D drive is to big i can not back up  . but i have 20gb unallocated space i dont know how it happend 
but thank you

---

### Post by AndyOpie150 on 2012-10-11
Ubuntu 12.04 install should allow you to wipe the whole disk before install.

---

### Post by 0011235813 on 2012-10-11
> **AndyOpie150 said:**
> Ubuntu 12.04 install should allow you to wipe the whole disk before install.
Uhm... Don't select the "Erase Disk and Install Ubuntu" option. That will delete everything on the computer, including the OP's partition containing the personal files. 

OP, you're better off using the "something else" option in the menu. That will allow you to just install Ubuntu on /dev/sdba1 and ignore your secondary partition containing the data.
Also, you can buy an external drive and backup the files, either manually or with an automated tool like the deja dup bundled in Ubuntu.
I think the 500GB ones can be brought for around £60-£70 in the UK.

---

