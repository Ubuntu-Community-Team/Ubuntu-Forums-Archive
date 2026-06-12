---
title: "How to download packages from Internet instead or CD?"
date: 2010-07-29
forum: General Help
---

### Post by siteregsam on 2010-07-29
Hi,

 I had installed Ubuntu Server. The user interface is textual. I need to install GUI(gnome). When i tried to install the package, the system looks for it from cd rom. Actually i need to fetch the packages from internet. 

If its a desktop edition of ubuntu then i can do so by removing mark "Installable from CD-ROM/DVD". 

[IMG]https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=ubuntusoftwarecd1.png[/IMG]

How to do the same using commands?
Thanks in advance....

---

### Post by linux18 on 2010-07-30
```
 cd /etc/apt; sudo sed -i '/cdrom:/d' ./sources.list && sudo apt-get update 
```and with that, I just realized how good I am at making shell commands. this will: change to your apt directory, open up your software text file, remove any line with an instance of "cdrom:" save the file, and  reload your packages from the internet.

---

### Post by siteregsam on 2010-07-30
Hi linux18, [COLOR=Black][]("http://ubuntuforums.org/member.php?u=1108811")[/COLOR]

i am really thankful for u....
Is there a way to revert back what i did with command

 [COLOR=Blue]*cd /etc/apt; sudo sed -i '/cdrom:/d' ./sources.list && sudo apt-get update *[/COLOR]

????
If u know a way in then u should know a way out, i hope...

---

### Post by linux18 on 2010-07-30
```
 cd /etc/apt; sudo mv ./sources.list ./sources.list.bak; sudo cp ./sources.list.save ./sources.list; cd ..; cd .. && echo DONE                 
```good thing there is a backup by default

I'm curious why you wanted to change it back?

---

