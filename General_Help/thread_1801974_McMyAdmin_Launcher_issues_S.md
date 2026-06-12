---
title: "McMyAdmin Launcher issues :S"
date: 2011-07-11
forum: General Help
---

### Post by Nick_Carriere on 2011-07-11
I have recently decided to use ubuntu 10.04 for running my minecraft and its server. I use McMyAdmin and to run it I need to go to the the directory and run the start.sh file then click run in terminal. I have been trying to make it easier by making a desktop launcher and keeping the folder off of my desktop. Every time I try to make the launcher the terminal opens then closes. I have tried "sudo sh /home/nick/McMyAdmin-latest/start.sh" and "sh /home/nick/McMyAdmin-latest/start.sh" even dropping the sh on the start and trying both ways. Nothing. The file is executable. Can anyone help me with my issue. Thanks. :)

---

### Post by AgentZ86 on 2011-07-11
> **Nick_Carriere said:**
> I have recently decided to use ubuntu 10.04 for running my minecraft and its server. I use McMyAdmin and to run it I need to go to the the directory and run the start.sh file then click run in terminal. I have been trying to make it easier by making a desktop launcher and keeping the folder off of my desktop. Every time I try to make the launcher the terminal opens then closes. I have tried "sudo sh /home/nick/McMyAdmin-latest/start.sh" and "sh /home/nick/McMyAdmin-latest/start.sh" even dropping the sh on the start and trying both ways. Nothing. The file is executable. Can anyone help me with my issue. Thanks. :)

are you running this from the local machine or are your trying to ssh@machine and login to another machine on the network to run the shared file ? 

I'm not sure I completely understand how your trying to run the executable ? 

Please clarify

---

### Post by Nick_Carriere on 2011-07-11
> **AgentZ86 said:**
> are you running this from the local machine or are your trying to ssh@machine and login to another machine on the network to run the shared file ? 

I'm not sure I completely understand how your trying to run the executable ? 

Please clarify

I am running it locally. Its just a simple .sh file that tells it to start the server program.

---

### Post by AgentZ86 on 2011-07-12
Ok

I see so you can already go to your home folder and simply click the item and it works but you can't make a desktop launcher

Ok, just right click and create launcher, but then browse to that location and file you wish to use for that command. There is a browse button.

And from the pulldown select location and not any application and not application terminal.

You will noticed this sort of happens even if you wanted to make a launcher for lets say and .mp3 file it will not launch because technically it's not a launcher but a location

I'm not sure why exactly but just try to create your launcher that way.

Right click / create launcher / command browse / and select your file
Then make sure the pulldown menu is for location.
Give your icon a name and should work fine from there

Let me know if you get permission errors or something, but you should not get any now.

I suspect you were getting permission errors before if you selected application or application terminal.

Hope this helps

---

### Post by Nick_Carriere on 2011-07-12
It worked, the only issue is that I still need to click "Run in Terminal" but its not a big deal and it isn't like I have to open it often.

---

### Post by Nick_Carriere on 2011-07-12
NVM :(, it wants to install the server on my desktop now... Guess I just have to open it throught the start.sh file...

---

