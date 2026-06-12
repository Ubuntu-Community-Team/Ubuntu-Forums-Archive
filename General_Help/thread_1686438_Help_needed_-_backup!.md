---
title: "Help needed - backup!"
date: 2011-02-12
forum: General Help
---

### Post by christia on 2011-02-12
Serious help needed.

I recently upgraded 10.04 to 10.10. I fidled around with some stuff (am not super user in any way), and now the computer can't log into the gui. it just goes to a black screen where it says:

"Ubuntu 10.10 Vaio tty1, Vaio login:"
(i have a sony vaio z)

I can then write "root" and then enter my password and it logs me in, but doing startx gives "fatal error" blabla (i googled it and seems others have had same problem)

Now, i am sure that this can be fixed, but i think i'll just do a clean install cause it was getting a little messed up anyways. However, i recently had a daughter and although i think all pictures are backed up, i want to double check that. So i would like to transfer everything i have in my home folder (i think that is where documents, pictures and movies are saved, right?) to an external harddrive.

So question is simply: what commands should i write to do this from the black screen? (i guess it is the konsole?) Please don't leave out any details if possible as i am no expert

thanks!

---

### Post by MrRichard on 2011-02-12
I'm not too sure on the commands to copy a folder, so I cannot help you there. But there's an easier way. Do you have your Ubuntu Live CD/USB still? If not can you make one?

If you can, you will be able to view your installation of Ubuntu and your external hard drive.

---

### Post by thefasterblueone on 2011-02-12
After logging in try:

```
sudo service gdm start
```

---

### Post by christia on 2011-02-12
for the gdm thing, when i do that it says:

"start: Job is already running: gdm"
?


For the live CD thing, will that work? i won't have same problem as with this thing? Can i do a new live cd then?

---

### Post by MrRichard on 2011-02-12
> **christia said:**
> for the gdm thing, when i do that it says:

"start: Job is already running: gdm"
?


For the live CD thing, will that work? i won't have same problem as with this thing? Can i do a new live cd then?

Yes, you can. The Live CD is like an operating system on it's own; completely independent of any other software.

Go to ubuntu.com and download Ubuntu 10.10 or Ubuntu 10.04 and burn it to a CD or to a USB. Boot from that CD/USB and click "Try Now." A default Ubuntu desktop should greet you. From there, you can browse your files and backup anything you'd like :)

---

### Post by christia on 2011-02-12
Thanks, i will try to give that a go! So i can access my files from the cd-version?

Although i get super frustrated quite often when i use ubuntu, it is in some way quite fun with these issues!

if anyone knows how to transfer the stuff, please let me know as well! just in case...

---

### Post by MrRichard on 2011-02-12
> **christia said:**
> Thanks, i will try to give that a go! So i can access my files from the cd-version?

Although i get super frustrated quite often when i use ubuntu, it is in some way quite fun with these issues!

if anyone knows how to transfer the stuff, please let me know as well! just in case...

Yes, you can access your files from the CD Version. I hope your future experiences with Ubuntu and Linux is a lot smoother and less problematic. :)

---

### Post by Habeouscorpus on 2011-02-12
Do you have other accounts besides root? I think (not sure) that X cannot be run as root. Try logging into the other account.

---

### Post by christia on 2011-02-12
yeah have other user but also doesn't work there. 

this all happened because i blindly (stupidly) just copy pasted some sudo this sudo that stuff into the console when i was trying to get chromium to work properly

actually that is my top issue with ubuntu - i love chrome, i want it, and i want the latest flash to be easy to install. don't have very good experiences with this.

i think i will try linux mint next time. am very happy with ubuntu, but i just want a distro that is FAST, works without too much hazzle (i don't mind a little searching, but not all the time) and has programs i like

---

