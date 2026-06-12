---
title: "Deep Freeze an Account and Clone a PC to make Fat Client lab"
date: 2009-10-18
forum: General Help
---

### Post by jahst on 2009-10-18
This is my first guide attempting to show how to deep freeze an account and clone a single master ubuntu PC making a fatclient lab. It only does the differences in files, so goes very very fast.


**---------------------  The need  --------------------------**

- I needed the students account to be "Frozen" like the program Deep Freeze... Any changes are reset automatically.
- To be able to clone a system over the network so that the changes I make to one machine are automatically applied to the others
- This is not a whole system install... if I only changed 3 things I didn't want to reinstall the entire system... to much time
- I only wanted the differences in the file systems which means "rsync"
- I needed to be able to do everything from one PC.. no logging in to each computer and then changing each one.. to much wasted time.


**--------------------  Disclaimer   ------------------------**

I still consider myself a linux newb.. I've used it for years .. but haven't really tried anything on this scale before... so no promises.. but it worked for me... and worked great. I updated 29 computers in less than 30 minutes... about 1 PC per minute !!!!
Of course this will take longer if you do large changes..because more date needs to be transfered. But when I made a mistake in one of my scripts.. I simply fixed it on the host PC, and then did this. 30 minutes later all the PCs were fixed. I couldn't login to each one in 30 minutes. So you should be able to save a LOT of time.. 

I'm not going to cover installing linux.. this assumes you already have some type of basic install done. This is where Ping, clonezilla, or partimage, or whatever might help. I just burned a few copies of Ubuntu and went PC to PC.. but I'm now looking at ways to speed this up using remastersys to built a super small version of Ubuntu that already has the programs and scripts installed that I need. Speeds up install process. 

I know there are probably ways to use ldap and connect to student login accounts on our Windows Network using PAM etc.. but I don't have the time to do this right now... and not sure I want to risk it on a network I'm not in charge of. This is super simple and works for me. Besides, the first week or two of school some students dont have accounts.. so they cant login.. so they cant work.

I simply create a guest account that students login as, and then mount their network shared folder to the destkop. This way, even if they can't login to the window network.. they can still login as guest on my ubuntu machine.. and do work. 

Student folders are simply shared folders on a windows network.


**--------------------   Requirements   --------------------**

All computers must be exactly the same (or similar enough that linux can adjust itself?)

All computers must have some base linux install.. I think a command line system is enough.. you basically need the partitions, bootloader, and install openssh-server


Must install: openssh-server with root login enabled




**-----------------   Steps On All PC's (Master and Clones)**

1 - ensure all PC's are the same hardware and have the same partitions with ubuntu installed
(Use same admin user names and passwords when you install)
(I made my partitions exactly the same size too... is that necessary?)

mine looked like this

/dev/sda1 Windows XP
/dev/sda2 Windows recovery
/dev/sda3 Ubuntu
/dev/sda4 swap 



2 - Make sure all PCs have rsync and openssh-server installed  ( we will secure it in essential steps )

3 - Make sure all PCs have enable root login "yes" in /etc/ssh/sshd_conf file  


4 - set root password (make it strong and same for all PCs)

sudo passwd root



**-----------------  Steps On the Master Machine - Make at least these essential changes**


0 - Secure admin users /home directory so others cant view it

```
sudo chown "admin user name":"admin user name" -R /home/"admin user name"
```
```
sudo chmod 750 -R /home/"admin user name"/
```
 


1 - Change grub to use partitions rather than UUID.
(You could probably write a fancy script to fix this.. and I might try it one day, but this works fine for now)
This example shows Ubuntu on /dev/sda3

---- old -----

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		2a7886ed-a67b-4e14-bddb-3127c33880e7
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=2a7886ed-a67b-4e14-bddb-3127c33880e7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet


---- new -----

title		Ubuntu 9.04, kernel 2.6.28-15-generic
# uuid		2a7886ed-a67b-4e14-bddb-3127c33880e7
# kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=2a7886ed-a67b-4e14-bddb-3127c33880e7 ro quiet splash
kernel		/boot/vmlinuz-2.6.28-15-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.28-15-generic
quiet




  

  
2 - (optional) fstab is ignored in the script, but you could change that to use partitions rather than UUID as well


3 - install pyneighborhood (this installs all the samba stuff you need to mount windows shares, or you can install the samba packages individually) smbfs and smbclient



4 - create the guest account. 

```
sudo adduser guest
```


5 - Set user privilages to mount USB, share files on network, etc. in System, Admin, Users and Groups
- you can use a terminal and do this quickly


Test with
```
cat /etc/group
```

Change with - should be one line
```
sudo usermod -aG adm,dialout,fax,cdrom,tape,audio,dip,video,plugdev,fuse,lpadmin,netdev,sambashare guest
```

then test again
```
cat /etc/group
```



 **- SECURE THE OPEN SSH server** 
- otherwise they can ssh into other machines as guest

# Restrict ssh access to AllowGroups sshers

edit   /etc/ssh/sshd_config

add the following config option

AllowGroups sshers

Then create new group sshers and check names of users who can use ssh  ( in my case only the admin and root accounts )

DO NOT LET "guest account" SSH - because all machines are clones, and all have same guest name and password they can ssh into other machines... not good.




**- some fnx fixes **
I was having issues with pulseaudio not loading correctly if automatic login was enabled.. so I changed this so they have to use the login screen.

I did remove the guest password to make logging in easier by

sudo gedit /etc/passwd
remove the "x" in the file password location

guest:"X":501:502:Guest:/home/guest:/bin/bash
will look more like
guest::501:502:Guest:/home/guest:/bin/bash



 **------------ Login as Guest Account -----------------------**

6a - Customize the quest account.
6b - Add school color themes for files and folders  [http://www.gnome-look.org/](http://www.gnome-look.org/) is great for this
6c - Setup program defaults you might want, etc
6d - Add scripts to allow access to shared folders on network




This works at my school.. you will need to change the scripts to work on your network.
It mounts 2 shared folders on the network

The Users shared folder for their hidden private files on a windows server
and the common shared folder for all the teachers shared folders
You will need to customize this for your network.. this only works on mine.



---------  Login script   -------------------


```
#!/bin/bash

ip="ip address or hostname for students server here"
servername="hostname of common server here"
commonfolder="shared folder name on common server here"


echo 
echo 'Enter your Windows Login Name'
read UN
echo 'Password will not be visible and cursor will not move!'
echo 'Enter your Windows Password'

# This code hides the password when typing
stty_orig=`stty -g`
stty -echo 
read PW
stty $stty_orig


# This logs out the last person just in case they didnt
# Reads line from hidden .CUN.txt file created during login

while read UN
do
	echo "$UN"
	umount.cifs /home/"$USER"/"$UN"
	rmdir /home/"$USER"/"$UN"
	umount.cifs ~/"$servername"
	rmdir ~/"$servername"
	
done < /home/"$USER"/.CUN.txt


# This creates the new user login information file
echo "$UN" > /home/"$USER"/.CUN.txt

# This makes and mounts the shared folders
mkdir /home/"$USER"/"$UN" --mode=777

# --- Note shared folder is a hidden windows folder
# --- Thats why $UN is "$UN"$  -- the last $ hides the folder on the windows network
# --- If your shared folders are not hidden you will need to replace "$UN"$ with "$UN"

mount.cifs //"$servername"/"$UN"$ /home/"$USER"/"$UN" -o ip="$ip",username="$UN",password="$PW",file_mode=0775,dir_mode=0775

mkdir ~/"$servername"

mount.cifs //"$servername"/"$commonfolder" ~/"$servername"/ -o username="$UN",password="$PW",iocharset=utf8,file_mode=0777,dir_mode=0777

echo
echo Your folder should appear on the desktop
echo If your folder appears to be empty
echo you probably typed your name or password incorrectly
echo and should try again
echo DO NOT FORGET TO LOGOUT AT END OF CLASS
echo Press Enter Key to exit
read enter



```

---------------  logout script  --------------------

```
#!/bin/bash

servername="hostname of common server here"

# Reads line from hidden .CUN.txt file created during login and automatically logs out

while read UN
do
	echo "$UN"
	umount.cifs /home/"$USER"/"$UN"
	rmdir /home/"$USER"/"$UN"
	umount.cifs ~/"$servername"
	rmdir ~/"$servername"	
done < /home/"$USER"/.CUN.txt



# This was stupid because if the user couldn't logout, now they really cant logout.
#rm /home/"$USER"/.CUN.txt


echo 'Your folder should NOT be visible on the Desktop'
echo 'If something is wrong simply reboot your computer'
echo 'Press ENTER to close this window'
read enter


```

-----------------  END LOGIN & LOGOUT SCRIPTS  -----------------




**7 - Add launchers **

I put all my customizations... background, these 2 scripts, and anything else in a hidden folder ".myscripts" in the guest accounts home directory.
Then I make a launcher on the desktop to each script (Login and Logout). 
I made little graphics in "Inkscape" that indicate this for the icons. 
"IN" and "IN" with a big red X through it.. or whatever you decide to make.
This hides the ugly stuff from students.. makes them feel more comfortable with a new OS.

- Right click on desktop
- Create launcher
- Application in terminal
- Give it the correct name (login or logout)
- Browse for the correct script
- Add the correct icon.
- Repeat for other script



**8  - Freeze it !**
8a - Logout guest and login as admin account
8b - Then run this script to "Freeze" it.



---------- DEEP FREEZE SCRIPT -----------

```

#!/bin/bash
echo Enter name of user you want to protect.
read name
sudo mkdir /.secure
sudo chmod 700 /.secure
sudo mkdir /.secure/rsync_"$name"
sudo rsync -r -t -p -o -g -v --progress --delete  -l -D /home/"$name"/ /.secure/rsync_"$name"/
sudo awk 'BEGIN { print "#!/bin/bash\nrsync -a --delete /.secure/rsync_'"$name"'/ /home/'"$name"'/\n" }' > /home/$USER/rsync_"$name".tmp
sudo mv /home/$USER/rsync_"$name".tmp /etc/init.d/rsync_"$name"
sudo chmod +x /etc/init.d/rsync_"$name"
sudo rm /etc/rc2.d/S99rsync_"$name"
sudo ln -s /etc/init.d/rsync_"$name" /etc/rc2.d/S99rsync_"$name"
echo "$name" is now protected.
echo Please rerun this script to protect another user
echo or to update an account with any new changes
echo for that specific user.
echo Press enter to exit.
read exit



```

---------  END DEEP FREEZE SCRIPT -------------

  
  
  
  
9 - I found that logging in automatically broke pulse audio ( ?? ) but if you want them to skip login screen all together and login automatically you can simply do this to enable automatic login.

System, Administration, Login Window, Security
Check the "enable automatic login" box and pick the "guest" account you created

    
  
**10  - Setup cloning script**
10a - Put the "excludes.txt" file someplace safe in admin users home folder
10b - Move the clone script to /usr/bin 
10c - chown root:root
10d - chmod+x
10e - allow only root to view and execute with chmod 700




**------------------ rsync_fatclient_excludes.txt file must be someplace safe like admin account folder-----**


#-----------------------------------------
# Important files and folders to include or exclude
# + /boot/grub
# + /boot/grub/menu.lst
# - /rsyncos
# - /masterimage
- /dev/shm
- /root/.ssh
- /etc/ssh
- /etc/fstab
- /proc
- /lost+found
- /sys
- /tmp
- /mnt
- /media
- /etc/hostname
- /etc/hosts
- /home/master/.gvfs
- /home/guest
- /home/master/.gconfd
#-----------------------------------------




------------------ End Excludes.txt file  ------------
------------------ Rsync_fatclients Clone Script -----------
------------------ Be sure to change file path--------

```


#!/bin/bash
# Clone Rsync Fat Clients

excludes="/path/to/excludes/file/rsync_fatclient_excludes.txt";

echo 'You must be logged in as root via sudo su'
echo 'Rsync from host to client'
echo 'Enter client name or IP address'
echo 'Might need .local appended to client name'
echo 'Try pcname.local if pcname fails'
echo 'Or use IP'
read client

#echo 'Changing to root directory'
cd /


#echo 'changed to root at root directory successful'
#read


echo 'This code rsyncs to client machine as root'
echo Syncs from '/' on host to '/' on "$client"
#echo 'Is this correct?'
#read
rsync -av --ignore-errors --delete --exclude-from="$excludes" --rsh=ssh / root@"$client":/

#echo 'Any Errors?'
#read

echo "$client" completed  

```

-----------  End Clone Rsync_Fatclients script ---------------




11 - Change to root user with sudo su (normal sudo didnt work for me.. I had to be root via sudo su)
11a - run the script by calling the file name (Rsync_Fatclients or whatever you saved the script in /usr/bin as)
11b - use more terminals to clone multiple PC's at once


All you have to do is type a PC name and enter a password when prompted!

This works wonders for me.. and saves me a lot of time.
Took me hours and hours to figure out..and I learned A LOT.
Hopefully helps save others a lot of time in the future.
I make no guarantees that it will work for you.. small coding problems might mean it works differently on your networks.. so please give me feedback and help improve these scripts.
If you see any security flaws, or more efficient ways to do things, please help out.

The Freeze script I am especially proud of and it makes introducing Linux much more enjoyable for new users.
I create their main account, and always include a guest account which I freeze. 
Then I tell them to use the Guest account any time they are not sure what they are doing.. so when they accidentally delete the panel or items from the panel, they can restart and they are all back in the same positions just like new. I find this makes users feel much more comfortable and they tend to experiment much more.

You can use variations of this freeze script to Deep Freeze an entire Ubuntu partition, or make safe folders that are not frozen.
just include --exclude="/path/to/safe/folder" in the script for the first sync and in the awk section of the freeze script.

Better yet, unlike the Ubuntu guest account, you dont have to be logged into your account and activate guest for them. They can simply login as guest.

If you ever want to make changes to the protected frozen account simply restart the PC.. login as guest.. make the changes.. logout and login as admin account.. then rerun the script. It will update the freeze.

If you ever want to make changes to your fat clients, simply install new programs or updates to your master PC and then run the cloning script. Be careful of Linux Image updates and Grub menu.lst
Double check to make sure it always boots from partition number not UUID.. guess how I learned that?

Any help or suggestions would be great.. after all I've never had computer classes and learned everything from reading the forums and other helpful people posting knowledge on the net... I'm 

**J**ust
**a**
**H**igh
**S**chool
**T**eacher

that loves the idea of Ubuntu and the helpful community that comes with it. So hopefully this is a little part of giving back.

---

### Post by jakswa on 2010-06-04
Thanks for this!  From reading above, I gather that you're using Rsync to do the magic of the "freeze" (ie none of the users changes are saved on reboot).  Is that correct?  I'd like more information on how exactly this keeps the system from saving changes on shutdown...

I've been researching ways of doing what you've done here, and the one I'm currently pursuing (with some problems) is just having a liveCD image *be* the system (read-only, and no changes are saved on shutdown).  Kind of like this guide does (except only copying the liveCD over, without installing from the partition):  [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

Currently I've been figuring out how to edit the liveCD (with some success), and am stuck on how to restrict the default ubuntu user from messing with the windows partition the machines will have as well (but still letting the users use sudo to install programs and edit files)...

Any info you can give is greatly appreciated!

---

### Post by jahst on 2010-06-12
Hello

I posted this a long time back.. and was always wondering if it would be useful to anyone... so thanks.

Yes, rsync is doing the magic... it's proving to be a very powerful tool the more I use it.


[COLOR="Red"]"I'd like more information on how exactly this keeps the system from saving changes on shutdown..."[/COLOR]


2 things:

1 - because the "guest" user I create is not an administrator... they can only make changes to their account.. not the system.

2 - the guest account is not changed on shutdown.. it's restored on startup.... which yes.. means their history, etc it still on the machine until startup... which isnt a problem for me.

I used to know where to put the files to run it on shutdown instead.. but don't remember. I'll look into it and get back to you.

You could also try a google search.. "run script on shutdown" which is what I will be doing anyway.. and how I figured it out the first time.



I would NOT recommend you use a Live CD as the main OS. 
They usually run with root powers. If by some chance you find a way to fix most of your problems.. and make a live CD with all the programs and configurations you need, you would have to redo each image every time there was an update or you needed to change something... too much work.


I know this because I originally tried this route as well.. until I started practicing what I preach... "let the computer do the work for you.. that's it's job". I just had to figure out how to get the computer to do the work first.


My way.. I test everything on a clone machine. If it works and I like the changes.. I make them on the master machine.. and then run the updates to all clones in the lab.

If I don't like the changes on the clone.. then I just re-clone the single machine from the master... which of course, undoes all my test changes on the clone.

I can assure you.. this method is very very time saving and effective.


[COLOR="Blue"]Why do you need / want the users to be able to install programs and edit files?[/COLOR]

This would be a huge security risk for the PC and network. 

A normal user will be able to edit any file in their home directory.. which is a lot. They shouldnt have a need to edit any system files, as doing so would allow them to break anything that you setup and possibly more.

If you haven't already, I'd recommend you setup a test machine, create a guest account, "sudo adduser guest" or whatever you want it to be called.. and then run the "freeze" script on it.

Login as the guest and test it out.



Good luck, and please feel free to ask if you have any more questions.

Jahst

---

### Post by jakswa on 2010-06-12
Thanks for the reply!  Unfortunately, the reason we want students to have root (or at least mostly root), is because they will be configuring the systems themselves (this will be a college lab, and the students will be CS and IT students learning linux administration).

I've made it a long way since posting in this thread.  A nice gentleman in another thread described using AppArmor to limit only the things I needed to keep safe (the XP partition, and the liveCD *image*), and that's the route I'm taking at the moment.

Otherwise, we want the students to have free reign over the liveCD image as it runs (but still have it boot fresh everytime).

I'll see how that goes.  If not, we'll probably be settling for a crippled install with no root access.

---

### Post by jahst on 2010-06-17
[COLOR="Red"]"A nice gentleman in another thread described using AppArmor to limit only the things I needed to keep safe"[/COLOR]

Any chance you could post the link to that thread... I'd like to learn more too. Never tried AppArmor before.. but will be investigating. 


... I'm still not sure how well the liveCD approach will work ... seems like anyone with root access will always be able to undo what you did.. or in the case of a LiveCD... at least access the windows partitions (very bad).
Also LiveCD's tend to be slow and you'll have a hard time "installing" large amounts of software... because nothing is ever really installed.
 

Please keep me posted on your LiveCD and AppArmor progress... you can send private message, or start a new thread about your LiveCD attempts.


My method will still work if you give students root access...but you might have to do a little extra work.... I have not tried this... but in theory.. it'll work. Also no guarantee on the security aspect.

------------------------------------------

First - setup fstab to mount Windows partition read-only(so they cannot change it without reboot). or better yet, prevent mounting of Windows partition at all .. which Im not sure is possible since your users will have root powers.


2 - setup a dedicated machine for the master image that student do not have access to.. or simply clone the files to an external drive / DVD image, whatever.


3 - reverse my scripts so on bootup each clone pulls the data from the master image rather than pushing it from the source. ( I have tested it this way and it works )


This way, even if they change the fstab.. it'll be reset on reboot.. I think.


Again, because you are giving students full access as root.. they will be able to break things if they are malicious.


If you are set on using LiveCd you might want to look into creating Thin Clients.. rather than fat clients.

It's possible you could pull the plug on the PC hard drive and boot the entire OS into RAM from an image someplace on the network.

Good luck, and again please keep me posted on your progress.


Jahst

---

### Post by jakswa on 2010-06-17
[http://ubuntuforums.org/showthread.php?p=9415034](http://ubuntuforums.org/showthread.php?p=9415034)

---

