---
title: "Help!"
date: 2009-09-15
forum: General Help
---

### Post by webcabbie on 2009-09-15
Ive been an ubuntu user for a year or so now and never bothered to learn any of the terminal commands or that crap.

Im just not that kind of pc user. I love ubuntu but, today after an automatic update I restarted and it started doing some disk check crap. 

it found errors and said run fsck. so i did. 

It found some errors and asked me if I wanted to fix them so I  said Yes. 

Then when it restarts I go to log in and after putting in my username and password I get a black screen with an arrow and nothing else. 

Not having any technical know how I decided to throw in the live cd and then pull my files that I desperately need onto a usb drive. 

Should work fine right? As it happens every single file that I need  is locked and it tells me I dont have permissions.

I called the geek friend who got me using Ubuntu in the first place and he was saying something about logging into to it with ssh blah blah blah chinese.. IF I had that level of technical ability I wouldnt be driving a freaking taxi for a living. 

I am hoping someone out there takes pitty on me and has easy to follow moron instructions on how I can get to my files. 
--
If anyone out there can help please call me at  781-284-2842

---

### Post by ram2500 on 2009-09-15
Did you run fsck while the disk was mounted (in use?) - Running fsck while the drive is mounted (in use) can cause serious errors. In that case, try typing startx to see if it will log you into the GUI (graphical user interface). 

There's a big chance that fsck had corrupted some files, so if you can't get to the GUI, try to copy the directories of which your files are stored to a flash drive using the cp command (ex: cp /home/Documents /media/flashdrive) you will likely need to type sudo before this- it will enable you to perform this task. 

You will have to mount the drive that you're copying to: mount /media/flashdrive is an example.

I understand your frustration with the command line...but, it's not cr*p! It's a powerful tool. You'll get a grip on it as you use it more often.

---

### Post by jonobr on 2009-09-15
Man thats a good post.

Running the terminal commands here may not be so bad and may get you out of a jam

I would check to see if you can start the gui first.
When you login, you could try a startx, to start the gui, although Im not sure that will work.

I would try to ssh to the machine first.
You can do this by using a windows or other box if you have one handy and download an application called putty.

IN putty put in the ip address of the machine and hit open,.

If that works you should get a login prompt.
Now your into a  cli now after entering your password
What I would then do is to archive all your files.

If they are in the desktop in a folder called blah

I would type 

```
cd ~/Desktop
```

Then type

```
tar -cvf blah.tar blah
```

This creates an archive callod blah.tar of your files .

If you have items in another place we can try and get them copied for you using the cp command,. just let me know where they are and I can help

Once you archive you have a file called blah.tar

With that you can move them to your USB drive or you could copy them off to your windows or other box across your network.


Copying may require the sudo command but it will be something like
```
cp ~/Desktop/blah.tar /media/Somefilehandle
```

If you want to use the windows method, I would downlaod an ftp application like 3cdaemon (you can doa google for that.,

If you want to go that road I could explain how to setup

---

### Post by Yannick Le Saint kyncani on 2009-09-15
> **webcabbie said:**
> INot having any technical know how I decided to throw in the live cd and then pull my files that I desperately need onto a usb drive. 

Should work fine right? As it happens every single file that I need  is locked and it tells me I dont have permissions.

alt+f2 -> gksudo nautilus

---

### Post by jzacsh on 2009-09-15
> **Yannick Le Saint kyncani said:**
> alt+f2 -> gksudo nautilus

I agree with Yannick....
[LIST]
[*]go back in with the LiveCD like you did before
[*]hit the keys **_alt_**+**_F2_**
[*]in the field that comes up type "gksudo nautilus"
[*]put in your password when prompted
[*]now, through this file browser, you won't get permissions problems when you try to pull your files
[/LIST]

---

### Post by webcabbie on 2010-01-17
I never came back here and said thank you.. the Nautilus thing worked. I was able to recover my data. I sincerely apologise for not coming back to say thank you until now.

---

