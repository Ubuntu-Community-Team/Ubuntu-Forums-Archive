---
title: "Virtual Box"
date: 2012-02-26
forum: General Help
---

### Post by wingnut2626 on 2012-02-26
I've seen several posts on this, and i cannot figure out why i cannot make it work the way everyone else has made it work.  I have ubuntu 10.04 as my host system, and im running a Windows XP virtual machine.  I want to share files between the two operating systems.  How can I make this work in the easiest, most efficient manner?

---

### Post by Pilot6 on 2012-02-26
You need to make shared folders. Just look in the docs.

---

### Post by wingnut2626 on 2012-02-26
I've tried all of that and its not working.  

net use x:  yadda yadda.  Its simply not working.  What is wrong

---

### Post by howefield on 2012-02-26
Try being a bit more expansive in your postings as to what you tried and the resultant errors/issues, othewise it becomes a game of 20 questions.

Presumably you are using a current version of virtualbox and have the extension pack and also guest additions installed ?

Have you tried checking the automount checkbox in the VM settings.

I used to use shared folders but these days simply put the network adapter in bridged mode, this makes the guest appear like a separate computer on the network.

---

### Post by haqking on 2012-02-26
[http://www.virtualbox.org/manual/ch04.html#sharedfolders](http://www.virtualbox.org/manual/ch04.html#sharedfolders)


we need errors or steps of the instructions that you cannot complete

In windows XP just choose map network drive from windows explorer and you choose browse, you should see the virtual box icon in your network then choose the shared resource

---

### Post by Morbius1 on 2012-02-26
> **wingnut2626 said:**
> I've tried all of that and its not working.  

net use x:  yadda yadda.  Its simply not working.  What is wrong
There's no need to do that anymore. If you created a shared folder within the VBox application itself it will mount in the Windows guest and be assigned a drive letter automatically.

You have to have guest additions installed first though within the Windows guest.

---

### Post by wingnut2626 on 2012-02-26
You know you are right.  I'm just so frusterated that i posted things quickly.  This is what i tried:

I installed the Guest Additions on the XP virtual box:

I then added a folder called "Windows"  on my ubuntu desktop that i wanted to use as a shared folder.  

So running the virtual machine, i then added the folder in the list of shared resources.  

So i went back to my XP machine and typed the following command:

net use x: //vboxsvr/windows

and i get a "network not found message"

---

### Post by haqking on 2012-02-26
> **wingnut2626 said:**
> You know you are right.  I'm just so frusterated that i posted things quickly.  This is what i tried:

I installed the Guest Additions on the XP virtual box:

I then added a folder called "Windows"  on my ubuntu desktop that i wanted to use as a shared folder.  

So running the virtual machine, i then added the folder in the list of shared resources.  

So i went back to my XP machine and typed the following command:

**net use x: //vboxsvr/windows**

and i get a "network not found message"


UNC paths use \ and not /

should be as follows

```
net use x: \\vboxsvr\windows
```

plus as already said if it isnt already mounted then you can browse in network neighbourhood anyways

---

### Post by wingnut2626 on 2012-02-26
I just tried the code that you provided and i still got the same error message.  67 Network address not found #-o

---

### Post by haqking on 2012-02-26
> **wingnut2626 said:**
> I just tried the code that you provided and i still got the same error message.  67 Network address not found #-o

well i cant say that i gave you the correct address, only the correct format.

as mentioned a few times though, have you tried just using windows explorer and choosing map network drive and then browsing to the shared folder

---

### Post by wingnut2626 on 2012-02-26
Where do i zctually find that?  I can find network places but nothing shows up.

---

### Post by TheFu on 2012-02-26
The methods being described are to share host files with the client OS.
if you are trying to share files inside the client OS back to the host, then you need to setup a network shared folder inside WinXP and don't need to worry about the vbox "shared folders" settings (inside the VM settings) at all.

In general, virtualization doesn't alter the way that client machines share network resources ... provided the client IP address isn't NAT or firewalled.

I hope this doesn't confuse the the other posts. As I read those, they seemed to assume you were trying to share files from the hostOS ... but you never actually said that.

---

### Post by wingnut2626 on 2012-02-26
That is what i am trying to do.  Is there any way that someone can provide me thr comprehensive directions from step one?

---

### Post by Morbius1 on 2012-02-26
> I installed the Guest Additions on the XP virtual box:

I then added a folder called "Windows"  on my ubuntu desktop that i wanted to use as a shared folder.  

So running the virtual machine, i then added the folder in the list of shared resources.  I just did the same thing ( different path ) on my Win2K guest: First attachment

Now when I start my Win2K guest I see this in Explorer: Second attachment

All happens automatically.

---

### Post by haqking on 2012-02-26
> **TheFu said:**
> The methods being described are to share host files with the client OS.
**[B]if you are trying to share files inside the client OS back to the host**, then you need to setup a network shared folder inside WinXP and don't need to worry about the vbox "shared folders" settings (inside the VM settings) at all[/B].

In general, virtualization doesn't alter the way that client machines share network resources ... provided the client IP address isn't NAT or firewalled.

I hope this doesn't confuse the the other posts. As I read those, they seemed to assume you were trying to share files from the hostOS ... but you never actually said that.


You dont **NEED** to.

Shared folders does the same thing.

If you have a shared folder, you can get files from the host to the client or vice versa.

It is the same thing

---

### Post by wingnut2626 on 2012-02-26
See, but heres the thing.  I have no access to the E: drive.  It doesnt show up.

---

### Post by wingnut2626 on 2012-02-26
Also, when I run the "net use" command in the Windows terminal to see what devices im connected to, i get nothing.  FRUSTERATING

---

### Post by guestolo on 2012-02-26
You have "Windows" folder on Ubuntu desktop, you want to share with XP virtual machine

In XP Virtual machine
Go to DEVICES>>Shared Folders
Add a Shared folder
In the folder path dropdown menu, navigate to the shared folder on Ubuntu desktop and select it
You may want to choose to Automount and make Permanent
OK out of there

Remain In XP virtual machine
Right click on START button and choose Explore
In the left pane, look for "My Network Places"
Expand it>> then expand on"Entire Network" >> "VirtualBox Shared Folders" >> " and possibly **" \\Vboxsvr"**

Look for your Shared Windows folder [B]\\VBOXSVR\Windows

[/B]You can then do the next steps
Click on TOOLS>> in the top menu bar in XP
Select "Map Network Drive"
Choose a Letter assignment, you can leave it Z. as default
Then Browse to that networked folder [B]\\VBOXSVR\Windows
[/B]OK and Finish

Now, if you want, go to MyComputer in XP
under Network drives
Right click on your new mapped drive and select "Create Shortcut"
Should prompt to put the shortcut on desktop

That should do it :)
Works for me, anyways

Take note: To view the Folders in the left pane of Explorer in XP
Ensure the next is set in Explorer menu bar
 VIEW>>Explorer bar>>**Folders **checked

---

### Post by wingnut2626 on 2012-02-27
Thank you!  That worked.  I've got a few more questions but i think i'm going to start a nes thread for those.

---

