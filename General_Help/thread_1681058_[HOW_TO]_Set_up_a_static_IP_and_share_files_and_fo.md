---
title: "[HOW TO] Set up a static IP and share files and folders on your local network"
date: 2011-02-03
forum: General Help
---

### Post by balta on 2011-02-03
So I had quite a busy afternoon figuring how to do that, therefore I'll write a brief how to just in case someone can save some of his time.

First, what I wanted to do (aka *The Scenario* lol)
My machine dual boots windows7 and ubuntu 10.10, I share from the machine some files and folders I want to access from other machines running ubuntu or windows XP and from my wii (using WiiMC).
I wanted the shares to be accessed in the very same way, independently from the contents being shared from ubuntu or windows.
I set up on windows a static IP (192.168.1.140) and I access the files like
```
smb:///192.168.1.140
``` from other ubuntu machines and wii
and
```
\\192.168.1.140
``` from windows machines (under winXP home, it asks me for a login, any login grants me access so I really don't see the point of it but I can't avoid it... sorry)

Now, I'm quite sure I could have spared the hassle of setting up the static IP if I had referred to the machine name instead of it's IP, but well, the deed is done, and I did this way; if you manage to do it the other way round, please tell me, next time I'll have lees difficulties.

Second, the procedure.
[LIST]Set up a static IP
[/LIST]
I tried and failed setting up a static IP from the nice GUI of the Network Manager, and I found out that it causes problems (for the method I used).
Again, if you managed to do it with the GUI, please tell me, it would have been much easier.
[LIST=1]
[*]Remove the network manager from the automatic startup applications
Start > System > preferences > Startup applications and erase the checkbox from network manager

[*]Create a static valid static IP configuration in /etc/network/interfaces
To do so let us first create a backup of the existing configuration, you never know
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bk 
```
Then lets edit the file (you can use your own favorite editor, I used vim because it makes you feel like a true hacker, in the example I use gedit because it's easier and available for everyone)
```
sudo gedit /etc/network/interfaces
```
The content of the file should look something like
```
auto lo
iface lo inet loopback
```

Make it look something like
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address <YOUR STATIC IP ADDRESS>
netmask <YOUR NETMASK>
gateway <YOUR GATEWAY>
```

For instance mine looks like
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.140
netmask 255.255.255.0
gateway 192.168.1.1
```
[/LIST]

Done! Please triple check the numbers you enter, if you input something wrong ubuntu won't pop up any fancy window but will just silently not work.

Now on, lets share something.
I shared some folders from an internal hard-drive owned by *root*, for doing this I had to modify the configuration file of samba in a way one could share something not owned by him. I do believe that an alternative solution would have been to change the owner of the disk (using chow), but well, it works so now on!
[LIST]
[*]Select the folder you want to share
[*]Right click > Sharing Options
[*]Tick the first check-box labeled share this folder
[*]A pop up should appear telling you that software is missing, just obey and install it
[*]Reboot
[*]Please note that the following 2 steps are required only if you will be sharing folders you don't own
[*]Run this command from a terminal ```
sudo gedit /etc/samba/smb.conf
```
[*]Add the following line anywhere in the [global] section ```
usershare owner only = false
```
[*]Re-select the folder you want to share
[*]Right click > Sharing Options 
[*]Select a good name for the share, please avoid spaces. If you feel like it, put a fancy description.
[*]Decide for yourself if you want to check the second one to be checked, it's quite self explanatory.
[*]Same for the third one (personally I have always checked everything, I'm quite sure it is not very safe, but it works; I haven't tried yet other configs to see how do they work with windows and the wii, if you do know, please share your knowledge)
[/LIST]

And that should be!
For any problems feel free to comment here, I'm really not an expert but if I'll try my best to help you!

Have fun!

PS: sorry for the very low quality of the guide, I'm in a hurry and it's my first work, please be kind

---

