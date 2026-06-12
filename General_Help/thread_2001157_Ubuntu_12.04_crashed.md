---
title: "Ubuntu 12.04 crashed"
date: 2012-06-10
forum: General Help
---

### Post by davidzaq11 on 2012-06-10
I had a problem with my movies not playing smoothly in Ubuntu.
The sound and picture was fine but the movie would kind of stick or hesitate for a moment and then catch up to the sound.  
I was looking for something I could download or add to the terminal to make it run smoother.  I tried to follow a terminal command listed on Google by some one called Ubuntu and when I put in the command in the terminal, first it said no command found, then I typed in something else and got no software found.
Since then the software center won't open and the synaptic package manager won't open and I keep getting a box opening on the middle of the screen that says: SYSTEM PROGRAM PROBLEM DETECTED- DO YOU WANT TO REPORT IT.
But when I try to report it, I get a message:  UBUNTU SYSTEM AN INCOUNTERED AN INTERNAL ERROR,
I also have a red circle with a white line through it at the top of the page which when I click on the message says: 

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:
'E:Malformed line 68 in source list/etc/apt/sources.list(dist parse)'

That serves me right for believing everyone on the internet and trying to down load something I should not have.

Does anyone know how to fix this.  I have tried a few suggestions I read on Google like apt-get update -f and a few others but cannot seem to find a way to fix it. The terminal seems to open fine it is just the package center and synaptic package manager I am having problems with.

Does anyone have an Idea of what is going on here and how to fix it?
Thanks.

---

### Post by hottarod on 2012-06-10
I will start by saying I am not an expert in Ubuntu but I poke around the system from time to time.  This all has to do with Debian.  Sources are repositories where the software update manager or the apt-get command look to find what you are trying to install.  I believe Synaptic went the way of the dinosaurs back in 11.10.

If you are brave you can edit sources.list and see what is wrong there.  Mine only has 59 lines in it so there are some added repositories in yours for some reason.

Here are the last 6 lines of mine ending with #59;

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security multiverse

Its just a bunch of deb commands for where to go find software.  Whatever you tried from your Google search sounds like it put a deb in there with an invalid command structure or the address doesn't exist.  That is common as they do change things.  

Post your last several lines in sources.list so somebody on here that knows way more than me can look at it.  

Good luck.

---

### Post by sanderj on 2012-06-10
> **davidzaq11 said:**
> I had a problem with my movies not playing smoothly in Ubuntu.


What kind of hardware are you using: CPU and RAM ... ?

---

### Post by deadflowr on 2012-06-10
You can about several ways to try and fix this. 
First off open a terminal and run
```
sudo gedit /etc/apt/sources.list
```
Copy the contents.
In the forums "new" reply section, click on the #, which is for code.
Paste your copied content inbetween to two [code][code](/symbol omitted)
This will help us in the forums understand what's going on in line 68.

Another thing that I do whenever I mess up my source.list is change it in the update-manager.
Open the update-manager and in the left-bottom corner click on settings.
Move into the "other software" tab and uncheck absolutely everything.(The first one will prompt you for your password, but that's it.)
After unchecking all the checked repos in other software, close(not revert) and then click check in the update-manager.(this runs an update.
From there we can begin to fix any bad video problems, or at least try.

---

