---
title: "HELP I cannot boot into Ubuntu"
date: 2010-09-22
forum: General Help
---

### Post by chrisv on 2010-09-22
My Ubuntu was working perfectly fine until this morning. It is the latest release (10.04 I think) and it is the 64 bit version. This morning I go to my computer and see there are some updates waiting. I install the updates without paying much attention to them. I really do not remember what the updates were. 

Then Ubuntu asks me to restart so I restart. After restart I get the usual log in screen and I hear the drums. I put in my password, press enter and then the log in screen disappears and I expect to see my desktop. But that does not happen. Instead in a split second after disappearing, the log in screen reappears and I hear the drums again. 

At the beginning I thought that I simply forgot my password. But that is unlikely because I have been using the same password for 6 years now. But just in case I tried an incorrect password and I got a different behavior. If I put in an incorrect password, Ubuntu will simply say "authentication failed" and the log in screen will not disappear. When I put in the correct password, the log in screen disappears for a split second (as if my password is correct) but then instead of taking me to the desktop it takes me back to the log in screen and sounds the drums again. 

Any ideas?

---

### Post by bryanfblareunion on 2010-09-22
when your log in screen comes up and press ctrl+alt+F1. This will take you to the command prompt. see if you can login with this. If you can, then it may be something with the graphical side of things rather than a deeper problem. 

I'm not a super great command prompt user so i have no idea what to do after this but i'm sure you can fix it from here.

---

### Post by 3Miro on 2010-09-22
During boot time, do you get a list of options to boot into. If not, you can press and hold the shift key, it will open a menu for you. You should be able to open an older version of the kernel and try to log in with that.

My guess is that you have an application and/or theme that got broken by the updates and now the thing breaks when you try to restore the old session. There are logs that you can open and read to see what the problem is, but I am not sure which ones. I can only think of a rather dramatic solution:

1. Boot using a LiveCD and choose "try ubuntu".
2. Go to your harddrive, wherever the /home/ partition/folder is on your computer (not the one on the LiveCD).
3. Make a folder home/mybackup.
4. Open the home folder for home/your_username and then hit Ctr + H.
5. Cut and paste all files from home/your_username onto home/mybackup, then reboot into regular ubuntu and try to login again.

This method will reset all the settings on your system. All the old stuff is in home/mybackup so you can copy different folders to restore Downloads, Documents as well as bookmarks and e-mail settings (like .mozilla and .thunderbird). Other application settings will also be in the different .something folders.

This is probably an overkill, but it should work. Otherwise, you can try to find the log files for GDM and Gnome.

---

### Post by chrisv on 2010-09-22
I will try that. But I already tried "recovery mode" and one of the choices there was to do a text log in as root. I did that and was able to log in fine. But like you I have no idea what to do when I am logged in without the GUI. 

Unfortunately I cannot figure it out myself from there. I am a long time Linux user but I never really played with the internals that much.

[EDIT: This is a reply to bryanfblareunion]

---

### Post by chrisv on 2010-09-22
I tried to run an older version of the kernel but I get the same problem. So it is not the kernel update that did me in. 

I was trying to rack my brains to see what I must have done to cause this and the only thing suspicious that I remember is that I uninstalled evolution. I simply did not use it. Could that break gnome? 

If that is an issue, then how do i reinstall evolution from the text console? I tried 

apt-get install evolution, 

and it installed successfully but it did not solve my problem. Are there any other packages I must install?

---

### Post by Quackers on 2010-09-22
Although it is possible to uninstall evolution if you do it the wrong way (like I did) it can have very bad consequences. You could try going to the Synaptic Package manager and re-installing everything with evolution in the title. Or you could wait for somebody else to give a more specific answer.

EDIT oops you can't get to it can you? Let me have a look around for the command line instructions

---

### Post by Quackers on 2010-09-22
Try this
sudo apt-get update
then
sudo apt-get install ubuntu-desktop
then reboot.
I think the damage is done by ubuntu-desktop being tied in to evolution

---

### Post by 3Miro on 2010-09-22
> **chrisv said:**
> I tried to run an older version of the kernel but I get the same problem. So it is not the kernel update that did me in. 

I was trying to rack my brains to see what I must have done to cause this and the only thing suspicious that I remember is that I uninstalled evolution. I simply did not use it. Could that break gnome? 

If that is an issue, then how do i reinstall evolution from the text console? I tried 

apt-get install evolution, 

and it installed successfully but it did not solve my problem. Are there any other packages I must install?

That is not it.

Something else that you can try: boot into console mode and once you login you can run "startx". Then a lot of stuff will be displayed on the screen and when the startx command fails, you can look at the output for (EE) errors. Hopefully this will help resolve the issue.

---

### Post by chrisv on 2010-09-22
I think I fixed my problem. I did a search about evolution removal issues and found someone complaining that evolution removed gnome-panel. So I did apt-get install gnome-panel and now I am able to log in normally. 

The only problem that remains is that I get an error message on log in that says something about ubuntu not being able to load gnome fast user switch applet. But my computer works otherwise. The fast user switch applet does not seem to break anything, so it may be an unrelated issue. 

Thank you everyone for your help!

---

### Post by chrisv on 2010-09-22
One last note about this. I read the messages above and installed ubuntu-desktop as recommended by Quackers. It fixed the fast user switch applet problem I mentioned before and it installed a lot of packages that I was missing and whose lack would have probably caused problems down the road. 

So thanks a lot Quackers, you were right.

---

### Post by Quackers on 2010-09-22
Even a blind dog can find a bone sometimes :-)
Iknow that when you uninstall evolution it can take ubuntu-desktop with it - because that's what I did and the good folks here put me right.
Apparently evolution is one of those utilities that's tied in to other more important things.

---

