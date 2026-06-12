---
title: "Samba Shares , Unable to find in Windows 7"
date: 2011-02-19
forum: General Help
---

### Post by pages on 2011-02-19
Hi all I'm trying to set up a share for my system which is dual booting windows 7 64bit and ubuntu 32bit 10.10

What i did 
-Install Samba from the Ubuntu software center
- In System->Admin->Samba add the share for my /Home/Downloads
- In smb.conf i edited the workgroup to that of my windows7 workgroup
- In the home folder right clicked on Downloads and in sharing option i allowed others create and delete privileges and Guest access ( security not an issue). Then allowed Nautilus to add the permissions automatically 

Now from what I have seen if i go into windows 7 in the network section i should have a Ubuntu share appearing but i don't. The only devices which show are the router and the computer itself ( of which ubuntu isn't in)

Is there anything i missed or how do i access these files ?
Thanks for any help,
Pages

---

### Post by emarkay on 2011-02-21
I am sad to note you have had no responses.  As a long time Ubuntu user (since 2006) I have STILL not gotten Samba to work seamlessly in my simple home network.  I have filed legit bugs and asked for help numerous times.  ( feel free to search here...)  It's not a "critical issue" for me, but it still to put it bluntly, sux that I can't network.

As I only have XPSP3 here on some machines, I can not even offer debugging assistance.

[B]
Hey, Ubuntu Network experts here, what about it, give this person some help![/B]

---

### Post by Morbius1 on 2011-02-21
> - In System->Admin->Samba add the share for my /Home/DownloadsYou created a Samba share using the Classic-share method.
> - In the home folder right clicked on Downloads and in sharing option i  allowed others create and delete privileges and Guest access ( security  not an issue). Then allowed Nautilus to add the permissions  automatically You created a Samba share of the exact same directory using a completely different Samba method called Usershares ( aka nautilus share ).

These two methods create share definitions in two completely different places and it isn't a good idea to use both methods on the same folder in the long run. I think you could see how they could get out of sync in time.

The first thing I would do in terms of diagnostics is the following:

(1) Firewall
If you're using one on Windows or Linux disable it and see if that's what's getting in the way.

(2) Make sure all samba services are running on Linux:
```
sudo service smbd start
sudo service nmbd start
```If they aren't running these commands will start it. If they are running it will tell you that.

(3) Finally post the output of the following command from the Linux box:
```
smbtree
```It will list every workgroup and within every workgroup all of it's available shares. If it finds a problem it will give you an error message. All we're really interested in at this point is if it can see it's own shares.

---

### Post by pages on 2011-02-21
I disabled my firewalls to begin with and no success 

Booted into linux and ran the two commands to start the services ,
The smbd service was already running 
but nmbd came up as an unrecognised service ?

And the output from smbtree is as follows 
```

WORKGROUP-NEW
\\UBUNTU         		ubuntu server (Samba, Ubuntu)
\\UBUNTU\IPC$           	IPC Service (ubuntu server (Samba, Ubuntu))
\\UBUNTU\Downloads      	
\\UBUNTU\print$         	Printer Drivers

```

And thank you for your efforts in trying to fix this problem,
Pages

---

### Post by Morbius1 on 2011-02-21
That's rather confusing. If you did a:
```
sudo service nmbd start
```and it came back with "unrecognized service", you wouldn't get any output from smbtree.

Anyway, smbtree accurately shows your shares so let's do one more thing on the Ubuntu system: Run the following command and see if Ubuntu can connect to it's own share:
```
nautilus smb://ubuntu
```It should open up Nautilus and show you your shares. Post any errors.

On the Win7 system let's do the equivalent of smbtree:

Using "Command Prompt "
[COLOR=Blue]*Command Prompt should be under Accessories somewhere - doing this from memory*[/COLOR]
Then type:
```
net view
```That should show you: \\UBUBNTU
Then type:
```
net view \\ubuntu
```
That should show you your shares.

It will also output some rather incoherent error messages if there is a problem - but that's something to work with.

---

### Post by pages on 2011-02-21
nautilus smb://ubuntu

Opened the window which correctly showed the folders I want to be able to access - No errors propagated at all

Rebooting into Windows 7 in cmd I ran
net view
```

Name                  Remark
------------------------------------------------------
Shane-ASUS

Completed successfully
>

```


So it really doesn't give you any errors to work with :( 
Any ideas to where //UBUNTU might be hiding ??
Pages

---

### Post by Morbius1 on 2011-02-21
I don't want to jump to any stupid conclusions but:
> [COLOR=Blue]Rebooting into Windows 7[/COLOR] in cmd I ranWindows 7 and Ubuntu on the same system?

Are you trying to access an Ubuntu share from Windows in a dual boot on the same physical box?

Or is Win7 on one box and Ubuntu on another box?

---

### Post by pages on 2011-02-21
> **Morbius1 said:**
> I don't want to jump to any stupid conclusions but:
Windows 7 and Ubuntu on the same system?


Yes , i'm guessing samba isn't what i'm looking for then :) ?
Sorry for my lack of understanding googling "filesharing on windows and ubuntu" may have guided me wrong

---

### Post by Morbius1 on 2011-02-21
Yes, Samba is a network thing. 

You can't natively access a Linux filesystem from Windows because Windows refuses to believe we exist. There are third party utilities you can install on Windows to give you access but I've never used them - actually I find the thought of Windows accessing a linux system directly rather spooky. 

I have no idea how accurate this is anymore but you might want to look here: [http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

---

### Post by pages on 2011-02-21
thanks for your help 

I just find it annoying i can access my windows files from within Ubuntu but not visa-versa but ******* micro$oft again for you.

But once again thanks,
Pages

---

### Post by BHEJU on 2011-02-21
Hi I assume follwoing situation:
You have dualboot ubuntu and win 7 running on same physical machine.
And you want to have your win 7 read /home/downloads from ubuntu install (which will be ext4 (or 3)).
Assuming this is correct:
you can install EXT2fsd on your win7 machine.
It will give your win7 ability to browse ext file systems.
Then just navigate to downloads folder just like you access win7 file system from ubuntu.
However, I suggest you create a dedicated partition to keep system files safe.
Hope this helps.

Cheers

---

### Post by andyvarner on 2011-03-14
Well I'm actually having the exact problem you thought you were trying to fix. The funny thing for me here is that my windows box can see my laptop which i installed everything the same way but not my server that i'm running from the other room.

laptop(ubuntu) <--good--> desktop(win7) <--bad--> server(ubuntu)

i've followed all the steps up through the net view \\(myservername) part with no real results. shows the laptop, not the server. Any other thoughts?

---

