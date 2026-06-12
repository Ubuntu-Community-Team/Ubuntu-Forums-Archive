---
title: "Root owned folders"
date: 2009-10-02
forum: General Help
---

### Post by [=Vion=] on 2009-10-02
I have Audacious and it turns out that it can use Winamp themes. Me being a Windows poweruser I have plenty of winamp themes. So I search for the folder that has the winamp themes and try to paste the themes I have but it turns out I cant because the folder is owned by root. I tried running as superuser by typing su in the terminal and inserting my password but even then it still says that the folder is only modified by root. How do I gain access to that and a few other folders that turn out I cant access? Thanx in advanced!!!

---

### Post by SuperSonic4 on 2009-10-02
It's easier to use sudo infront of any command you use when you want to be root

```
sudo cp -Rv /some_folder /usr/share/wallpaper
```

Root file manager: ```
gksu nautilus
```

See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more stuff on sudo and root. You **can** enable the root account but nobody may tell you here but google knows and that link tells you how

---

### Post by ram2500 on 2009-10-02
Whenever I need to add or delete files owned by root, I just simply type:

sudo chown -R [username} {path to folder}

The "-R" flag is for recursive, meaning that everything within that folder is now mine.

---

### Post by [=Vion=] on 2009-10-02
hmmm... I can log in as root by entering a short simple command. It says to do that as a last resort. Isnt there another way to gain access to root owned folders? I read the whole thing but Im not really understanding much of the other alternatives.. Sorry for my stupidity.

---

### Post by SuperSonic4 on 2009-10-02
> **ram2500 said:**
> Whenever I need to add or delete files owned by root, I just simply type:

sudo chown -R [username} {path to folder}

The "-R" flag is for recursive, meaning that everything within that folder is now mine.

I get the feeling that the OP only wants to copy and paste winamp skin files/folders to the general directory so I would not recommend chowning this folder (likely to be /usr/share/*something*)

Usually you can copy them to a folder which already belongs to user which means only the user gets the theme

---

### Post by [=Vion=] on 2009-10-02
> **ram2500 said:**
> Whenever I need to add or delete files owned by root, I just simply type:

sudo chown -R [username} {path to folder}

The "-R" flag is for recursive, meaning that everything within that folder is now mine.

Nevermind.... this looks easier. Ill try it out soon. Hope it works!

---

### Post by [=Vion=] on 2009-10-02
> **SuperSonic4 said:**
> I get the feeling that the OP only wants to copy and paste winamp skin files/folders to the general directory so I would not recommend chowning this folder (likely to be /usr/share/*something*)

Usually you can copy them to a folder which already belongs to user which means only the user gets the theme

Alright now Im lost........:confused:

---

### Post by SuperSonic4 on 2009-10-02
> **'[=Vion=] said:**
> hmmm... I can log in as root by entering a short simple command. It says to do that as a last resort. Isnt there another way to gain access to root owned folders? I read the whole thing but Im not really understanding much of the other alternatives.. Sorry for my stupidity.

The second command in post 2 tells you how to get a browser open as root.

> **'[=Vion=] said:**
> Alright now Im lost........:confused:

Do you have a link to the instructions? 

What I was trying to say is that it's not wise to chown system files to your user as root needs them to run. chowning it to you may result in a unbootable system

---

### Post by snotplop on 2009-10-02
> **'[=Vion=] said:**
> I have Audacious and it turns out that it can use Winamp themes. Me being a Windows poweruser I have plenty of winamp themes. So I search for the folder that has the winamp themes and try to paste the themes I have but it turns out I cant because the folder is owned by root. I tried running as superuser by typing su in the terminal and inserting my password but even then it still says that the folder is only modified by root. How do I gain access to that and a few other folders that turn out I cant access? Thanx in advanced!!!


Vion, where exactly are you trying to copy the files from and to?

---

### Post by ram2500 on 2009-10-02
I don't know about Winamp, but since I am often the only user of my computer, if I want to, for example, paste fonts into /usr/share/fonts, I simply chown it. Additionally, on the guest account, the fonts are there as well (even though I own the font folder), so it probably would be fine with the Winamp themes.

---

### Post by [=Vion=] on 2009-10-02
> **snotplop said:**
> Vion, where exactly are you trying to copy the files from and to?

The files are in my XP HDD but I can easily pass them to my Ubuntu desktop. I made a search of the name of the themes already available on ubuntu and it gave me a few results. The 1st one being usr\Audacious\Skins or usr\share\Audacious\skins I cant really remember right now...

---

### Post by SuperSonic4 on 2009-10-02
Audacious won't be a direct subdirectory in /usr.

If you get them to your ubuntu desktop (on the desktop) then copy and paste the following in a terminal: ```
sudo cp -Rv ~/Desktop/*Folder* /usr/share/audacious/skins
```

where *folder* is the name of the plugin folder

---

### Post by [=Vion=] on 2009-10-02
that´s assuming that the Audacious folder is in usr\share\audacious\skins. Ill have to do some googlin´ to see whare the themes are kept and then just change the path in the command accordingly right??

---

### Post by ram2500 on 2009-10-02
Try chowning it first. If it doesn't work for you the way you want it to (making it available for others) then just chown it back to root. Also, typing\your\pathname\like\this will get you nowhere, as that's Windows' hat. You have/to/type/pathnames/like/this/in/a/Unix/or/Linux/operating/system:)

---

### Post by snotplop on 2009-10-02
> **'[=Vion=] said:**
> that´s assuming that the Audacious folder is in usr\share\audacious\skins. Ill have to do some googlin´ to see whare the themes are kept and then just change the path in the command accordingly right??

This should help: [http://ubuntuforums.org/showthread.php?t=584782](http://ubuntuforums.org/showthread.php?t=584782)

---

### Post by SuperSonic4 on 2009-10-02
Yeah, but it's very unlikely to be anything else. You can use the ls command to be sure

```
ls /usr/share | grep audacious
```

```
ls /usr | grap audacious
```

I should be surprised if the second code gave an output.

Also ubuntu is caps sensitive: *Audacious* is not the same as *audacious*

---

### Post by [=Vion=] on 2009-10-02
> **snotplop said:**
> This should help: [http://ubuntuforums.org/showthread.php?t=584782](http://ubuntuforums.org/showthread.php?t=584782)

Nice.. This just solved my problem. Thnx

Oh and thnx to everyone else too. Guess I still hav alot to learn specially the whole \\ // thing. oh and case sensitive too? hmm...

---

### Post by SuperSonic4 on 2009-10-02
Yeah but there is tab completion. To check it type the first part of a word and hit the tab key :)

---

### Post by [=Vion=] on 2009-10-02
> **SuperSonic4 said:**
> Yeah but there is tab completion. To check it type the first part of a word and hit the tab key :)

Type where exactly? In the terminal?

---

### Post by SuperSonic4 on 2009-10-02
Yeah, it's not important for this task but it does save a lot of time

---

### Post by [=Vion=] on 2009-10-02
> **SuperSonic4 said:**
> Yeah, it's not important for this task but it does save a lot of time

Interesting...thnx The more I can learn the better :)

---

### Post by sisco311 on 2009-10-02
If it's a single user system (or you don't want to share the skins with others), 
then you can copy the skins in ~/.local/share/audacious/Skins.

.local is a hidden directory in your home directory.

You may have to press Ctrl+H in your file manager to list hidden files.

---

### Post by 37fleetwood on 2009-12-13
Hi, I know this post is a bit dated but I thought I'd help with windows refugees who are afraid of the terminal.
pcmanfm which is easily installable even in the new software center will allow you to open folders as root. it's in the "tools" menu. they should put this action in Nautilus, it would be helpful.
when you use this tool it simply asks for your password like installing anything does. once the window opens just drag and drop.
I use LXDE sometimes and it uses pcmanfm which is where I remember using it.
somehow this just seems easier and less likely to cause a problem with someone like me who doesn't know what he's doing.

I hope this is helpful to someone.

---

### Post by aysiu on 2009-12-13
> **37fleetwood said:**
> Hi, I know this post is a bit dated but I thought I'd help with windows refugees who are afraid of the terminal.
pcmanfm which is easily installable even in the new software center will allow you to open folders as root. it's in the "tools" menu. they should put this action in Nautilus, it would be helpful.
when you use this tool it simply asks for your password like installing anything does. once the window opens just drag and drop.
I use LXDE sometimes and it uses pcmanfm which is where I remember using it.
somehow this just seems easier and less likely to cause a problem with someone like me who doesn't know what he's doing.

I hope this is helpful to someone.
This is also available through Nautilus scripts or through a simple ```
gksudo nautilus
``` launcher or keyboard shortcut.

This thread is super-old.

---

