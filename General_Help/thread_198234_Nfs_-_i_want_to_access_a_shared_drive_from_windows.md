---
title: "Nfs - i want to access a shared drive from windows"
date: 2006-06-16
forum: General Help
---

### Post by CameronCalver on 2006-06-16
Hey i have about 6 computer at work and i would like to slowly migrate to linux ubuntu so i want the server to be ubuntu first.
I would like to have nfs to share /media/the partition
Can some1 help me and give me step by step

---

### Post by CameronCalver on 2006-06-16
And i kinda need it quick so i dont have the server down for two long when iam doing it

---

### Post by scxtt on 2006-06-17
this is a work in progress, and i don't really have a good test to see if it works - but try this:

1. open synaptic
2. install "nfs-common" and "nfs-kernel-server"
3. select a folder in ubuntu to share, right click on it and select "share folder" ...
4. open up windows and "map network drive"
5. pick a drive letter for windows, enter the path to the share, example:
[indent]\\192.168.1.100\home\scott\shared_folder[/indent]
6. after selecting "finish" you should see a new drive letter in windows that is the drive in linux.

a couple notes:

i wasn't able to check that it worked - i only have XP in a Virtual Machine and i'm having problems figuring out how to specify "who" can access the share in native ubuntu - shouldn't be a problem for your network ... you'll see what i'm talking about when you do step 3 ...

one of these days i'll get my 2nd box up and running so i can test this stuff again ... i was able to VERY easily get NFS going b/t Ubuntu and Fedora Core 4 a few months ago ...

---

### Post by CameronCalver on 2006-06-17
ok 1st when i click share do i do nfs or smb and if nfs what do i do for the host things and where is map network drive in windows

this is what i did made a /home/cameron/share and clicked on specify ip address then i typed in 192.168.1.130 tharts the winxp ip then clicked share now on windows where is map network drive and how do i make a new drive letter?

---

### Post by scxtt on 2006-06-17
if you don't have either installed - it will inform you of that (but since you're already working w/ SMB elsewhere, it will be installed - wasn't for me since i don't have any SMB packages installed) - and if you've installed the 2 NFS packages i specified above, you'll be able to select NFS - so make sure you select NFS ...

/home/cameron/share and 192.168.1.130 look good - that should work - presuming there aren't any firewall issues ...

"map network drive" directions:

[indent]open "My Computer"
click on "Tools" in the menu bar
select "Map Network Drive"[/indent]

after doing that you'll see how the "new drive letter" comes into play ...

---

### Post by CameronCalver on 2006-06-17
ok i will try it on our family computer(i am only 14 and i built my own computer) when my brother (10 years old) stop playing runescape in 35 mins ok and i just would like to say thanks for the help and yay "Way too much Ubuntu"

---

### Post by CameronCalver on 2006-06-17
ok now when i click finish it says username and password so i type my ubuntu computer name and password then it says 

Username CALVER/cameron

then password what do i type

---

### Post by scxtt on 2006-06-17
windows can be finicky about logins like that - try it multiple times, and it's possible that a restart of XP (to kinda refresh its networking) might help ... i vaguely remember this issue myself - but i forget off the top of my head how i resolved it ...

---

### Post by CameronCalver on 2006-06-17
I dont have a clue what the password for CALVER/cameron would be and i cant even create the drive it does not let me create it unless i type in the password can some1 help me

---

### Post by scxtt on 2006-06-17
it would most likely be the password for the user cameron, that's you isn't it?

---

### Post by CameronCalver on 2006-06-17
well i tryed my username cameron's password and it didnt work but the part that says CALVER that is the work group name on windows so what does that meen

---

### Post by handy on 2006-06-17
Cameron when you installed windoze, it would have asked you for an administrator account name & password.  If you can remember what that password was it may get you out of trouble.

The other problem that you face with windoze & networking, is that you can do all the right things & it doesn't work.  So, you undo it all, restart the machines, & set it up again, if it doesn't work you go through the undo / redo some more.  Then when it decides to work, it usually keeps on working.

All the best!

---

### Post by scxtt on 2006-06-17
yes, that's what i was trying to get @ before w/ my "finicky" comment -- thanks handy :) ...

---

### Post by CameronCalver on 2006-06-17
lol thanks greg how can i find out the username and password for the window computer or do you know it handy

---

### Post by handy on 2006-06-17
[QUOTE=CameronCalver]lol thanks greg how can i find out the username and password for the window computer or do you know it handy[/QUOTE]

Cameron, did I set up that windoze or did you?

If I did it, try **pass**

---

### Post by CameronCalver on 2006-06-17
ok i created a name and password for the windows computer but when i type in cameron (ubuntu account name) password it work then it says
CALVER/cameron as the username then for the password i typed wordpass and it is not right  this is exactly what it sayas


Connect to localhost.localdomain

Conecting to 192.168.1.110

Username CALVER\cameron

Password  ......

remember  password {}



p.s scxtt i know handy in real life so if your confused about when handy said cameron did i set  up that or did you

---

### Post by scxtt on 2006-06-17
just figured something out by "exploring" at work ... they're using samba, even on the unix box (white box linux running kde) - which is fine, but totally messed up my theory :p ... anyway i still think windows/linux & NFS will work, but XP will need a NFS client ... i've found one, but haven't tried it yet, it's [crossmeta](http://www.crossmeta.com/downloads/crossmeta-nfs-1_0_1.zip) - check it out if you'd like, i will when i'm done @ work ...

---

### Post by CameronCalver on 2006-06-17
ok ui downloaded that file run the setup and it createds a virtual drive i think this is getting too hard

---

### Post by nix4me on 2006-06-17
NFS will not be accessible from windows doing the steps posted above.

You will have to use samba for that.

nix4me

---

### Post by scxtt on 2006-06-17
you're right ... when i wrote that, i was almost certain the procedure we have at work was referring to a NFS share - but today, when i checked what the IP address was pointing to, it turned out to be a Windows 2000 box using samba ... i don't have any reason to believe NFS + Windows won't work, but "map network drive" can't connect to NFS ...

---

### Post by CameronCalver on 2006-06-17
ok well as you would know i have set up a samba now (becuase u helped me) so it doesnt matter

---

### Post by nix4me on 2006-06-17
NFS is unix/linux specific.

There are some windows file utilities that would work, but by default windows will not access a NFS share.

Thats what samba is for.  It works fine.

nix4me

---

### Post by CameronCalver on 2006-06-17
this has nothing to do with the thread but how do you do those code boxes when yout type things like sudo apt-get blahblah

---

### Post by scxtt on 2006-06-17
[quote=nix4me]There are some windows file utilities that would work, but by default windows will not access a NFS share.[/quote]no one said explicitly that it would ... and yes, samba will work - but it can be frustruating to set up ...

[quote=CameronCalver]. . . how do you do those code boxes when yout type things . . .[/quote]by using tags like <quote></quote> and <code></code> -- but replace <> with [] ...

---

### Post by CameronCalver on 2006-06-17
k just testing and you no how when u reply there are things  font sizes is there a code one

---

### Post by CameronCalver on 2006-06-17
```
just testing
```

---

### Post by scxtt on 2006-06-17
<size="1,2,3,4,5,6,7">text you want bigger/smaller</size>

you can get to all this if you "go advanced" ...

---

### Post by CameronCalver on 2006-06-17
when u go advanced how do you get the code box from a button

---

### Post by scxtt on 2006-06-17
unless you're using an incompatible browser (i use firefox, in ubuntu of course) you should see:

pound sign (#) for "code" tags
left and right angle brackets (<>) for html tags
a talking bubble (like in comics) for quotes

---

### Post by CameronCalver on 2006-06-17
```
yep i found it it is the hash and thanks for all your help
```



,cameron

---

