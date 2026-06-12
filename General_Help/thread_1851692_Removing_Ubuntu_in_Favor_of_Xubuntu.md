---
title: "Removing Ubuntu in Favor of Xubuntu"
date: 2011-09-28
forum: General Help
---

### Post by DaimyoKirby on 2011-09-28
So I just recently (yesterday) installed Xubuntu alongside my old Ubuntu 11.04.  Now, I've realized that I really like Xubuntu a lot better, and I want to remove Ubuntu.
First of all, how do I go about removing Ubuntu?
Second of all, if I remove it, will it mess up my files or anything?
Lastly, when I remove it, will it also take away all the duplicate Gnome applications in my menu, leaving only the XFCE applications?
For example:
[IMG]http://i.imgur.com/Hx6WJl.jpg[/IMG]
Notice the multiple screenshot applications, the multiple notepads, etc.
Will unistalling Ubuntu remove these extras, while retaining all my personal files, settings, applications *I* installed, etc.?

---

### Post by MG&amp;TL on 2011-09-28
Ah. You didn't install Xubuntu, you installed the Xubuntu desktop package on top of ubuntu.

You can remove Unity and gnome, but the easier way (I feel) would be to get a Xubuntu .iso, backup your files, then install Xubuntu as per usual.

---

### Post by DaimyoKirby on 2011-09-28
Oh. Ok.

Is there a way to save my desktop settings, such as sidebar and panels?

---

### Post by MG&amp;TL on 2011-09-28
I find it irritating the 'waste' application whenever you install a new DE. Good luck!

---

### Post by Gatemaze on 2011-09-29
> **DaimyoKirby said:**
> Oh. Ok.

Is there a way to save my desktop settings, such as sidebar and panels?

These settings are typically saved in your home folder. If you don't touch your home then you should be ok...

---

### Post by rojaasensei on 2011-09-29
Have a look at this page:

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

it will remove gnome and unity, and some apps like libre office, and it will install abiword and gnumeric.  However, when complete you can delete, reinstall what you like.  I found that my files were left intact.

Hope this helps.  It worked for me.

---

### Post by DaimyoKirby on 2011-09-29
I actually ended up just installing Xubuntu - it was nice to have a clean start, and to actually be running Xubuntu (instead of just a wrapper) - but thanks anyway.

So I have another question, and I'll see if you guys can solve it before I make a new thread.
After installing Xubuntu alongside Ubuntu, and moving the files I wanted over to Xubuntu, I then went and removed the old Ubuntu partition using gParted. Even though I removed it, I still see a screen like this when I log on:[IMG]http://buzzcodington.files.wordpress.com/2011/04/grub.jpg[/IMG]
(Take into account that this is not exactly what is shown, just a similar example.)

Is there a way to stop that from showing, and have my computer boot right to Xubuntu?

---

### Post by hhh on 2011-09-30
To remove the old Ubuntu entries, try running this in a terminal...```
sudo update-grub
``` You don't want your computer to bypass the grub screen if you have a Windows partiton because then you wouldn't be able to boot into it. If you don't have one, you can set Grub_Timeout to 0 in /etc/default/grub, see this page...
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by MG&amp;TL on 2011-09-30
Anything ubuntu-ish shows up in GRUB as "ubuntu" , I'm afraid.

---

### Post by DaimyoKirby on 2011-10-03
Just so you know, I've made a thread about my GRUB issue [here]("http://ubuntuforums.org/showthread.php?t=1853784"), if anyone cares.

---

### Post by collisionystm on 2011-10-03
Or you could have used tasksel to remove ubuntu-desktop and choose xubuntu-desktop.

---

