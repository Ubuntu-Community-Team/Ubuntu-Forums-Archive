---
title: "Brief questions from a newbie."
date: 2009-07-02
forum: General Help
---

### Post by Esotericstyle on 2009-07-02
Just a few weeks ago, I decided that I had had enough of Windows, and installed the latest Ubuntu on my Dell. I've been pretty happy with the whole system thus far, but a few things have been escaping me, despite my efforts to find solutions on the forums.

1. Almost as soon as I had Ubuntu running, I downloaded some sound collections to customize it a bit. They were initially just in folders on my desktop. I went through the System > Preferences > Sound menu to change the default sounds to the ones I downloaded. It all worked great until I moved the folder. Now, no matter how many times I change them, all of the sounds keep reverting back to the default ones as soon as I close the window. Also, every time the log in screen loads, it plays the default "error" sound effect, as if something failed to load, but I don't get any notifications regarding this error once I log in.

2. It seems that almost everything I try to do requires that I do something in the terminal. I've been running DOS and Windows since Windows 3.X, so I like to think I know a bit about the inner workings of computers, but the terminal just seems like some complex foreign language to me. I think I'm finally grasping all of the "sudo" command line stuff, but I'm still kind of lost as far as actually *accomplishing* anything in it. The built in help doesn't really seem to explain anything, so does anyone have book or link reccomendations for helping me figure out how the terminal actually functions? I'd hate to have to post on the forum looking for a command line for every little thing.

3. When something is instructing me to access the terminal and navigate to a specific directory, how exactly do I accomplish this? I've sort of been led to believe that I can just slap in a run command somewhere and the terminal will find what I'm looking for and do it for me. For example, if I'm trying to move something from my desktop into say, the usr/share/sound or whatever folder, what is the best way of doing so? I've just been using the sudo nautilus command, but most of what I've been reading has led me to believe that this is not a good way of doing things.

---

### Post by akakingess on 2009-07-02
> 2. It seems that almost everything I try to do requires that I do something in the terminal. I've been running DOS and Windows since Windows 3.X, so I like to think I know a bit about the inner workings of computers, but the terminal just seems like some complex foreign language to me. I think I'm finally grasping all of the "sudo" command line stuff, but I'm still kind of lost as far as actually *accomplishing* anything in it. The built in help doesn't really seem to explain anything, so does anyone have book or link reccomendations for helping me figure out how the terminal actually functions? I'd hate to have to post on the forum looking for a command line for every little thing.I would recommend doing what I did, which was just going to the local library and checking out some books on Bash (scripting) or Shell commands, etc. Also, Unix books will go over a lot of the same commands and issues within the terminal. Then it's just a matter of playing around and trying stuff out. If you are not doing Sudo then you shouldn't be able too break anything to badly. 

> 3. When something is instructing me to access the terminal and navigate to a specific directory, how exactly do I accomplish this? I've sort of been led to believe that I can just slap in a run command somewhere and the terminal will find what I'm looking for and do it for me. For example, if I'm trying to move something from my desktop into say, the usr/share/sound or whatever folder, what is the best way of doing so? I've just been using the sudo nautilus command, but most of what I've been reading has led me to believe that this is not a good way of doing things.Same goes for this question, when you open a terminal you always start in the "home" directory which you can always return to by typing ```
cd ~
``` then you can use the good old "cd" command to "change directory" and if you are in the usr/share/sound directory you can simply use the command "mv" (move), for instance ```
mv filetomove directorytomoveitto
```Hope this helps a little...

Sorry, let me clarify, to change to a certain directory, for example you would type ```
cd usr/share/sound
```
then you could type "ls" and that will list everything in the current directory.  Also, some commands, like "firefox" will run firefox without having to change directories or anything, I believe because it is in the "bin" directory. I am not quite sure why it works like that, but thought I would let you know what I know. Hope you continue to enjoy your Ubuntu experience (I have only been using it for about 3 months and have already converted 2 of my 5 computers completely and am dual booting a 3rd, so I am hooked!!!!)

akakingess

---

### Post by internalkernel on 2009-07-02
Welcome... lol... So, firstly, I have no idea what's going on with the sound scheme - it's probably something relatively simple. I would take that and turn it into it's own forum posting and maybe you can get some more specific help. I can try to help with the other stuff though... 

> **Esotericstyle said:**
> 2. It seems that almost everything I try to do requires that I do something in the terminal. I've been running DOS and Windows since Windows 3.X, so I like to think I know a bit about the inner workings of computers, but the terminal just seems like some complex foreign language to me. I think I'm finally grasping all of the "sudo" command line stuff, but I'm still kind of lost as far as actually *accomplishing* anything in it. The built in help doesn't really seem to explain anything, so does anyone have book or link reccomendations for helping me figure out how the terminal actually functions? I'd hate to have to post on the forum looking for a command line for every little thing.

Forget what you know about DOS, it's really not going to be all that helpful. Keep to the basic concepts of the what DOS was though - another method of interacting with your system. Ready for some reading? 
[Command Line Intro]("http://www.physics.ubc.ca/mbelab/computer/linux-intro/html/index.html")
[More about the command line]("http://www.tuxfiles.org/linuxhelp/cli.html")

> **Esotericstyle said:**
> 3. When something is instructing me to access the terminal and navigate to a specific directory, how exactly do I accomplish this? I've sort of been led to believe that I can just slap in a run command somewhere and the terminal will find what I'm looking for and do it for me. For example, if I'm trying to move something from my desktop into say, the usr/share/sound or whatever folder, what is the best way of doing so? I've just been using the sudo nautilus command, but most of what I've been reading has led me to believe that this is not a good way of doing things.

Let me introduce you to your two favorite command line friends... it's "Tab-Complete" and "man". These two are totally indispensable... 

The first "tab-complete", when you are trying to navigate to a directory... the command is simply "cd" (change directory), 

so try this in a terminal: 
```
cd /usr/sh
``` hit tab and watch the magic... Now, sometimes you will have to hit tab twice. If there is more than one option available, hit tab twice and it will list available options. For instance... 
```
cd /usr/s
``` hit tab twice... 

The same works for commands, try typing just an "ip" on the command line and hit tab twice... let's say we're looking for that command to see the network connections. In windows it was ifconfig, in linux it's ipconfig - so if you start typing "ipc" and hit tab it should complete for you... 

Now the next trick, try:
```
man ipconfig
``` 

man stands for manual, and yes that is the instruction set on how to use that command... and hit "q" to exit :)

Between those two you should be able to stumble around, rather dangerously, on your system. Read up a bit first, and after awhile you'll get the hang of it. It can be really esoteric, so don't be to worried about having to find help someplace...

---

### Post by Esotericstyle on 2009-07-02
Thanks, both of you, that's a lot of helpful information. It seems that for the most part, I was just over-complicating things. I just found that "Ubuntu Pocket Guide" PDF on this forum, so I'm reading through that and those links, which will hopefully answer most of my questions in the future. Tab-complete is my new best friend! XD I figured there had to be some sort of help command, but didn't have a clue where to start. I'm also pleased that I don't have to worry about doing too much damage while I'm messing around. It seems for the most part that it just yells at me and undoes anything damaging I do anyway.

---

### Post by akakingess on 2009-07-02
> **Esotericstyle said:**
> Thanks, both of you, that's a lot of helpful information. It seems that for the most part, I was just over-complicating things. I just found that "Ubuntu Pocket Guide" PDF on this forum, so I'm reading through that and those links, which will hopefully answer most of my questions in the future. Tab-complete is my new best friend! XD I figured there had to be some sort of help command, but didn't have a clue where to start. I'm also pleased that I don't have to worry about doing too much damage while I'm messing around. It seems for the most part that it just yells at me and undoes anything damaging I do anyway.

Happy Ubuntuing!!! This forum is also a good resource and everyone on here is very friendly and helpful, I read it daily just to learn new stuff from some of the posts. Welcome by the way, sorry I didn't formally welcome you in the first place.

akakingess

---

