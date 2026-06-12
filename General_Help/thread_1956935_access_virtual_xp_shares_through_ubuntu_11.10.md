---
title: "access virtual xp shares through ubuntu 11.10"
date: 2012-04-11
forum: General Help
---

### Post by Robert R on 2012-04-11
Hi i currently have ubuntu 11.10 installed and would like to know how can i access shares on a xp virtual machine. The vm is installed on virtual box.  can anyone help i can ping the machine but just dont know where to start to access shares on the vm.

---

### Post by PhantomTurtle on 2012-04-11
[http://ubuntuforums.org/archive/index.php/t-627847.html]("http://ubuntuforums.org/archive/index.php/t-627847.html"). Also I think you need to be in the vbox users group to do this. Here is a tutorial: [http://www.webupd8.org/2011/02/get-your-usb-drives-to-work-with.html]("http://www.webupd8.org/2011/02/get-your-usb-drives-to-work-with.html")

---

### Post by anejo on 2012-04-12
Make sure you have the vbox guest additions installed on the XP instance.
You say that you want to access shares on XP... I am assuming that you want to have access to those files in Linux?

---

### Post by Robert R on 2012-04-16
> **anejo said:**
> Make sure you have the vbox guest additions installed on the XP instance.
You say that you want to access shares on XP... I am assuming that you want to have access to those files in Linux?

Yes i would like to create a share so i can pass files from linux to the vm xp and vice versa

---

### Post by haqking on 2012-04-16
its called shared folders

[http://www.virtualbox.org/manual/ch04.html#sharedfolders](http://www.virtualbox.org/manual/ch04.html#sharedfolders)

---

### Post by anejo on 2012-04-17
So... did the link at vbox.org help you?
The process is real simple but if you want the setup steps again, just ask...

---

### Post by Robert R on 2012-04-17
> **anejo said:**
> So... did the link at vbox.org help you?
The process is real simple but if you want the setup steps again, just ask...

I know it supposed to be simple but just for clarity my setup is:

Desktop has Ubuntu 11.10 installed 
 
2 vms on virtual box

1 xp and 1 server 2003 

The machines are using a bridged adapter and are on the same subnet as my physical machines. So they can ping everyone by ip address.. 

im really not familiar with networking in Linux or how it works. Someone told me i had to install samba, but i cant find it since the new ubuntu release i dont see the software centre is so difficult to use the old package manager was soo much simpler. \

Now im not sure how do i set up a shared folder on the linux machine so windows can see it... before i set up the sahres on the xp machine and then use a mount toll to mount the link on my linux desktop but i cant even find or install the GUI for umount,

---

### Post by Morbius1 on 2012-04-17
[1] VBox shared folder.

As stated earlier, if you set up a shared folder from within VBox application itself then the guest OS will automatically mount it and even give it a "drive" letter in Windows without you having to take any other actions.

[2] Assuming you want to simulate a true network:
> Now im not sure how do i set up a shared folder on the linux machine so windows can see it.
The same way you create a "Simple Share" on WInXP: Right click a file you own > Select "Sharing Options" > Select all the boxes > You have just create a Samba guest share. That process will automatically install the correct version of Samba.

[3] Connecting to the WinXP share:
Nautilus > Network > .....

If for whatever reason that doesn't work. In a terminal type:
```
nautilus smb://192.168.0.100
```[COLOR=Blue]*Changing 192.168.0.100 to the ip address of the WinXP guest.*[/COLOR]

---

### Post by Robert R on 2012-04-23
> **Morbius1 said:**
> [1] VBox shared folder.



[2] Assuming you want to simulate a true network:
The same way you create a "Simple Share" on WInXP: Right click a file you own > Select "Sharing Options" > Select all the boxes > You have just create a Samba guest share. That process will automatically install the correct version of Samba.

[3] Connecting to the WinXP share:
Nautilus > Network > .....

If for whatever reason that doesn't work. In a terminal type:
```
nautilus smb://192.168.0.100
```[COLOR=Blue]*Changing 192.168.0.100 to the ip address of the WinXP guest.*[/COLOR]

Hey that worked just like i wanted it to thanks alot

---

### Post by forrestcupp on 2012-04-23
Just for future reference in case someone is confused, you don't have to set up a network share to have a shared folder in Virtual Box.

---

