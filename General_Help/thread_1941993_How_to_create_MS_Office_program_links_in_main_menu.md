---
title: "How to create MS Office program links in main menu?"
date: 2012-03-16
forum: General Help
---

### Post by A Traveller on 2012-03-16
Hi all.

I have followed the steps shown at the following page to install MS Office 97 on an Ubuntu 10.04 pc.

[http://www.wine-reviews.net/microsoft/running-ms-office-97-under-linux-with-wine.html](http://www.wine-reviews.net/microsoft/running-ms-office-97-under-linux-with-wine.html)

For some reason, when I go to Applications - Wine - Programs, only Microsoft Access appears in the menu (apart from Accessories with Notepad). How do I add links for Excel, Word and PowerPoint? I have tried copying the 'Command' for Access from the Launcher Properties, adding a new item and replacing the word 'Access' by 'Excel' but that hasn't worked.

So, for Access, it was:-

env WINEPREFIX="/home/username/.wine" wine C:\\windows\\command\\start.exe /Unix /home/username/.wine/dosdevices/c:/users/username/Start\ Menu/Programs/Microsoft\ Access.lnk

and I tried:-

env WINEPREFIX="/home/username/.wine" wine C:\\windows\\command\\start.exe /Unix /home/username/.wine/dosdevices/c:/users/username/Start\ Menu/Programs/Microsoft\ Excel.lnk

At present, in order to open Excel, PowerPoint or Word, I am having to go to Applications - Wine - Browse C Drive - Program Files - Microsoft Office - Office - right-click on the icon for the application - click Open with Wine Windows Program Loader. If I place a copy of these icons on the desktop and then right-click on them to open them with Wine Windows Program Loader, nothing happens! I can only open them if I travel the lengthy route above! Why can't I create desktop shortcuts that work?

Also, if I click on Browse to browse for files on the pc, the Home Folder only shows a few folders such as Documents, Music, Pictures, Videos and a few others. How do I browse to the .wine folder, for example?

Any help would be appreciated.

Thanks.

---

### Post by davidvandoren on 2012-03-16
Go to system preferences Main Menue.
On the left click on wine and then where you want the shortcut to appear.
Click on the right **new item**.
On the pop-up click next to command **browse**. 
Right click and choose show hidden files and folders. 
Find your way to c program files and select you ms word exe.
Name it what ever you like and write what ever comment. 
On the left you'll see the icon button click on it and choose an icon for word.
If you cant find an Icon download one from google pictures just type word icon and choose one you like.

---

### Post by A Traveller on 2012-03-16
Thanks for your very detailed and helpful instructions, davidvandoren. It did as you said. Now is there any way of making it so that the program opens when the link is clicked? If the link is clicked, nothing happens because it needs to be told to open with Wine, however, this option doesn't appear when right clicking on a menu item. Am I correct that I have to right click on the original program executable file, e.g. excel.exe and then choose Wine as the Open With option and leave the check mark next to the option for remembering this setting?

Also, I won't be able to test anything out at the moment as it seems installing Wine or MS Office on the hard drive has ruined it. My computer started to give off beeping noises throughout the installation process and started to freeze and now the hard disk would not boot up at all. I had to disconnect the drive in order to for my pc to start up. It's a good thing I only installed it on a test drive and not my main drive! Has anyone else ever experienced their system being messed up from installing Wine/MS Office?

Thanks.

---

### Post by A Traveller on 2012-04-25
Hi davidvandoren. My hard drive has let me in, but it is freezing very frequently now. I just wanted to let you know that the links in the main menu are working fine. Thanks for your instructions. I am assuming that it is normal that Access and Outlook don't work and give the following errors.

'Microsoft Access can't start because there is no license for it on this machine'

and

'Cannot start Microsoft Outlook'

---

### Post by Mark Phelps on 2012-04-25
> **A Traveller said:**
> ... 
'Microsoft Access can't start because there is no license for it on this machine'  and 'Cannot start Microsoft Outlook'

Had you checked the WineHQ website before doing this work, you would have discovered that, unfortunately, MS Access and MS Outlook do not work in Wine.  

Which is most probably, why you're getting the messages.

---

### Post by techsupport on 2012-04-25
The easiest way to achieve what the OP is requesting to have done on their desktop would be to install PlayOnLinux, it is down this list:

[http://debianhelp.wordpress.com/2011/12/31/to-do-list-after-installing-ubuntu-10-04-3-lucid-lts/](http://debianhelp.wordpress.com/2011/12/31/to-do-list-after-installing-ubuntu-10-04-3-lucid-lts/)

PlayOnLinux will help you install MS Office and gives the user the option to have icons placed directly on the desktop. PlayOnLinux has the automatic configuration for icons, and other settings too. 

:guitar:

---

### Post by Mark Phelps on 2012-04-25
PlayOnLinux is a front-end to Wine.  If the apps don't work in Wine, they won't work with PlayOnLinux.  Like Wine, it's not a miracle cure.

---

### Post by A Traveller on 2012-07-27
Thanks for the replies Mark Phelps/techsupport.

I had read that Access and Outlook don't work, however, included the errors I got anyway.

As mentioned in my third post, the links worked fine afterwards.

Thanks.

---

