---
title: "Nautilus could not create the following required folders"
date: 2010-08-14
forum: General Help
---

### Post by cake nom nom on 2010-08-14
ok so last night i went into system>administration> user & groups i think it was and  i thought by un-checking the option that i made it so i didnt have to enter a password at the login screen that it would boot up automatically you know?

turns out when i boot up the computer it doesnt ask for a password but

nothing comes up. at first..


then i get a message that says:

Could not update ICEauthority file/home/drnomnomcake/.ICEauthority

it gives me the option to click CLOSE.

and when i do

another messege comes up that says:

There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

it gives me the option to click CLOSE

and when i do its just a empty background no pannel nothing just the purple default wallpaper.

 a few moments later then another message


Nautilus could not create the following required folders: /home/drnomnomcake/desktop,
/home/drnomnomcake/.nautilus.

Before running nautilus. please create these folders or set permissions such that Nautilus can create them.

i can then click ok.

---

### Post by marshmallow1304 on 2010-08-14
Can you do anything after that?  If so, open Applications->Accessories->Terminal, and do
```
sudo chown -R drnomnomcake:drnomnomcake /home/drnomnomcake
```

If not, boot into recovery mode (At the GRUB menu, select the recovery mode option.  If the menu does not show up, hold down Shift during boot), select "Drop to root shell" and do
```
chown -R drnomnomcake:drnomnomcake /home/drnomnomcake
reboot
```

---

### Post by cake nom nom on 2010-08-14
this did not do anything i believe

---

### Post by cake nom nom on 2010-08-14
can someone please help i just got back from Costa Rica & Panama where i took thousands of pictures which will all be gone if i cant find a solution to this and have to reformat :(

---

### Post by AlphaLexman on 2010-08-14
I am having trouble understanding if you are having a permissions issue or if your 'default' folders are missing e.g., ~/Pictures

---

### Post by cake nom nom on 2010-08-14
I'm not sure :( i believe its a permissions issue because all i did was switch it from requiring a password when log in to not

---

### Post by AlphaLexman on 2010-08-14
Well let's take a look...
Post the output of:
```
cd ~ ; ls -l
```
and,
```
cd /home/ ; ls -l
```

---

### Post by robsoles on 2010-08-14
Hey Doc, please answer three things to help us help you:

(1) Are you able to get a terminal session on the machine by pressing [Ctrl]+[Alt]+[F1] when you are on the screen with the purple wallpaper and no panels? (Please use that terminal to execute AlphaLexman's suggestions and post back the results as per their request.)

(2) Did you choose "Require password to login and decrypt home folder" type option when you installed Ubuntu on this machine?

(3) Did you click the 'Change' button next to "Password: Asked on Login" in "Users Settings" and then clicked the checkbox for "Don't ask for password on login" and then typed your password and pressed OK or was it something else you did to make your predicament?

---

### Post by cake nom nom on 2010-08-15
1.i **can** access the terminal by hitting ctrl+alt+f1

2. i **did** choose "Require password to login and decrypt home folder"

3. i don't exactly remember how i did it all i remember is that i made it so no password was required 


the out put to 
cd ~ ; ls -lis (i have to type this out on a nother computer) :

total 133296

-rw--------- 1 drnomnomcake drnomnomcake 729154 2010-08
drwx-------
-rwxr-xr-x
-drwx-------
drwxr-xr-x

...
ill just take some pictures & post them

---

### Post by Ginsu543 on 2010-08-15
Well, at least to save your vacation pics, you may want to boot up into a live session using a LiveCD, open Nautilus, open the hard drive your pics are on, and copy them to a safe location and/or backup drive.

---

### Post by cake nom nom on 2010-08-15
cd ~ ; ls -l
[http://i35.tinypic.com/4tollz.jpg](http://i35.tinypic.com/4tollz.jpg)
[http://i37.tinypic.com/2mwxr84.jpg](http://i37.tinypic.com/2mwxr84.jpg)
[http://i35.tinypic.com/14b6tdu.jpg](http://i35.tinypic.com/14b6tdu.jpg)


& 

cd /home/ ; ls -l


is : 

[http://i35.tinypic.com/24pibgo.jpg](http://i35.tinypic.com/24pibgo.jpg)
[http://i36.tinypic.com/vphq88.jpg](http://i36.tinypic.com/vphq88.jpg)

---

### Post by AlphaLexman on 2010-08-15
There are no username(s) in /home/ just 2 pictures. that is not good!

Edit: Do this ->
```
cd ~ ; cd .. ; ls -l
```
I just can't believe your 'home' folder is gone. It must be somewhere!

---

### Post by robsoles on 2010-08-15
> **AlphaLexman said:**
> ...
```
cd ~ ; cd .. ; ls -l
```
I just can't believe your 'home' folder is gone. It must be somewhere!

It is somewhere - hidden. '-l' needs to be '-al' to show up hidden files, please checkout his response to my 2nd question earlier - I quote him below:

> **cake nom nom said:**
> 1.i **can** access the terminal by hitting ctrl+alt+f1

Good but:

> **cake nom nom said:**
> 2. i **did** choose "Require password to login and decrypt home folder"


Makes it all very very bad - The system is going to be tricky to recover, did you notate the encryption hash the first time you logged in after installing? When you take the above option the OS has a message for you to notate it somewhere secure, I hope you did because (to best of my understanding) you have broken the chain that did it automatically for you on login with your password!


When you use the tty terminal (that is what you access by pressing [Ctrl]+[Alt]+[F1]) and it has you login using your regular username and your regular password you should be already in your home directory.

Please just login and type;
```
ls -al
```into the terminal immediately after logging in and post it back here. Then go on to AlphaLexman's last instructions which (except my addition of '**a**' flag) were;
```
cd ~
cd ..
ls -**a**l
```and please show us the output of that as well.

---

### Post by AlphaLexman on 2010-08-15
Thanks robsoles I missed that.

Edit: and doesn't an encrypted folder have a .private (or similar) folder somewhere, where the actual data is stored?

---

### Post by cake nom nom on 2010-08-16
ls -al
[http://i37.tinypic.com/15oysuh.jpg](http://i37.tinypic.com/15oysuh.jpg)
[http://i33.tinypic.com/30decnn.jpg](http://i33.tinypic.com/30decnn.jpg)
[http://i37.tinypic.com/2qnb0r6.jpg](http://i37.tinypic.com/2qnb0r6.jpg)



cd ~
cd ..
ls -**a**l
[http://i37.tinypic.com/f1frfd.jpg](http://i37.tinypic.com/f1frfd.jpg)
[http://i38.tinypic.com/kak5me.jpg](http://i38.tinypic.com/kak5me.jpg)
[http://i37.tinypic.com/296f4vo.jpg](http://i37.tinypic.com/296f4vo.jpg)


and as for my paraphrase i took a screenshot of it, could there be a command i could put in to access it? it showed up on one of the screenshots from above

---

### Post by robsoles on 2010-08-16
Sorry, I was in bed 7 hours ago.

Now that I realise you are taking photos of your display after issuing the commands and uploading them to tinypic I finally go and look at the pictures I see you have lots of relevant files to a user! (Your posts make it look like you have bizarre files on your HDD but they should be something like http\:\/\/i37.tinypic.... etc etc if that the case!)

I don't spot the signs of an encrypted home folder, it looks more like everything is out in the open so it is probable that the act of logging in via tty terminal is decrypting your home folder as it ought. (phew!)

Restoring gnome to ask for your password and get on with the job of decrypting your home folder is probably a very simple command that I don't know immediately and I have some pressing work to do here (I just got into work) but I will check in on this thread later today.

EDIT: I saw the file 'passphrase.png' - I don't mean to be mean but if it's where I think it is then it is useless there due it would be inaccessible if your home folder wasn't being decrypted and mounted when you log in.

EDITED AGAIN: A result from following search should have instructions to follow that will help but you need to try to make sure they are talking about an encrypted home folder and that their post clearly indicates their success - I've seen people post about how they ruined it

[http://www.google.com.au/search?q=restore+gnome+login+screen+in+ubuntu](http://www.google.com.au/search?q=restore+gnome+login+screen+in+ubuntu)
[http://www.google.com.au/search?q=restore+gnome+login+screen+in+ubuntu+encrypted+home+folder](http://www.google.com.au/search?q=restore+gnome+login+screen+in+ubuntu+encrypted+home+folder) (perhaps)

---

### Post by cake nom nom on 2010-08-16
thank you rob, your a hero! i'll keep you posted.

---

### Post by AlphaLexman on 2010-08-16
I have to admit I was [COLOR=Red]misled[/COLOR] also by the tinypic url's in your post. But looking at the 'screenshots' and trying to 'panorama' them together, I can gather this...

f1frfd.jpg -> kak5me -> 296f4vo, are three overlapping images (left to right) of the [/home/] directory (parent of ~/).

It must look something like this:
```
drwxr-xr-x  4 root         root          4096 2010-07-19 00:47 .
drwxr-xr-x 22 root         root          4096 2010-07-30 00:09 ..
drwx------ 54 drnomnomcake drnomnomcake 16384 2010-08-14 04:25 drnomnomcake
drwxr-xr-x  3 root         root          4096 2010-07-19 00:47 .ecryptfs
```**AND** it appears that in your [~/] directory the pics: 15oysuh.jpg -> 30decnn.jpg -> 2qnbor6.jpg, are overlapping images (top/middle to bottom)

It appears [/home/drnomnomcake/.Private] points to [/home/.ecryptfs] (but we can't see past the characters '/home/.e')

I realize you are doing the best you can to give us information, but what I really want to see are the permissions (-rw-r--r--) of the 'ls -al' output, especially the [~/.Private] directory.

The permissions to your 'home' folder look weak however. I may be wrong here, but I would at least give [/home/drnomnomcake/] 755 permissions until you sort this mess out.
```
chmod 755 /home/drnomnomcake/
```
Although your encryption links look OK to me.

---

### Post by robsoles on 2010-08-16
Sorry AlphaLexman but I have to disagree. His home folder's permissions are '700' right now and that is currently believed best for a home folder. 755 gives more permissions away and it really shouldn't be necessary to allow other processes/users to have access to it at all.

The problem is that the GDM process for decrypting and mounting his encrypted home folder has become disconnected, I am sure there is a simple set of commands or instructions to fix it but I am at work and lunch is another hour away - the instructions should be in a result of either or both of the searches I linked in my last post, I can try harder to find them at lunchtime.

When the encrypted home folder is not mounted you usually see two files out in the open (in it), of which at least one refers to mounting the encrypted file-space using the GUI, and a .private hidden folder as you suggested before.

---

### Post by mc4man on 2010-08-16
in a 'normal' install (not encrypted), when you set the option to autologin a 'custom.conf' is created in /etc/gdm. Editing that file or moving to a .bak would restore the login 
Have no experience with encrypted, as in, is anything different there.

---

### Post by robsoles on 2010-08-16
Pretty sure I have found it in this thread [http://ubuntuforums.org/showthread.php?t=1309143](http://ubuntuforums.org/showthread.php?t=1309143)

Using terminal
```
sudo nano /etc/gdm/custom.conf
```
(If that leads to an empty document then I am wrong, rest of instructions are pointless)

Look for > Autologin true or > Autologin=true and change 'true' to 'false'

then press [Ctrl]+[X], [Y] (for save question) and [Enter] (to actually save it!) to write that change to the hard drive

then```
sudo 'shutdown -r now'
``` to restart your machine and (all going to plan) you should have your old login screen back and when you login you should have access to all your stuff!

Please let us know how that goes!

---

### Post by robsoles on 2010-08-16
> **mc4man said:**
> in a 'normal' install (not encrypted), when you set the option to autologin a 'custom.conf' is created in /etc/gdm. Editing that file or moving to a .bak would restore the login 
Have no experience with encrypted, as in, is anything different there.

mc4man is right (AFAIK) and if I'd noticed his post and considered it I would have either withheld my last post or just used it to back them up!

---

### Post by cake nom nom on 2010-08-16
> **robsoles said:**
> Pretty sure I have found it in this thread [http://ubuntuforums.org/showthread.php?t=1309143](http://ubuntuforums.org/showthread.php?t=1309143)

Using terminal
```
sudo nano /etc/gdm/custom.conf
```(If that leads to an empty document then I am wrong, rest of instructions are pointless)

Look for  or  and change 'true' to 'false'

then press [Ctrl]+[X], [Y] (for save question) and [Enter] (to actually save it!) to write that change to the hard drive

then```
sudo 'shutdown -r now'
``` to restart your machine and (all going to plan) you should have your old login screen back and when you login you should have access to all your stuff!

Please let us know how that goes!


empty file/new file i think ill post a screenshot

---

### Post by mc4man on 2010-08-16
I think - if the Op is unfamiliar with nano, would be to try moving to a .bak, could always be moved back. (1st time I used nano I borked a file real good, was lucky I also couldn't save it.) 

(unless there is something in there specific to the encrypted? 

```
sudo mv /etc/gdm/custom.conf /etc/gdm/custom.conf.bak
```

---

### Post by cake nom nom on 2010-08-16
here is the screen shot

[http://i36.tinypic.com/ejfkw6.jpg](http://i36.tinypic.com/ejfkw6.jpg)
[http://i35.tinypic.com/dh9zqd.jpg](http://i35.tinypic.com/dh9zqd.jpg)


the little things at the bottom read


                                                                 [ New File]
^G Get Hel    ^D WriteOut    ^R Read File    ^Y Prev Page    ^K  Cut Text     ^C Cur Pos
^X Exit          ^J  Justify        ^W Where Is     ^V Next Page   ^U UnCut Text  ^To spell

---

### Post by cake nom nom on 2010-08-16
> **mc4man said:**
> I think - if the Op is unfamiliar with nano, would be to try moving to a .bak, could always be moved back. (1st time I used nano I borked a file real good, was lucky I also couldn't save it.) 

(unless there is something in there specific to the encrypted? 

```
sudo mv /etc/gdm/custom.conf /etc/gdm/custom.conf.bak
```


yeah im sorry, im not too sure what nano is

should i do the following code anyway?

---

### Post by robsoles on 2010-08-16
Please Doc, do as mc4man posted to do, I repeat it here for you:

```
sudo mv /etc/gdm/custom.conf /etc/gdm/custom.conf.bak
```

I wish you could copy and paste it from here to your terminal to be sure you don't make a typo or anything but just try carefully and tell us what terminal replies with for that command (if it doesn't look like an error then try restarting!)

---

### Post by cake nom nom on 2010-08-17
i got the following 
mv: cannot start ' /etc/gdm/custom.conf ' : No such file or directory

---

### Post by robsoles on 2010-08-17
Please show us the picture you can take of the screen after typing in
```
ls /etc/gdm
```

(Try to get the relevant part of the screen in one pic please Doc ;))

---

### Post by cake nom nom on 2010-08-17
i got the following all in a straight row:

custom.conf.save  custom.conf.save1 failsafeBlacklist failsafeXinit failsafeXServer gdm.schemas  Init PostLogin  PostSession  PreSession Xsession

---

### Post by robsoles on 2010-08-17
please try
```
sudo mkdir /root/gdm-bak/
sudo 'mv /etc/gdm/custom.* /root/gdm-bak'
```
and then please show me the output from
```
ls /etc/gdm -al
```
(sorry, I forgot the 'show everything' switch earlier!)

---

### Post by cake nom nom on 2010-08-17
[http://i35.tinypic.com/2edwbqe.jpg](http://i35.tinypic.com/2edwbqe.jpg)
[http://i37.tinypic.com/lgvfa.jpg](http://i37.tinypic.com/lgvfa.jpg)

---

### Post by cake nom nom on 2010-08-17
still no solution :(

---

### Post by robsoles on 2010-08-17
so, let's try something that mc4man suggested to me in a single PM yesterday :)

```
sudo 'echo AutomaticLoginEnable=false >> /etc/gdm/custom.conf'
```
(Please make sure you use the ' apostrophe marks I have put here)

The suggestion is that perhaps by making a 'custom.conf' file under /etc/gdm it will override whatever is going on and give you back a 'connected' login sequence to have your desktop decrypted and thereby a usable GUI/Desktop session again.

I am taking it a step further to specify in the custom.conf file that AutomaticLoginEnable will equal false - it's a longshot but at least it's trying.

If that fails I will be pressing into changes from 9.10 to 10.04 because in 9.10 it was in /etc/gdm/custom.conf !!

---

### Post by robsoles on 2010-08-17
Sorry, just experimented with above code and it will not work in terminal as I posed it!

```
sudo -i
echo AutomaticLoginEnable=false >> /etc/gdm/custom.conf
exit
```

should work and do as I want it to! Whether or not that fixes the problem is another story which needs a restart of the system to confirm or deny:
```
sudo 'shutdown -r now'
```(That line should work fine whereas 'echo' was apparently not recognised by sudo command before!)

---

### Post by cake nom nom on 2010-08-17
> **Ginsu543 said:**
> Well, at least to save your vacation pics, you may want to boot up into a live session using a LiveCD, open Nautilus, open the hard drive your pics are on, and copy them to a safe location and/or backup drive.


this is possible?? its all i care about.

---

### Post by cake nom nom on 2010-08-17
> **robsoles said:**
> Sorry, just experimented with above code and it will not work in terminal as I posed it!

```
sudo -i
echo AutomaticLoginEnable=false >> /etc/gdm/custom.conf
exit
```should work and do as I want it to! Whether or not that fixes the problem is another story which needs a restart of the system to confirm or deny:
```
sudo 'shutdown -r now'
```(That line should work fine whereas 'echo' was apparently not recognised by sudo command before!)


ok i just saw this i will try it now

---

### Post by robsoles on 2010-08-17
> **cake nom nom said:**
> this is possible?? its all i care about.

Due to your home folder being encrypted booting from a livecd and getting the pics won't be easy at all.

I can step by step you through getting your stuff onto a USB stick if that is what it comes to, but I am expecting we will crack this problem before much longer!

---

### Post by cake nom nom on 2010-08-17
dang it still did auto login did i do somthing wrong?

[http://i34.tinypic.com/14btfth.jpg](http://i34.tinypic.com/14btfth.jpg)

---

### Post by cake nom nom on 2010-08-17
> **robsoles said:**
> Due to your home folder being encrypted booting from a livecd and getting the pics won't be easy at all.

I can step by step you through getting your stuff onto a USB stick if that is what it comes to, but I am expecting we will crack this problem before much longer!


kudos!!!!!

---

### Post by robsoles on 2010-08-17
> **cake nom nom said:**
> dang it still did auto login did i do somthing wrong?

[http://i34.tinypic.com/14btfth.jpg](http://i34.tinypic.com/14btfth.jpg)

I cannot see for sure - would need to see right hand part of screen to be sure you typed >> /etc/gdm/custom.conf as file to send the line being echo'd to.

I will post again later from home (after making sure I am not going to steer you wrong) about copying your pics onto a USB stick and also (hopefully) at least one more try for disabling autologin on your laptop there to fix the problem.

Sorry to make you wait pal.

---

### Post by robsoles on 2010-08-18
Left it a bit late and didn't do the tests I intended but the following should fail harmlessly rather than destroying your pictures Doctor Cake Nom Nom so please forgive me.

After logging into terminal available by pressing '[Ctrl]-[Alt]-[F1]' type in
```
ls /dev/sd*
```
take note of what is there and then plug in your USB flash drive that has enough space for your pictures(!)
```
ls /dev/sd*
```
again after a few seconds should show you what the USB drive is called in your system. Probably /dev/sdb1 (*NOTE: You must use a drive reference that ends in a numeral for our purpose and I won't explain further here!)

Taking /dev/sdb1 (**make sure you pick the *right* one!) as the USB's correct ID in the system use terminal:
```
mkdir ~/temp-usb
cd ~/
sudo mount /dev/sdb1 ~/temp-usb
mkdir ~/temp-usb/recover-pics
cp -R ~/Pictures/* ~/temp-usb/recover-pics/
sudo umount /dev/sdb1
rm ~/temp-usb
```
(The last line in that sequence is just for housekeeping, all other lines are vital to operation!)
Before doing anything even slightly permanent (like formatting your HDD and reinstalling Ubuntu for instance) please please verify that you have all the Picture files that you want!

This can be done for your entire profile or home folder -please ask for more instructions before deleting anything you may want to keep pal!


*If anything I have suggested in this post gives you an error please stop following instructions and report back the action and error!

---

### Post by cake nom nom on 2010-08-18
> **robsoles said:**
> Left it a bit late and didn't do the tests I intended but the following should fail harmlessly rather than destroying your pictures Doctor Cake Nom Nom so please forgive me.

After logging into terminal available by pressing '[Ctrl]-[Alt]-[F1]' type in
```
ls /dev/sd*
```take note of what is there and then plug in your USB flash drive that has enough space for your pictures(!)
```
ls /dev/sd*
```again after a few seconds should show you what the USB drive is called in your system. Probably /dev/sdb1 (*NOTE: You must use a drive reference that ends in a numeral for our purpose and I won't explain further here!)

Taking /dev/sdb1 (**make sure you pick the *right* one!) as the USB's correct ID in the system use terminal:
```
mkdir ~/temp-usb
cd ~/
sudo mount /dev/sdb1 ~/temp-usb
mkdir ~/temp-usb/recover-pics
cp -R ~/Pictures/* ~/temp-usb/recover-pics/
sudo umount /dev/sdb1
rm ~/temp-usb
```(The last line in that sequence is just for housekeeping, all other lines are vital to operation!)
Before doing anything even slightly permanent (like formatting your HDD and reinstalling Ubuntu for instance) please please verify that you have all the Picture files that you want!

This can be done for your entire profile or home folder -please ask for more instructions before deleting anything you may want to keep pal!


*If anything I have suggested in this post gives you an error please stop following instructions and report back the action and error!

do i do this under the live cd?

---

### Post by robsoles on 2010-08-18
> **cake nom nom said:**
> do i do this under the live cd?

Not if you want ""easier"" access to the pictures you are copying!


It is possible to 'mount' your home directory from the LiveCD if you have the **long** string of characters your desktop RECOMMENDED you to record some where - if you do it like that you don't need to execute my commands for terminal at all: You just use the graphically driven stuff in Nautilus to get it done...


Otherwise if you just boot the machine off it's own hard disk and then you follow my instructions in my previous post!

---

### Post by cake nom nom on 2010-08-19
darn.. ok i will do this now ill keep you posted

---

### Post by cake nom nom on 2010-08-19
**this is what i got**  After logging into terminal  '[Ctrl]-[Alt]-[F1]' & typing in:
 	Code:
 	ls /dev/sd* 
  	& then i plugged in the usb & typed in

Code:
 	ls /dev/sd* 
**this is what i got**
[http://i34.tinypic.com/xt3s7.jpg](http://i34.tinypic.com/xt3s7.jpg)
 [http://i33.tinypic.com/2h2pix0.jpg](http://i33.tinypic.com/2h2pix0.jpg)
 [http://i37.tinypic.com/20s6iyd.jpg](http://i37.tinypic.com/20s6iyd.jpg)

i was a bit confused on what to do & hesitated to do anything else because i dont want to mess anything up what should i do now?

---

### Post by robsoles on 2010-08-19
The USB drive turned up as **/dev/sdc1**

> **robsoles said:**
> ...

Taking **/dev/sdc1** as the USB's correct ID in the system use terminal:
```
mkdir ~/temp-usb
cd ~/
sudo mount **/dev/sdc1** ~/temp-usb
mkdir ~/temp-usb/recover-pics
cp -R ~/Pictures/* ~/temp-usb/recover-pics/
sudo umount **/dev/sdc1**
rm ~/temp-usb
```
(The last line in that sequence is just for housekeeping, all other lines are vital to operation!)
Before doing anything even slightly permanent (like formatting your HDD and reinstalling Ubuntu for instance) please please verify that you have all the Picture files that you want!

...

---

### Post by cake nom nom on 2010-08-20
after following the instructions & putting in mkdir ~/temp-usb/recover-pics

this is what i got

[http://i38.tinypic.com/t0lrhd.jpg](http://i38.tinypic.com/t0lrhd.jpg)
[http://i35.tinypic.com/2n7fcqp.jpg](http://i35.tinypic.com/2n7fcqp.jpg)

---

### Post by cake nom nom on 2010-08-22
> **robsoles said:**
> The USB drive turned up as **/dev/sdc1**

ok problem solved, had to add sudo to some comands i belive im backing up all of my music & my pictures as im typing this, ill post back in the morning

---

### Post by robsoles on 2010-08-22
Looks, simply enough, as if your USB stick's file-system has owners and permissions as opposed to being something like fat32.

---

### Post by cake nom nom on 2010-08-22
OK yeah so its confirmed i have all of my pictures! i wil just back up all of the folders onto my external now, thank you everyone for helping kudoss !!

---

### Post by ecern on 2011-04-06
There is a simple fix to all of this.

Boot into the recovery shell from the GRUB login screen

Drop to a root prompt

Create a new user with adduser

Enter the reboot command

Boot Ubuntu normally and login as the new user

Use the mouse to select System->Administration->Users and Groups

Select your previous user name that is currently unable to login and click on change.  You will be asked for a PW.  Provide the password of the locked out user, presuming that user has sudo permissions.  Go through the dialogs and change options for your previous user so that a password IS required at login.  You will then be presented with a new password screen.  Enter your original password for that user.

Then reboot normally.  When Ubuntu comes up, select the user that was previously unable to login properly, give the PW, and login.

You should now have your system back the way it was before you changed the option into "Login without a Password."

---

