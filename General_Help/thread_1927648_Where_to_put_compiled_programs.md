---
title: "Where to put compiled programs?"
date: 2012-02-18
forum: General Help
---

### Post by Adam's AI on 2012-02-18
Hi, simple question: where do I put compiled programs? I've looked at ([http://www.pathname.com/fhs/pub/fhs-2.3.html#BINESSENTIALUSERCOMMANDBINARIES](http://www.pathname.com/fhs/pub/fhs-2.3.html#BINESSENTIALUSERCOMMANDBINARIES)) and seen tutorials for downloading programs through the software center and using make, but I just downloaded blender ([http://www.blender.org/download/get-blender/](http://www.blender.org/download/get-blender/)), which comes with a folder fully-compiled and am not sure where in the filesystem I should place it.

---

### Post by josephmills on 2012-02-18
there are a couple of places that you can put things or even make a directory yourself. But most of the time (if the devs of the program are nice)  It will put things where they go(some of the time).  there is a directory called /usr/share/applications/ 
inside of here is your .desktop files. this is how the menu see the program. Ex sample say I go out there and I want to put the text editor sublime2 onto my system I go out and I download and extract and make or find depenceys then make or what ever the the software (sublime2 here )now works. But it is not in my menu. so I make a file called sublime2.desktop in side of this file I put```
[Desktop Entry]
Type=Application
Version=1.0
Name=Sublime 2
Comment=text editor
Icon=/usr/share/Sublime2/sublime_icon.png
TryExec=/usr/share/Sublime2/sublime_text
Exec=/usr/share/Sublime2/sublime_text
Terminal=false
Categories=GNOME;GTK;Utility;TextEditor;
Encoding=UTF-8

```  

I try to explain a little about this file. 

Type=Application

this tells us that it is a application 


Name=Sublime 2

this says here is the name 

if you want a icon for it you put the path here 

Icon=/usr/share/Sublime2/sublime_icon.png

this one is important this is how it knows where to go to launch the program or execute the path to the program 

Exec=/usr/share/Sublime2/sublime_text


which you can store you program in usr/share/<name of program>/<all there files> 



this tells it where to put it in the menu or the categories

Categories=GNOME;GTK;Utility;TextEditor;


Now scripts and binary are different all togeather. What I like to do for my scripts is make a dir under /home/$USER/ called bin
like so 
```

mkdir -p "$HOME/bin"
echo 'PATH="$HOME/bin:$PATH"' >> "$HOME/.bashrc"
exec bash

```
then I store my scripts there. ~/bin 
I hope that this helps in some sorta way.

---

### Post by Adam's AI on 2012-02-18
Thank you for the reply! That actually helps me quite a bit. I'm not sure if it applies directly to blender which I downloaded, but it that is definitely helping me with some of the other programs I'm struggling with.

With blender, it unzips to a folder (now just sitting in my downloads folder) that contains an executable, a bunch of text files, and 3 subfolders with data. I'm not sure if I should put it in /usr/applications as that folder seems to hold *.desktop files exclusively. What do you think?

(it's too bad the blender version in the software center is several versions old, or I'd use that... but at least this way I get to learn :P )

---

### Post by josephmills on 2012-02-18
> **Adam's AI said:**
> 

With blender, it unzips to a folder (now just sitting in my downloads folder) that contains an executable, a bunch of text files, and 3 subfolders with data. I'm not sure if I should put it in /usr/applications as that folder seems to hold *.desktop files exclusively. What do you think?



umm I am going to download and try this blender...   :) brb
I also found this will looking around 
[https://launchpad.net/~irie/+archive/blender](https://launchpad.net/~irie/+archive/blender)

---

### Post by josephmills on 2012-02-18
Blender is Sweet I just downloaded and installed made a .desktop file and all if you like to see it here you go 
**EDIT** It failed to upload did not like the codec so I am converting now then will upload again with a new link.

---

### Post by josephmills on 2012-02-18
finally that took forever but here is the video 
[http://www.youtube.com/watch?v=p_WCBw8aX6k&feature=youtu.be](http://www.youtube.com/watch?v=p_WCBw8aX6k&feature=youtu.be)

---

### Post by Adam's AI on 2012-02-18
> **josephmills said:**
> finally that took forever but here is the video 
[http://www.youtube.com/watch?v=p_WCBw8aX6k&feature=youtu.be](http://www.youtube.com/watch?v=p_WCBw8aX6k&feature=youtu.be)


Thank you very much for making the video!

Just to confirm:

As a general rule, it's a good idea to put downloaded software into the /usr/share/<applicationNameFolder> folder?

Do the makers of blender really expect us to make the .desktop files? Or is it an ubuntu-only feature and that's why they weren't included? (The read-me just says to run the program, which is why I was unsure where I should store it)

---

### Post by Khayyam on 2012-02-19
> **Adam's AI said:**
> As a general rule, it's a good idea to put downloaded software into the /usr/share/<applicationNameFolder> folder?

No, in fact the [File System Hierarchy](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure) defines '/usr/share' is used for "architecture-independent (shared) data". Infact, you should avoid using /usr for anything other than distribution installed software, /usr/local and /opt exist for this purpose.

The 'data' found in /usr/share are 'shared components', such as icons, docs, etc, and not 'applications'. The difference between the FSH and other methods of organising the filesystem is that components of an 'application' are spread over the filesystem under their respective categories, libraries in /lib /usr/lib, binaries in /bin /usr/bin .. etc, etc. For 'applications' which are stored under their own directory structure then /opt should be used.

I could explain why the FSH is organised this way but right now I'm just getting ready to go out, and so have to be brief in my response.
 
So, if the Blender you are installing is packaged in such a way that its intended to exist under its own directory structure it should go in /opt.

HTH ... khay

---

### Post by josephmills on 2012-02-19
> **Adam's AI said:**
> Thank you very much for making the video!

Just to confirm:

As a general rule, it's a good idea to put downloaded software into the /usr/share/<applicationNameFolder> folder?
 nope I am sure that you read the post above thou that was me trying to make the video faster + I have had troubled with opt in the past so I make a Dir causally. 

> 
Do the makers of blender really expect us to make the .desktop files? Or is it an ubuntu-only feature and that's why they weren't included? 
[/quote]


nope they want one person to make the .desktop file then make a .deb package out of it. So others dont have to deal with doing the same thing. as far as why they have not included. that is a great question. But I think that it has to do with. linux is what you make of it. you could make a .deb package then upload to launchpad. then everyone could get it but it looks like some one has from this post 
[code]I also found this will looking around 
https://launchpad.net/~irie/+archive/blender[/qoute]

I hope that this helps. Have a good one.

---

### Post by Khayyam on 2012-02-19
Joseph ...

Don't take this in the wrong way but your posts in this thread are utterly confused and unhelpful. As an experienced *nix user I'm practically at a loss to understand what you are presenting, why, and what kind of direction you are trying to give to the OP.

Added to that your use of english, spelling, mis-tagging, etc, make it almost impossible to filter out the message from the noise.

You have confused the OP's question with your digression into "/usr/share/applications", the purpose of ".desktop" files, and making .deb packages. How do these relate to the question of "where to put compiled programs"?

There is a simple answer, /opt, and though **you** "had troubled with opt" (sic) this is the FSH standard. Your troubles probably stem from you not understanding how the FSH, software, and environment variables, work.

So, the desire to help is commendable, but the lack of clear understanding of what you are presenting is not. Its "muddying the water".

If the OP has a problem we can try to deal with that problem, but we have to focus on the problem at hand and not the minutiae of how items show up in the menu, how developers might package software, etc, etc.

Anyhow, I've probably said enough. Again, please don't take this the wrong way, I too am trying to be helpful.

best ... khay

---

### Post by josephmills on 2012-02-21
**EDIT**
please if you think that I do not know something please by all means Teach. as far as my spelling and tags I should take more time.

---

