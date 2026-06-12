---
title: "Handbrake Shell script"
date: 2011-05-25
forum: General Help
---

### Post by whitestrat13 on 2011-05-25
I have installed Handbrake on my ubuntu 11.04 system.  It is currently an older machine and is running off of a flash drive while I am doing some "proof of concept" testing.  So far I have set up samba, mdadm, and webmin successfully.  I want to create a script that will be executed everytime I copy a file into a specific folder.  In this case this is what I want to happen:

1.  recognize new file in specific folder
2.  process through handbrake with my "blu-ray" preset
3.  output that file to another folder stored on a separate raid array
4.  Delete the Source file when the encode has been finished

If I can get this to work, I will be building a dual xeon e5645's, 12gb ecc ram, a 250gb re4 for the system drive, and 4x2tb drives (two raid 0 pairs) for source and output drives.  whole thing just less than 2k.

The reason for this is that I am tired of tying up my workstation for hours when I want to re-encode my mkv blu-ray/dvd rips or hd tv recordings.  Currently it takes between 2-3 hrs for a full length blu ray mkv file to be converted from mkv to mp4.  I can rip the disk in 20mins so that isn't an issue.  I just want to rip and save over the network to a specific folder on the linux machine, and then let the linux box do all my encoding without me even knowing it. 

Let me know if anyone has a clue of how to do this...I am a total noob at writing scripts.

---

### Post by katykat on 2011-05-26
Read the instructions ofr handbrakeCLI on the main site. 

The go to the CLI scripting forum, where what you are looking for has probably already been written. (The link is at the end.)

---

### Post by LazyBoy on 2011-06-06
If your linux box has a blu-ray drive, it can do the rip too and you'll avoid that big network copy.  Use halevt to kick it off automatically whenever you stick a blu-ray in the drive.

---

