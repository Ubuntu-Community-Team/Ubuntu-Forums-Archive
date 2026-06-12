---
title: "Can't get samba sharing to work"
date: 2009-11-18
forum: General Help
---

### Post by TheOrangePeanut on 2009-11-18
Okay, I have a desktop machine with Ubuntu 9.10 installed on it.  I have installed samba through aptitude, and I think nautilus-share was already installed.  

I tried to share several folders by right clicking them and hitting sharing options.  A box popped up ('folder sharing') and I clicked the button "Share this folder."  I also clicked the button "Guest Access".  I assumed this is all I had to do.

I got onto my Windows laptop and browsed the network.  I double clicked the desktop that should have been sharing the files and was prompted with a login box like I expected.  I typed guest and hit enter.  The browser window came up and there my folders were... however, when I tried to open them I got an error message that it could not find the folder (error code 0x80070035) and that I should check the spelling.  Well, I can't really do that since I'm just browsing and Nautilus doesn't give you the actual path in an address bar but a breadcrumb trail of buttons.

If I get on the actual machine that is doing the sharing, I can go to places -> network -> Windows Network -> 'WORKGROUP' and from there I can see the machine.  I can open it in the browser and see the folders I'm sharing, but there too it says "Unable to mount Windows share."

Did I miss a step, or do something wrong?  Can someone help me out here?

---

### Post by TheOrangePeanut on 2009-11-18
Anyone?

---

### Post by pcvii on 2009-11-18
I am having the same issue kinda. bassically ubuntu for me doesn't show a WORKGROUP or my laptop's computer in the Network folder. I have to type in smb://ComputerName to connect to my laptop. I think it's supposed to show my computer or allow me to browse the work group.

My laptop is running windows xp

---

### Post by TheOrangePeanut on 2009-11-20
It's similar, but backwards.  My Ubuntu PC has the samba server, and I can't open any folders from my Windows PC.

---

### Post by TheOrangePeanut on 2009-11-21
It's pretty frustrating that no one can even hazard a guess or give me a clue.

---

### Post by Iowan on 2009-11-21
Help is out there - it (he?) just hasn't found you yet. ;)
I've read other threads that suggest installing **smbfs** along with the **samba**. Did you try setting up a share via */etc/samba/smb.conf*?
[Here]("https://help.ubuntu.com/8.10/internet/C/networking-shares.html") is a (dated) How-To.

---

### Post by zachjg on 2009-11-25
I'm having a similar issue, although I'm not entirely sure if they are the same. When I enable the guest access option I can see the shares although I am unable to access them. This was remedied by turning off guest access, although you need to use the username/password of the owner of the files to access them. Here is another thread about the issue I'm having:
[http://ubuntuforums.org/showthread.php?t=1335774](http://ubuntuforums.org/showthread.php?t=1335774)

I had everything working perfectly with previous version of Ubuntu, but this is starting to get really frustrating. I've already encountered two major issues with file sharing in 9.10.

Hopefully someone has some suggestions.

---

### Post by DandyAndy on 2009-12-02
I don't have a lot of beans and i dont deserve any more than the ones i got but i just sorted out this issue in our home setup. Maybe it'll help some one as simple as me or help some one skilled find whats wrong.

My Girlfriends  Macbook could not access the share on our Ubuntu desktop machine, you could see the folder but not access it getting an error message saying something like "The operation cannot be completed because the original item Videos cannot be found"

I tried adding new shares with Samba Server Configuration (a GUI-thing for samba share which i barely remember installing, ). And these shares actually worked. 
So i tried adding the share that initially didnt work (home/Me/Videos) and still no luck. It did however start changing between the name videos and Videos indicating that something was wrong with it or having been set in different places.

So i did ```
sudo nautilus
``` and went to its properties through the right click menu and changed to not being shared and now it works. (there is sharing option availble directly thorugh right clicking as well but thats not what i used if it matters)
The working and non working shares looked exactly the same in: 

/etc/samba/smb.conf

all along so i suppose my tip is to try to unshare with nautilus and add them manually in smb.conf or through that GUI-tool i used.

I have NO idea what difference it makes but it was the only difference between working and non working shares in my case. 
In Nautilus the nonworking had that little shared-symbol with arrows on it. And now with them gone its ok.

---

