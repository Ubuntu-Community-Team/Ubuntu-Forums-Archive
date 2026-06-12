---
title: "How come I can't access root folder? and how to fix install screw up"
date: 2011-05-18
forum: General Help
---

### Post by Stayin100 on 2011-05-18
I am very new to linux, first off. But I am pretty experienced with android phones and just installed ubuntu on my lap top. I noticed when poking around the file's I can't access the folder labeled root, even though I am considered system admin. How do I gain SU?

Also while using the installer I didn't understand what the system size setting was for, so I left it at 17 gb and now realize that that is how big the partition of my hard drive utilized for ubuntu is. I'd like to change this to something in the neighborhood of 150gb, is there a simple way of doing this? And is there a way grab files I've saved in windows, such as word docs, spreadsheets and pdf's? Without booting into it and emailing them to myself or burning onto disk?

And lastly, forgive my windows terms, but is there some sort of 'control panel' where I can mess around and basically just browse through options and settings? 

And I kind of want to see how things look without unity, I thought I remembered seeing something about a setting to disable it and go back to a less polished user interface. 
Thanks in advance!

---

### Post by TeoBigusGeekus on 2011-05-18
1) You can't become root in ubuntu - the root account is disabled by default.
To gain root priviledges, you can either use sudo (for terminal apps) or gksu (for gui apps).

2) Boot up with a live cd, fire up gparted (gnome partition editor) with
```
gksu gparted
```
and do your thing. Just remember that in order to operate on any partition, the latter has to be unmounted.
If the live cd(usb) doesn't have gparted, you can install it with 
```
sudo apt-get install gparted.
```

3) To reach your windows partitions, go to the places menu (click on Desktop and then go to top panel).

4) The top right menu on your panel, the one with which you log off, restart, etc., has System Settings as its last choice.

5) When you login, you can change the Session option from Unity to Ubuntu Classic in order to log in with gnome 2 instead of unity.

---

### Post by TeoBigusGeekus on 2011-05-18
> **mmanomano546@gmail.com said:**
> I sent in a 1040X did that screw up my stimulus check? Because my  accounting told me to (Of over 15 years).. A lot of people said they got  a check

Are you high?

---

### Post by coffeecat on 2011-05-18
> **TeoBigusGeekus said:**
> Are you high?

Probably high on too much canned luncheon meat. :) I've reported it and it'll probably be gone in a moment, thus confusing anyone else who reads this thread!

---

### Post by dandnsmith on 2011-05-18
Obviously gone, as I was totally confused until I reached the last posting.

---

### Post by oldfred on 2011-05-18
If you are a new user, you do not want to poke around in root too much. I managed to destroy one install that way before I knew enough to do it intentionally to learn how to fix things. But it is easy to reinstall if you do not have data to save or be sure to have good backups before poking around if you have data you want to save.

When you log in, after putting in username at the bottom of the screen is the option to use gnome instead of Unity. If remembers last choice for reboots.

If in gnome, most user settings are in System, Administration or System, Preferences. In unity those choice I think were under the logout icon on the right top.

If you are going to dual boot with windows, it is best to have a separate shared NTFS partition. Set Ubuntu to only read from the Windows system partition and read/write from the shared partition. Ubuntu shows all the hidden system files that windows hides and lets you accidentally modify windows files/folders. Also windows does not like too much writing into its system partition from other systems.

Another choice on expanding is to create a separate /home.

Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

System performance is slightly better if all system files are located in a smaller partition so drive heads do not have to search entire drive for files. Data then can be scattered as it is not accessed as often.

---

