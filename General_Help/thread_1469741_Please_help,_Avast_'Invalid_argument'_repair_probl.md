---
title: "Please help, Avast 'Invalid argument' repair problem...?"
date: 2010-05-02
forum: General Help
---

### Post by liviococcia on 2010-05-02
Hello Members, i'm a total novice on Ubuntu so can anyone help at all...

I've installed Avast Home Edition, and after updating the software i got the error below:

' An error occurred in avast! engine: Invalid argument '

I found the answer to the problem, but it won't retain the change when i next startup the computer, this is what i did when following the instructions

1: Opened a Terminal Window
2: from the flashing cursor i typed..    sudo sysctl -w kernel.shmmax=128000000   ..then pressed enter on the keyboard.
3: It asked for my password, this did not appear as i typed it and then press enter again.
4: what then appeared was...  kernel.shmmax=128000000  i presumed this was confirmation that it had been accepted and changed.

This does correct the problem, but What have i missed for it to not retain itself when i next boot up.

Help would really be appreciated.

Kind regards
Livio

---

### Post by liviococcia on 2010-05-03
Just to update....

I first checked for any Ubuntu 9.10 updates, and accepted any that were outstanding, after restarting the computer Avast Home Ed still showed the error box 'Invalid argument' when the application tried to open

After doing more searching on the web, i found some more info regarding the 'sysctl.conf' file, and altering the 'shmmax' page file type memory. 

I found out that if i added the line...

   kernel.shmmax = 128000000    

..to the bottom of the sysctl.conf text file this seemed to do the trick, as far as i can tell anyway so far.

Using the 'File browser' i found out that the sysctl.conf is in the 'etc' folder, i found the file was a 'read only' text file, so i used Alt +F2 to open the 'Run application'  box and typed...   gksu gedit   ... this opened the text editor application Gedit as an administrator user , and opened the sysctl.conf text file by going through the application itself, now it was a writeable file so any changes could now be saved.

The reason i'm being as detailed as i can, is that finding out basic newbie user information like accessing, and changing something in Ubuntu as an administrator(root) was not to me widespread information as it could have been, especially when you have to make changes to operating system files. 

Do you think that the addition i've made to the sysctl.conf file above will be ok as it stands? it seems to have worked out so far i guess only time will tell, or comments from other forum members.

Regards

---

### Post by N_L on 2010-05-07
Got same issue with avast and would like to know if it affects anything to fix it like that^.
Bump for you too :)

---

### Post by liviococcia on 2010-05-09
> **N_L said:**
> Got same issue with avast and would like to know if it affects anything to fix it like that^.
Bump for you too :)
Hello N_L, just to add some more info

So far i have not noticed any problems or issues from what i have done when Ubuntu 9.10 is fully installed, and not in a dual boot system, i have had to do this process on two of my laptops, so far.

What i have noticed is, i also have Ubuntu 9.10 running in a Virtual PC enviroment on a Windows Xp computer using 'VMware Player', and adding the text instruction..    kernel.shmmax = 128000000    ....to the 'sysctl.conf' file does not rectify this 'invalid argument' error for me.

I'm guessing that controlling the system pagefile memory must happen right at system bootup, and that VMware player doesn't bother to refer to this sysctl.conf system file at all to run Ubuntu.

Also for info.., i've notice that if you go for the upgrade to Ubuntu 10.04, during the upgrade install process it will ask if you want to keep, or replace these text configuration files so i would suggest making backup copies of any system files that may have been edited.

regards
Livio

---

### Post by dino99 on 2010-05-09
the best choice with ubuntu is "clamav", install the packages ("8") from synaptic (system admin synaptic)

you can add this ppa to synaptic repo tab: [COLOR="Blue"]ppa:ubuntu-clamav/ppa[/COLOR] to have the more recent updates from [https://launchpad.net/~ubuntu-clamav/+archive/ppa](https://launchpad.net/~ubuntu-clamav/+archive/ppa)

see also below "secured ip" link

---

