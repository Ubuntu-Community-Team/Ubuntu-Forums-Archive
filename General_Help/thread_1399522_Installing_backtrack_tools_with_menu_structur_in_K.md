---
title: "Installing backtrack tools with menu structur in Kubuntu 9.10"
date: 2010-02-05
forum: General Help
---

### Post by teage3 on 2010-02-05
Installing backtrack4 tools with menu structure in Kubuntu 9.10

*NOTE* This WILL break your kpackagekit !!! You will need to reinstall kpackagekit after the installation is complete or fix it with synaptic. 
*This may or may not break your system so do at your own risk* 

For this to work you will need to follow these instructions EXACTLY as it is here.

Go to: [http://rapidshare.com/files/347154482/BT4-Kubuntu-essentials.tar.gz](http://rapidshare.com/files/347154482/BT4-Kubuntu-essentials.tar.gz)

Download the tarzip and open it up.
 
INSTALLING THE BACKTRACK SUB MENU STRUCTURE

Place the menu_backup folder in your home directory. <<----YOU WILL NEED THIS FOR THIS TO WORK
Open the BT4-app-list folder and place the backtrack.txt1 file also in your home directory.
Open a shell and type: kdesudo dolphin /etc/xdg/menus
Delete the kd4-applications.menu file. (dont worry, I have provided a backup copy in the download)
Open the BT4-kde4-applicantions.menu folder and place it where you deleted the old menu.
Now you can exit.

Now you have the bt4 sub menu. 

ADDING THE BT4 GPG KEY AND REPO

Open a shell and type: 

wget -q [http://archive.offensive-security.com/backtrack.gpg](http://archive.offensive-security.com/backtrack.gpg) -O- | sudo apt-key add - 

This adds the GPG key.

Then in a shell type:

 sudo echo "deb [http://archive.offensive-security.com](http://archive.offensive-security.com) pwnsauce main microverse macroverse restricted universe multiverse" > /etc/apt/sources.list

This adds the repo.

Then run :  sudo apt-get update

You now have the bt4 pwnsauce repo.

INSTALLING THE BT4 APPLICATIONS

Open a shell and run:

for i in $(cat backtrack.txt1); do sudo aptitude -y install $i; done

This will install all the apps listed in the backtrack.txt1 file.  

This process is a long one so be patient.

When the installation is complete, Run this command:

sudo cp ~/menu_backup/* /usr/local/share/applications/

This points to the menu_backup folder that you copied to your home directory and will place all the newly installed apps in the backtrack sub directory in youre menu.

Enjoy:
           teage

---

### Post by RaveJunkie on 2010-08-13
I have followed many failed ways to do this and first one to work for me.  THANK YOU!!!

this is just what I wanted.    :o

---

### Post by Zerocool Djx on 2010-10-30
does this really work?

what is "kpackagekit"?

---

### Post by cybercode.rs on 2011-04-20
it is kubuntu app menages. NICE TUTORIAL MAN! Keep it up! It is working for me!

---

