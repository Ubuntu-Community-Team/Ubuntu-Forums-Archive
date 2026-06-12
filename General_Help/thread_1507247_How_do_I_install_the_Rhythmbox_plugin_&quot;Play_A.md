---
title: "How do I install the Rhythmbox plugin &quot;Play Album&quot;?"
date: 2010-06-11
forum: General Help
---

### Post by jrg3 on 2010-06-11
The plugin is located here: [https://launchpad.net/playalbum/]("https://launchpad.net/playalbum/")

Problem is, I see absolutely nothing to install. 

Any help?

---

### Post by claracc on 2010-06-11
You go to the url address: [https://launchpad.net/playalbum/](https://launchpad.net/playalbum/)
there, you click on i  View the branch content,  under Development focus, (in the left side, at the middle of the page), in the next page you click on playalbum.rb-plugin, in the next page you click on download file and voila!,  you can save the bin file.

Regards

---

### Post by jrg3 on 2010-06-11
Thanks, but I'm still having problems. I've downloaded playalbum.rb-plugin and __init__.py and placed them both in ~/.gnome2/rhythmbox/plugins/ 

I had to create directory. After it didn't work I did chmod 755 on the plugins dir. 

[I]Edit: Rather, I did a chmod 755 on the contents of the directory. E.g., ~/.gnome2/rhythmbox/plugins/*
[/I]
When I navigate to my plugins inside Rhythmbox I find the new plugin listed, as expected, but when I tick the box to activate it I get an error alert stating "Plugin Error: Unable to activate plugin Play Album".

Did I do something wrong, or is this plugin just broken?

---

### Post by claracc on 2010-06-11
Perhaps you also have to download the .bzrignore file, inside there are two files: deply.sh and help.py, try with them, I don't know if they can help.

Anycase, to install the playalbum plugin you have to write in a shell, in the directory you have the plugin ./playalbum.rg-plugin.bin, if it gives you an error you can try with sudo.

---

### Post by jrg3 on 2010-06-11
That worked, thanks!

---

### Post by charding on 2010-07-17
I'm not even sure how this plugin works anyways.

I've tried right-clicking on any album within rhythmbox and it gives me the same menu as if I didn't enable the plugin.

Am I missing something? I thought this plugin would add an entry in the right click menu to queue the album I was right-clicking on....

---

### Post by peterlldj on 2010-07-26
Hello guy
If you don't have downloaded and installed the three files (viewed on the site) in your plugins directory, the plugin will not work properly. You could access the hiden folder  /.gnome2 on your personal directory, and then on this folder find the rhythmbox folder. Into this folder, it have another folder called plugins. Into this other folder, you need create a new folder and name it playalbum, and then put the three files downloaded on  this new folder. Restart Rhythmbox, open the menu edit -> plugins and voilá - You will find the option playalbum with the descriptions about plugin.

---

