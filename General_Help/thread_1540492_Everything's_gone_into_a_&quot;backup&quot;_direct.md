---
title: "Everything's gone into a &quot;backup&quot; directory--how do I restore it?"
date: 2010-07-27
forum: General Help
---

### Post by InquisitiveErin on 2010-07-27
OK, so I was trying to install a program and apparently deleted just about everything on my computer. Almost no applications work, and seemingly none of my directories exist. However, when I open the terminal, it has me working in /home/erin.backup-2010-07-27 (when it's usually just /home/erin). And when I tell it to list the contents of this current backup location, it shows me all the files, directories, and programs I seem to have carelessly deleted. How do I put all that content back where it belongs?

---

### Post by robsoles on 2010-07-28
It is simultaneously believable and unbelievable that nobody has posted you the most likely fix to your problem yet.

Please open a terminal and type the following series of commands into it - I include some redundancy so that I can help you recover if the reason that people haven't tried to help comes true ;)

```
sudo -i
(type in your password sweetie)
mkdir /root/this-is-a-redundancy
cp -Rf ~/* /root/this-is-a-redundancy
mv -R * ~/
```The last command there may make you choose between 'y' or 'n' to commit certain 'moves' which I could have had it skip asking you by adding the 'f' to the '-' flag like the 'cp' command before it but using 'force' all the time isn't that brilliant - choose 'y' in every case but I want the output of that command posted back to this thread using copy&paste please, if you are not sure you'll be able to do that then please post back that fact before proceeding with my crap instructions.

All going well this should restore your 'happiness' but without examining your circumstances I am risking failure by posting what I have - I hate failing a great deal more than a lot of the people who have looked at your request for help and decided not to post!

---

### Post by robsoles on 2010-07-28
Please don't work from an emailed copy of my previous post! If you are getting emails I hope you read this one before proceeding - I erred just enough to be painful rather than dangerous in my previous post before editing it a minute later - read post from site rather than email please!!!

---

### Post by InquisitiveErin on 2010-07-28
Hey, thanks so much. I'm planning to try it, but I'm not sure that copying and pasting the output will work, as Firefox won't currently run on my computer (I'm posting on this thread via an iPhone). I'm tempted to try your instructions anyway, but I realize that getting all sudo-happy and trying things willy-nilly is how I screwed myself up in the first place, so I'll patiently await your green light. :)

Just to clarify, I'm to run those commands from the new "backup" directory and not my usual erin directory, right?

---

### Post by AlphaLexman on 2010-07-28
> **InquisitiveErin said:**
> Just to clarify, I'm to run those commands from the new "backup" directory and not my usual erin directory, right?
It will not make a difference what directory you are in, robsoles has safely made sure that all paths are absolute and not relative.

---

### Post by robsoles on 2010-07-28
> **InquisitiveErin said:**
> Hey, thanks so much. I'm planning to try it, but I'm not sure that copying and pasting the output will work, as Firefox won't currently run on my computer (I'm posting on this thread via an iPhone). I'm tempted to try your instructions anyway, but I realize that getting all sudo-happy and trying things willy-nilly is how I screwed myself up in the first place, so I'll patiently await your green light. :)

Just to clarify, I'm to run those commands from the new "backup" directory and not my usual erin directory, right?

the mv command needs to be ran from your 'new' backup directory - I relied on where you said your terminal opens and tried to give instructions based on that.

---

### Post by robsoles on 2010-07-28
thinking a little more about it, I sort of wish I had asked you to type
```
ls ~/[Tab]
```before executing the mv command - when you press [Tab] with that line in terminal it should change '~/' to '/home/erin' but may change to '/home/erin.backup/' making my mv command fall on it's backside - don't run mv if above code expands to '/home/erin.backup/' post back instead please!

---

### Post by AlphaLexman on 2010-07-28
> **robsoles said:**
> the mv command needs to be ran from your 'new' backup directory - I relied on where you said your terminal opens and tried to give instructions based on that.
Sorry, you are right, I did not catch that!

---

### Post by InquisitiveErin on 2010-07-28
OK, I created the directory '/root/this-is-a-redundancy', but when I tried to execute the cp command, I got the following output:

cp: cannot copy a directory, '/root/this-is-a-redundancy', into itself, '/root/this-is-a-redundancy/this-is-a-redundancy'

---

### Post by robsoles on 2010-07-28
My mistake! It's because of switching to root user like I have.

```
exit
exit
```
just type "exit[Enter]" till terminal closes to be sure.
re-open a terminal
```
sudo cp -Rf ~/* /root/this-is-a-redundancy
```
Please tell me what it does to you using this method (If it works out OK I am going to get you to pop the next command in without 'sudo' and get you to tell me what the output from terminal is again!)

Please consider trying the 'ls ~/[Tab]' test I asked for while having terminal open in your own name rather than after 'sudo -i' command.

---

### Post by InquisitiveErin on 2010-07-28
The cp command seems to have worked like a charm--no output except prompting me for my password. The 'ls ~/[tab]' changed to 'ls /home/erin'. However, when I went ahead with the mv command, the output was:

```
mv: invalid option -- 'R'
Try 'mv --help' for more information.
```

---

### Post by robsoles on 2010-07-28
Dunno what I was thinking -R means recursive and it is redundant with the mv command.

```
sudo mv * ~/
```

---

### Post by InquisitiveErin on 2010-07-28
Thanks so much, robsoles--your instructions worked great. All those files and things are back in /home/erin where they belong. Unfortunately, though, It seems my unintended deletions were just the tip of the iceberg. I still can't get to my desktop, and some very frustrating error messages pop up. I'm probably just going to back up any important files on a flash drive or something, make an Ubuntu CD, and use it to wipe everything out and start over. That seems easier than Googling around, messing with every individual error. Thanks again for all your help. :)

---

### Post by robsoles on 2010-07-28
Sorry it didn't make all the problems go away and it was a little muddled from the outset.

I am not against pursuing the new errors with you if you change your mind but often a nice fresh install (with all the files you can't stand losing/not easily downloaded again) is marvelous!

---

### Post by InquisitiveErin on 2010-07-28
I really do appreciate the offer, but a nice, fresh install sounds like much less of a headache for both of us. (Plus, it's fun--almost like having a new computer. :))

---

