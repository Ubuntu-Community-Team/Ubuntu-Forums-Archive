---
title: "Help With Ironkey"
date: 2009-08-15
forum: General Help
---

### Post by kyle2595 on 2009-08-15
Hi, I have had my Ironkey USB flash drive for a wile now and I have just tried it with Ubuntu 9.04. When I plug it in, the Ironkey logo appears on my desktop (the silver key with a ring around it), it is attached.
I double - click on it, then I click on "Linux" then "ironkey" and it says: 
> "sh: cannot create /proc/scsi/device_info: Permission denied
unable to add IronKey entry to /proc/scsi/device_info
please try re-running as root
Hit return to exit"

Does any one know how to access it or fix this?
Thank you!

---

### Post by Ranax on 2009-08-15
> **kyle2595 said:**
> Hi, I have had my Ironkey USB flash drive for a wile now and I have just tried it with Ubuntu 9.04. When I plug it in, the Ironkey logo appears on my desktop (the silver key with a ring around it), it is attached.
I double - click on it, then I click on "Linux" then "ironkey" and it says: 


Does any one know how to access it or fix this?
Thank you!

```
sudo nautilus
```

Then goto to your IronKey in the Nautilus treeview. Although that is only a temporary solution.... :(

---

### Post by kyle2595 on 2009-08-17
When I run the command, it says:
> ** (nautilus:13670): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


---

### Post by kyle2595 on 2009-09-15
I FINALLY figured it out! Here's what I did:  (I am running Ubuntu 9.04.)
When I plug in my IronKey, it automatically mounts and the IronKey logo appears on the desktop.  Then I double clicked it, then I double clicked the "Linux" folder, then I right - clicked on the "ironkey" file and clicked "Open With" then  "Open With Other Application" then click "Use a Custom Command" and type: **gksudo**.  Then type in your IronKey password in the window that pops up, hit enter, and you should have a file named "IronKey USB" on your Desktop.
Thanks to all who helped!

---

### Post by dmflad on 2009-10-20
Since Ubuntu (and Open Source) are all about helping and sharing, here's what I shared with Kyle on a PM, in case others find it helpful.

My Launcher settings:
Type: Application in Terminal
Name: IronKey
Command: sudo /media/IronKey/linux/ironkey
Comment: Start IronKey

I plug IK in and wait for light to go out on drive, IK icon/logo appears on my desktop. If I do "df -h" from command line I see new entry:/dev/sr1 50M 50M 0 100% /media/IronKey

Now I click my IK Launcher icon (mine looks like set of keys). A terminal window pops up asking for my sudo password. I enter my password (not root's password)

Now another terminal window pops up labeled "IronKey Unlock" asking for my IK password. I enter enter my IK password and both the IK Unlock and the Terminal screens disappear.

On my desktop I have a new icon, looks like key on top of a folder and is labeled "IronKey USB". When I click it I get a File Browser window of my IK. IK USB also shows in Places menu. Another "df -h" from terminal window and I see new entry: /dev/sdb 3.8G 1.2G 2.7G 30% /media/IronKey USB

I know there was a time when I was transitioning from Ubuntu 8.04 LTS to Ubuntu 9.04 when my Launcher wasn't working quite right and only way to start up IK was to do it all from terminal. During that time I had to su to root, make sure IK was mounted, then cd down into directory /media/IronKey/linux/ and then "sh ironkey".

During that time I kept tweaking my Launcher settings and eventually what I show above is what worked. Unfortunately I'm not sure if I did something correctly or if Ubuntu update fixed something as I tend to keep poking things until I get what I want but seldom do I track what I did to get there.

---

### Post by Givzadamn on 2010-12-23
> **kyle2595 said:**
> I FINALLY figured it out! Here's what I did:  (I am running Ubuntu 9.04.)
When I plug in my IronKey, it automatically mounts and the IronKey logo appears on the desktop.  Then I double clicked it, then I double clicked the "Linux" folder, then I right - clicked on the "ironkey" file and clicked "Open With" then  "Open With Other Application" then click "Use a Custom Command" and type: **gksudo**.  Then type in your IronKey password in the window that pops up, hit enter, and you should have a file named "IronKey USB" on your Desktop.
Thanks to all who helped!

This solution worked perfectly for me in 10.10. Thanks.

---

