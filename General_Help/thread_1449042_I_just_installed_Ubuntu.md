---
title: "I just installed Ubuntu"
date: 2010-04-07
forum: General Help
---

### Post by Slacker G on 2010-04-07
I am very impressed with how far Linux has come. There are a couple of things that geekedly challenged  people like myself have with the system. 

  Mainly loading and updating  apps. I needed to install  vlc. But I have no lan nor do I  have a fast Internet connection. 

  I think it would be great to have a program where Ubuntu could load apps from a CD or DVD. It would be great to just tell it what you want and have it load the program from the DVD or CD. 

  I see DVD 's with Linux programs for sale on the Internet. I do not know if they will load the programs that I need without having an internet connection. 

  So far, I can not install even the first app that I need. vlc for Ubuntu. 

  Is there help anywhere out there for the average non Internet connected user? I want to stay with this type of OS. But I do need help.

---

### Post by BigSteve_G on 2010-04-07
I had a very similer problem when I started with Linux.
 
The way I found was to use APTonCD to create a CD or DVD with all your currently installed programs on then when it comes to installing them use the package manger, from the menus (cant remember which one as I'm on a work XP machine at the moment) select add CD, once thats done click on the 'origin' button (botton left) & select the programs you want from that CD - its worked very well for me.
 
- Just a suggestion (dont wanna get shot down in flames for saying it) but have you tried Linux Mint its based on Ubuntu but with extras (including APTonCD installed by default)

---

### Post by steveneddy on 2010-04-07
[LIST]
[*]Not knowing where you are from or where you live, you could go to an internet cafe or the local library and use their connection for updating and installation.


[*]You could also go to a friend's home and use their faster internet connection.


[*]Find local free Wifi somewhere in your community and use that connection for your needs.
[/LIST]

---

### Post by Slacker G on 2010-04-07
Steve,

  I am sure there are thousands of people like me who would use Ubuntu if they didn't require high speed internet access to obtain the apps they need. The developers shouldn't just leave us out in the cold. we are many.

  I will follow up on your suggestion and see how far I get. I will try to find the link to the 5 DVD set again. Then I can contact them to see what works in my case. 

  Other Steve, 

  That would be cool but I don't have a lan in the system... and it is a tower. However, I had an enjoyable visual of myself (in my mind)  walking into a library to use the high speed access with a monitor in my arms and a tower strapped to my back.

---

### Post by nothingspecial on 2010-04-07
Walk into the library with a memory stick and download packages from [[COLOR="Magenta"]here[/COLOR]]("http://packages.ubuntu.com/karmic/").

Each package you download will have dependencies, signified by a red circle. You must download them also (and any dependencies of the dependencies.

Take the stick back home and copy them all into your home directory, then
```

cd
sudo dpkg -i *.deb
```

---

### Post by BigSteve_G on 2010-04-08
"I am sure there are thousands of people like me who would use Ubuntu if they didn't require high speed internet access to obtain the apps they need. The developers shouldn't just leave us out in the cold. we are many."
 
I know what you mean as I only use a pre-pay mobile broadband so the speed isnt as good as fixed-line broad band & the more I download the more I have to payout for top ups (although with Linux apps I find the sizes are small so I can get a lot) - if getting a fixed line broadband line is an issue why not try a pre-pay broadband dongle? thats what I did & since Ubuntu 9.04 they are well supported.
 
But once you've downloaded the programs & use APTonCD will will never have to download them again & it can install them on other DEB based linux machines.
 
"I will try to find the link to the 5 DVD set again. Then I can contact them to see what works in my case." - Youve lost me with this bit to be honest - what 5 DVD set?

---

