---
title: "Learning shell scripting a good idea?"
date: 2011-08-08
forum: General Help
---

### Post by tech291083 on 2011-08-08
Hi,

Is bash scripting or shell scripting fundamental to learning Linux? I am not much aware of the actual use and potential of the same. I thought that it is basically meant for system admin tasks. What can desktop/single pc users like myself gain from it? There must be some advantage to it. Thanks.

---

### Post by whatthefunk on 2011-08-08
Yes.  Yes.  Yes.

Although Linux GUIs are improving all the time, it is still necessary to do some things through the terminal.  I also find that I can do most things a lot faster in the terminal.  Plus, you can further customize your system.  And its fun!

---

### Post by Grenage on 2011-08-08
> **tech291083 said:**
> Hi,

Is bash scripting or shell scripting fundamental to learning Linux? I am not much aware of the actual use and potential of the same. I thought that it is basically meant for system admin tasks. What can desktop/single pc users like myself gain from it? There must be some advantage to it. Thanks.

Yes, they're useful, but no unless you're going to be using scripts enough to remember the info.  You could read up and create a decent script, but if you don't touch the terminal for 10 months, you'll have forgotten nearly all of it.  I write the odd script, and do what I can from the terminal; I don't do it because it's necessarily faster than the GUI (it usually is), but merely to stay familiar with it.

I'm regarding scripts as multi-line code that you'd usually save to a file, and not 1-2 line *for* loops where you're renaming files, et cetera.

---

### Post by tech291083 on 2011-08-08
> **Grenage said:**
> 

I write the odd script, and do what I can from the terminal; I don't do it because it's necessarily faster than the GUI (it usually is), but merely to stay familiar with it.

I went through a couple of beginner's tutorials on shell scripting online over the last weekend, but since I am totally new to it, I could not see the actual use and meaning of the same. Your anwser is really interesting to note. So what exactly you use shell scripting for a normal pc, I guess? If you do not mind please give me couple of example that can be useful on a daily basis. This hopefully will encourage me to look further into it, thanks

---

### Post by sanderd17 on 2011-08-08
I don't script a lot, but I use the CLI a lot. I use it to delete-copy-move-edit files, to mount filesystems, to install applications, to launch applications, and for certain apps that only work on the CLI (like R, or gpsBabel).

Commands I use a lot:
[LIST]
[*]ls
[*]mv
[*]cp
[*]rm
[*]mount
[*]umount
[*]apt-get
[*]grep
[*]less
[*]cat
[*]vim
[*]chmod
[*]chown
[/LIST]

It's just so easy that I don't have to search for the right button and that I don't have to mess with a lot of windows. BTW, if you read this here: [http://linuxcommand.org/](http://linuxcommand.org/), then you have enough basic knowledge and you only need to search more if you want to.

---

### Post by mendhak on 2011-08-08
> **tech291083 said:**
> Hi,

Is bash scripting or shell scripting fundamental to learning Linux? I am not much aware of the actual use and potential of the same. I thought that it is basically meant for system admin tasks. What can desktop/single pc users like myself gain from it? There must be some advantage to it. Thanks.
As a newbie, some of the things I've found it useful for are

1 - Check if my external USB drive is plugged in and if it is, begin an rsync backup of specified folders

2 - Try and mount a windows share from another computer so that I can share files between the two computers.  

3 - Same as #2, but mounting the home directory of another Ubuntu computer

4 - Sometimes, I need to change permissions on folders/files to get different applications to work

You can see it's mostly around file sharing.  I'm sure your uses aren't the same as mine, but a lot of what you do will drive the types of scripts you write.  

I initially followed [this]("https://help.ubuntu.com/community/Beginners/BashScripting") tutorial.  Give it a go, just try a few simple things for the sake of trying them.  Once you know what you *can* do, ideals will pop into your head and you can start pursuing them.  

I've also seen that when you want to 'do' something and you search online for it, a lot of the answers are terminal commands instead of 'click here, then here' as the terminal commands are faster.

---

### Post by Grenage on 2011-08-08
> **tech291083 said:**
> I went through a couple of beginner's tutorials on shell scripting online over the last weekend, but since I am totally new to it, I could not see the actual use and meaning of the same. Your anwser is really interesting to note. So what exactly you use shell scripting for a normal pc, I guess? If you do not mind please give me couple of example that can be useful on a daily basis. This hopefully will encourage me to look further into it, thanks

Scripts themselves I don't normally use unless I'm at work; there have been a few home occasions, but not many!  The only two recent examples would be when I wrote a script for my media centre; it basically lists all files over a certain size, uploads the listing alphabetically to a webserver, then tells the media centre to update itself.  I also wrote a script that imports files when a particular esata drive is connected, with the file destinations being dependant on their original directory.

An example of (probably inefficient) basic commands I might use at home would be:

for f in *;
do mv "$f" $(echo "$f" | sed 's/random\([0-9][0-9]\)/newname\1\.mkv')"
done

Which will basically rename any files in the directory when the match sed's criteria.  If you have a directory full of photographs or a TV series - little snippits like this can save you a *lot* of time.

sed, awk, grep, et cetera, are the 'bread and butter' tools that you may find very useful; there's a lot of crossover with these apps, so ultimately there are several ways to do the same thing.

---

### Post by raja.genupula on 2011-08-08
for skill , knowledge , to know about about your system shell scripting  is the best thing . if you wanna play with your system there is no best joystick than scripting

---

### Post by tech291083 on 2011-08-08
> **mendhak said:**
> A
I initially followed [this]("https://help.ubuntu.com/community/Beginners/BashScripting") tutorial.  Give it a go, just try a few simple things for the sake of trying them.  Once you know what you *can* do, ideals will pop into your head and you can start pursuing them.  


Thanks a lot, I will try this tutorial...

---

