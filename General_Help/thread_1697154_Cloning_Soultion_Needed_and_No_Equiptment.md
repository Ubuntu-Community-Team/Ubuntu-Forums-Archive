---
title: "Cloning Soultion Needed and No Equiptment"
date: 2011-02-28
forum: General Help
---

### Post by Jiberty Nickett on 2011-02-28
Hey everyone,

I am new to Linux, I mean Ubuntu less than a year and that it it.  I work in a building with about 65 computers using Windows XP, 7, and Ubuntu (my computer).  I presently update one machine and use a Symantic Ghost USB portable HDD to image that machines.  Then I image the rest, ONE AT A TIME!  

This takes forever as you may imagine.  I have no option of getting a server to make my life easier because of budget cuts and the usual whining about spending money.  I have seen that Ubuntu and FOG has a solution but I am really new, like I said, and lost on some of the finer parts of what I need to do.  SO to my question.

"I have Ubuntu 10.04 on a Dell Dimension 2400, best I got at the moment and plenty! of HDD space.  Where or what can I use as a guide to help set up this system to take an image from a PC and send it to the rest, etc..."  The building is on a network but I want the 65 PC's to talk to my extra computer, the 2400 "POS", and update the images in a batch when ready.

I've bitten off a BIG project, but I have time... and would rather use Linux to create a solution than begging my boss for more junk.

"Save me Obi-Tux, you my only hope."

---

### Post by Kirboosy on 2011-02-28
You could use Clonezilla to get the job done.


Or just create an image and setup a generic [PXE server]("https://help.ubuntu.com/community/PXEInstallMultiDistro") on your computer (granted it will work only if the clients computers can support it)

If you are still interested in FOG look [here]("http://www.fogproject.org/wiki/index.php?title=FOGUserGuide")

---

### Post by Jiberty Nickett on 2011-02-28
I have a counter-part in a different area who uses FOG and another who using Symantic Ghost.  To say the least they are not willing to share their time to help the low man on the poll out of a Jam.  I say they are .... Well you get the idea.  I will look into the other options you listed.  

Thanks, I'll take all the help I can get.

---

### Post by jsb102 on 2011-03-01
Fog is a really great free imaging/deployment tool.  The GUI is really good, but I wouldn't say it's intuitive.  I've installed it twice.  The first time was painful in that the install went great, but I mistakenly put a different password in MySQL at the wrong time.  I didn't recover from that so I started again from scratch.  It was at least 6 months ago when I installed it so I wouldn't be able to rattle of the instruction.  I would suggest first off going to the wiki page for the Fog Project and reading through the install.  [http://www.fogproject.org/wiki/index.php?title=FOGUserGuide](http://www.fogproject.org/wiki/index.php?title=FOGUserGuide)
Also, this YouTube video.
[http://www.youtube.com/watch?v=fvltHkAtW2A](http://www.youtube.com/watch?v=fvltHkAtW2A)
It shows the install for Ubuntu 8.10, but it worked fine for my Ubuntu 10.4 OS.

After you get it installed and get logged in to the main screen, check for updates.

All I can really say is be patient.  I have very limited experience in Linux so I think it took me longer than most to get it working, probably 3 days to get the install right and capture my first image.  Once it's working though, it is very powerful and fast at deploying images.  The PXE booting is very smooth.  Once you register a computer in your FOG set up, taking an image of it is simple, and even more simple is deploying the image.  Don't forget to Sysprep the computer you are taking the image from.  You will have to do this with the Windows Sysprep utility and something that I would really like to see is a Sysprep type of utility incorporated in to FOG.  The pain of the learning process was well worth the results.  I've worked with 4 other computer imaging solutions, and FOG is by far my favorite.

Hope that helps.

---

