---
title: "General question about how to sort problems in Ubuntu"
date: 2012-02-12
forum: General Help
---

### Post by robert13 on 2012-02-12
Hi Guys.
Sorry for very long thread.
I am first time on this forum (actually on any Ubuntu forum).
I have used Ubuntu since 10.04 and I was happy as regular user.
But sometimes came to point where I need to know more or I'd like to do something more advanced.
(By the way I do programming for PIC microcontrollers and design electronics hardware based on GSM).
I've installed again (fresh) Ubuntu 11.10 and have some problems. About 2 weeks fight with things
and actually I haven't done any task successfully in terminal.
Example. I want to have access to another internal disk, I did research and find solution:
change permissions to hard drive. I tried but found another problem: can not access to file (some file somewhere) permissions denied. Found solution for this - another problem occurred... 
Another example. I want to install extension for Gnome3.2.
Found. Try to install following suggestions (copy and paste to terminal). Problem - not have permissions for creating files in director usr/share/.../extensions/    Find solution "sudo". Another problem - directory omitted.
Find "cp -r". OK. Works but copied not folder with files inside but files only to .../extensions/
I do not know if this is ok (can't find) but I though that should be 
".../extensions/folder_name/file_for_extension.js"
I have checked Gnome Tweak Tool (Advanced Settings) but there is not any extension.
Etc etc.
I do not know what I am doing wrong but is not easy...
My question is where I can find some more references how to do things in Ubuntu especially in terminal - 
something like Ubuntu Pocket Guide by Keir Thomas but with more informations.
Not with informations about command in terminal but informations like:
- extensions for Gnome are there...
- how to change permission for file in file system
- how to change permissions for hard drive - I can read but can't write and delete files. Root is owner.

Sorry for this massive thread but I am frustrated now little bit. I fall in love with Ubuntu when I started use
it but now I stuck to nothing. I do not want to come back to my previous OS.
Please help.

Robert

---

### Post by dragonfly41 on 2012-02-12
As a relative newcomer myself .. I'm still using ubuntu 10.10 .. I can understand frustration in having to learn commands .. but it is the linux way of life. 

I have found **Double Commander** to be a useful GUI tool  for general file management, setting permissions etc.

[http://www.webupd8.org/2011/02/download-double-commander-046-deb-works.html](http://www.webupd8.org/2011/02/download-double-commander-046-deb-works.html)

```
sudo add-apt-repository ppa:alexx2000/doublecmd
sudo apt-get update

sudo apt-get install doublecmd-gtk
```Navigate to your files in Double Commander, right click and set attributes.

...

Also **[COLOR=Red]CLI[/COLOR] [COLOR=Red]Companion[/COLOR]** keeps a repository of terminal commands you learn to use.

[COLOR=Red][EDIT: corrected CLI Commander to read CLI Companion .. install via Synaptic Package Manager[/COLOR]


More links ..

[http://linuxcommand.org/](http://linuxcommand.org/)

[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)

---

### Post by Cookieh on 2012-02-12
Seeing as you're familiar with assembly language for PICs, think simpler. Bash is way easier and you will only need to learn about 20 commands in your Ubuntu's distros lifetime.
For extensions, try having a look at this :
[http://blog.fpmurphy.com/2011/04/gnome-3-shell-extensions.html](http://blog.fpmurphy.com/2011/04/gnome-3-shell-extensions.html)

---

### Post by Ms. Daisy on 2012-02-12
You may want to look at this sticky regarding learning Linux commands:

[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)

---

### Post by robert13 on 2012-02-12
Thanks a lot guys.

These information are useful for problems I have explained.
But there is lot other problems. Maybe you've got suggestions how to develop my better knowledge
in Ubuntu. This is really general question.
Should I annoy with stupid questions people on forum if I can't find answer on Google and not on this forum.
I think they are stupid - probably they are ridiculously simple to sort out.

Thanks
Robert

---

