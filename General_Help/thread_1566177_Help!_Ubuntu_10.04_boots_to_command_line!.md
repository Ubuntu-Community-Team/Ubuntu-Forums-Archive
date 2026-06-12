---
title: "Help! Ubuntu 10.04 boots to command line!"
date: 2010-09-02
forum: General Help
---

### Post by Ranger_Joe on 2010-09-02
Hey everyone, let me just get one thing out of the way right off the bat. I'm a TOTAL newbie. At this point, I am nothing more than a Linux wannabe. So, I'm going to need explicit detail in any instructions you give me. Sorry, but I'd really appreciate your help.

Ok, I installed Ubuntu 10.04 via CD and am currently dual booting it with Windows 7. I have a Sony Vaio VPCEA laptop if that matters. After installing Ubuntu, I'm not seeing the GUI when it boots. It will ONLY go to the command line. Worst of all, it's not responding to the "startx" command. That was working last night... not now.

Anyway, ALL I WANT is the see the GUI on startup. I want to see the splash screen, then the GUI. Very simple.

Can anyone tell me how to do this? THANKS! :p

---

### Post by woodmaster on 2010-09-02
try ```
sudo restart gdm
```

---

### Post by Ranger_Joe on 2010-09-02
Will that fix it forever? I want it to boot to the GUI every time.

---

### Post by hakermania on 2010-09-02
try adding the command woodmaster gave you at the startup....

---

### Post by Ranger_Joe on 2010-09-02
Just type "woodmaster"? What  will that do?

---

### Post by Autodidact on 2010-09-02
Open terminal (Applications menu -> Accessories -> Terminal). Run:
```
sudo gedit -w /etc/rc.local
```

Paste this line at the bottom of the file that opened and save:
```
sudo service gdm start
```

Now this command will be executed at startup.

P.S.
woodmaster is just the forum-member who replied to your question

---

### Post by Ranger_Joe on 2010-09-02
Ok. I will try all of this tonight and let you know.

Sorry for my newbieness. You guys are awesome.

---

### Post by Ranger_Joe on 2010-09-03
Ok guys,
So... I would love to enter the codes Autodidact gave me. However, now I can't get past the command line.

I tried typing in "sudo startx" which was working last night. However, now it is not. I've also tried simply typing "startx". With both codes, my computer simply goes to a black screen and stays there... like it's THINKING about doing something but ultimately decides not to.

I ALSO tried running Autodidact's code straight from the command line, since I can't get past it. That didn't work either. It said it was unable to load display.

How do I solve this so that I can solve my actual problem? Any help you guys can give would be great! Thanks again!

---

### Post by Ranger_Joe on 2010-09-03
Ok, I finally got into the GUI. So scratch that.

Anyway, once in Lucid Lynx, I did exactly as Autodidact said. I went to the terminal and ran this EXACT code:

sudo gedit -w /etc/rc.local

Nothing happened. This looks like a file path. Am I supposed to change this based on my computer? to what?

I then typed in simply:

sudo gedit

It then opened the program gedit... looked a lot like notepad. Then I typed in this code:

sudo service gdm start

I tried to save it just like Autodidact said but I didn't know where to save it to. 

Clearly I am doing this all wrong. I realize how stupid these questions are and the agonizing detail you must go into is no doubt annoying. I get it. But you guys have been awesome so far and I would appreciate more help. Thanks!

---

### Post by lisati on 2010-09-03
> **Ranger_Joe said:**
> Ok guys,
So... I would love to enter the codes Autodidact gave me. 

On behalf of the grammar police: them aint "codes", them is "commands".

:D

And you *are* allowed to use stuff like [noparse]```
 and 
```[/noparse] to help us distinguish what you've typed in from the rest of your answer.

---

### Post by Ranger_Joe on 2010-09-03
Sorry... commands;)

---

### Post by Ranger_Joe on 2010-09-05
Anyone have any more on this?

---

### Post by Ranger_Joe on 2010-09-07
I'm hoping if I rephrase my question, someone will answer. I tried putting this command into the terminal:

```
 sudo gedit -w /etc/rc.local 
```

However, I typed it exactly as you see it. I'm thinking this is a file path that should be changed based on the user. Please tell me the EXACT command I need to put into the terminal and be explicitly detailed... I'm new. 

Thanks again. Sorry for all the trouble.

---

